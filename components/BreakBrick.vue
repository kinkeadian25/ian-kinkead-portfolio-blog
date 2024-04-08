<template class="position-relative">
  <div class="justify-center items-center flex flex-col pb-12">
    <h1
      class="text-3xl font-bold text-white border rounded-md border-emerald-400 p-2"
    >
      Brick Break
    </h1>
    <p class="text-white pt-2">
      Use the left and right arrow keys to move the paddle.
    </p>
    <p class="text-white pb-4">
      I am not sure how you ended up on my site, but odds are you could use a
      mental break!
    </p>
    <div class="break-brick bg-slate-900 border-2 border-emerald-400 shadow-xl">
      <div
        class="paddle bg-emerald-500"
        :style="{ left: paddlePosition + 'px' }"
      ></div>
      <div
        class="ball bg-emerald-500"
        :style="{ left: ballPosition.x + 'px', top: ballPosition.y + 'px' }"
      ></div>
      <div
        v-for="(brick, index) in bricks"
        :key="index"
        class="brick"
        :style="{
          left: brick.x + 'px',
          top: brick.y + 'px',
          backgroundColor: brick.color,
        }"
      ></div>
      <button v-if="!playing" class="play-button" @click="startGame">
        Play
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bricks: [],
      playing: false,
      paddlePosition: 350,
      ballPosition: { x: 400, y: 300 },
      ballDirection: { x: 4, y: 4 },
      intervalId: null,
    }
  },
  mounted() {
    this.initBricks()
    window.addEventListener('keydown', this.movePaddle)
  },
  beforeDestroy() {
    window.removeEventListener('keydown', this.movePaddle)
  },
  methods: {
    initBricks() {
      const colors = ['#A9A9A9', '#008B8B']
      const brickWidth = 70
      const brickHeight = 20
      const brickMargin = 10
      const bricksPerRow = Math.floor(800 / (brickWidth + brickMargin))
      const rows = 2

      for (let i = 0; i < bricksPerRow; i++) {
        for (let j = 0; j < rows; j++) {
          this.bricks.push({
            x: i * (brickWidth + brickMargin),
            y: j * (brickHeight + brickMargin),
            color: colors[(i + j) % colors.length],
          })
        }
      }
    },
    startGame() {
      this.playing = true
      this.intervalId = setInterval(this.updateGame, 16)
    },
    movePaddle(event) {
      const step = 15
      if (event.key === 'ArrowRight') {
        this.paddlePosition = Math.min(this.paddlePosition + step, 700)
      } else if (event.key === 'ArrowLeft') {
        this.paddlePosition = Math.max(this.paddlePosition - step, 0)
      }
    },
    updateGame() {
      this.ballPosition.x += this.ballDirection.x
      this.ballPosition.y += this.ballDirection.y

      if (this.ballPosition.x <= 0 || this.ballPosition.x >= 780) {
        this.ballDirection.x = -this.ballDirection.x
      }

      if (this.ballPosition.y <= 0) {
        this.ballDirection.y = -this.ballDirection.y
      }

      if (
        this.ballPosition.y <= 580 &&
        this.ballPosition.y >= 560 &&
        this.ballPosition.x + 10 >= this.paddlePosition &&
        this.ballPosition.x <= this.paddlePosition + 100
      ) {
        this.ballDirection.y = -this.ballDirection.y
      }

      for (let i = 0; i < this.bricks.length; i++) {
        const brick = this.bricks[i]
        if (
          this.ballPosition.y <= brick.y + 20 &&
          this.ballPosition.x >= brick.x &&
          this.ballPosition.x <= brick.x + 70
        ) {
          this.bricks.splice(i, 1)
          this.ballDirection.y = -this.ballDirection.y
          break
        }
      }

      if (this.bricks.length === 0) {
        clearInterval(this.intervalId)
        this.playing = false
        alert('You Win!')
        this.resetGame()
      } else if (this.ballPosition.y >= 600) {
        clearInterval(this.intervalId)
        this.playing = false
        alert('Game Over!')
        this.resetGame()
      }
    },
    resetGame() {
      this.bricks = []
      this.paddlePosition = 350
      this.ballPosition = { x: 400, y: 300 }
      this.ballDirection = { x: 4, y: 4 }
      this.initBricks()
    },
  },
}
</script>

<style scoped>
.break-brick {
  width: 800px;
  height: 600px;
  position: relative;
  border: 1px solid #000;
}

.paddle {
  width: 100px;
  height: 20px;
  position: absolute;
  bottom: 0;
  background-color: #008080;
}

.ball {
  width: 20px;
  height: 20px;
  position: absolute;
  background-color: #008080;
  border-radius: 50%;
}

.brick {
  width: 70px;
  height: 20px;
  position: absolute;
  margin: 5px;
}

.play-button {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
