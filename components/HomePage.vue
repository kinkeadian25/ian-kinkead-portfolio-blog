<template class="position-relative">
  <div class="text-white pt-12 flex flex-col items-center justify-center">
    <div class="container mx-auto text-center px-4">
      <h1 class="text-4xl font-bold mb-4">
        Hi, I'm<span class="ml-2 text-4xl animate-typing text-emerald-400">{{
          typedText
        }}</span>
      </h1>
      <div class="flex flex-col items-center justify-center">
        <img
          src="/me.jpeg.JPG"
          alt="Photo of Ian Kinkead with his dog, a catahoula named Russ."
          class="rounded-full w-64 h-64 mx-4 my-6 shadow-xl border-4 border-emerald-400"
        />
        <div class="flex flex-row items-center justify-center">
          <a
            href="https://www.linkedin.com/in/ian-kinkead/"
            target="_blank"
            rel="noopener noreferrer"
          >
            <img
              src="/LI-In-Bug.png"
              alt="LinkedIn Logo"
              class="w-16 h-14 mr-4 mb-6"
            />
          </a>
          <a
            href="https://github.com/kinkeadian25"
            target="_blank"
            rel="noopener noreferrer"
          >
            <img
              src="/github-mark.png"
              alt="GitHub Logo"
              class="w-16 h-16 ml-4 mb-6 bg-white rounded-full p-3"
            />
          </a>
        </div>
      </div>
      <div class="text-white mx-auto px-4 sm:px-0">
        <nuxt-link to="/blog" class="text-emerald-400 underline">
          Checkout my blog
        </nuxt-link>
        to see some projects, open source work, and other things I am learning
        about!
      </div>
      <div
        class="border-dotted border-b-2 border-slate-600 my-16 mx-4 sm:mx-60"
      ></div>
      <h2 class="text-lg font-semibold text-white mx-auto">
        <span class="text-white"></span>
        Console.WriteLine(<span class="text-emerald-400">aboutMe</span>);
      </h2>
      <div
        class="bg-black border-2 px-3 border-emerald-600 my-6 mx-4 sm:mx-20 lg:mx-40 shadow-xl"
      >
        <p class="my-3 text-slate-200">
          The magic of taking an idea and making it happen through code is what
          keeps me ticking. All complex problems have an elegant solution. I may
          not be the one to figure them all out, but I strive to participate as
          much as I can through open source, my professional work, continuous
          learning, and formal education. I am fully committed to learning how I
          can make technology more inclusive, high-performing and maintainable
          everyday.
        </p>
        <p class="my-3 text-slate-200">
          Whether you're looking for a skilled developer or simply want to chat
          about the latest tech trends, I'd love to hear from you! I am
          primarily a web developer focused on backend performance and simple
          but fault-tolerant microservice architectures, but I also catch the
          frontend bug whenever I get the opportunity at work or in my personal
          projects due to my graphic design and animation background.
        </p>
        <p class="my-3 text-slate-200">
          In the Navy, I was a Mass Communication Specialist. I mostly released
          photos, videos, and graphics for internal and external audiences. I
          was on an aircraft carrier and rode in lots of helicopters!
        </p>
      </div>
      <div
        class="border-dotted border-b-2 border-slate-600 my-16 mx-4 sm:mx-60"
      ></div>
      <h2 class="text-lg font-semibold text-white mx-auto">
        <span class="text-white"></span>
        Console.WriteLine(<span class="text-emerald-400">workExperience</span>);
      </h2>
      <div
        class="bg-black border-2 px-3 border-emerald-600 my-6 mx-4 sm:mx-20 lg:mx-40 shadow-xl text-left"
      >
        <div class="my-4">
          <h3 class="font-semibold text-slate-200">
            PACCAR, Renton, WA – Software Engineer/Technical Lead, Apr 2023 –
            Present
          </h3>
          <br />
          <p class="text-slate-200">
            As a full stack developer at PACCAR, I have been getting the chance
            to work with and lead cross-functional teams in developing
            customer-facing web applications. I have also served as a technical
            lead for a high visibility and cost project, contributing to the
            development of user stories and integration plans across multiple
            teams, which has been super exciting!
          </p>
          <br />
          <p>
            I also have gotten to do a ton of work automating incident
            resolution and report generation, which is extremely rewarding. My
            work also includes enhancing various systems for a large
            architecture's efficiency, fault tolerance, and scalability.
            Throughout my time at PACCAR, I have been able to deliver a lot of
            full-stack features to production while maintaining zero
            vulnerabilities and supporting production due to great mentorship
            and a lot of permission to innovate.
          </p>
        </div>
        <div class="my-4">
          <h3 class="font-semibold text-slate-200">
            Microsoft, Bremerton, WA (Remote) – Student, Oct 2022 – Feb 2023
          </h3>
          <br />
          <p class="text-slate-200">
            During my time as a student at Microsoft, I graduated from the
            Microsoft Software and Systems Academy Cloud App Dev program. This
            program provided me with valuable experience in building cloud-based
            web and desktop apps and working with key Azure services. I also had
            the opportunity to contribute to the Microsoft-owned GitHub
            repository dotnet/Roslyn, collaborating on code and tests for the C#
            and VB compiler.
          </p>
        </div>
        <div class="my-4">
          <h3 class="font-semibold text-slate-200">
            US Navy, USS Nimitz – Content Development & Creative Director, Jan
            2016 – Mar 2023
          </h3>
          <br />
          <p class="text-slate-200">
            As a Content Development & Creative Director on the USS Nimitz, I
            led a team in creating media campaigns that reached a wide audience
            and collaborated with international partners. Additionally, I
            developed and delivered training programs to promote open-mindedness
            and efficiency among the crew.
          </p>
        </div>
        <div class="my-4">
          <h3 class="font-semibold text-slate-200">Technical Skills:</h3>
          <ul class="list-disc ml-6">
            <li class="text-slate-200">
              Fluent: C#, SQL, HTML, CSS, JavaScript, TypeScript, Python, Git,
              GithHub, Kafka, WCF, REST, Tailwind, Angular
            </li>
            <li class="text-slate-200">
              Proficient: Java, Powershell, Azure, AWS, Docker, Vue, React,
              jQuery
            </li>
            <li class="text-slate-200">Can Spell: C++, Go, Kotlin</li>
            <li class="text-slate-200">
              Tools: Postman, Sumo Logic, Visual Studio, VSCode, Android Studio,
              IntelliJ, Swagger, ADO
            </li>
          </ul>
        </div>
      </div>
      <div
        class="border-dotted border-b-2 border-slate-600 my-16 mx-4 sm:mx-60"
      ></div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  setup() {
    const strings = ['Ian Kinkead.', 'a Builder.', 'a Software Engineer.']
    const typedText = ref('')
    let stringIndex = 0
    let characterIndex = 0
    let isDeleting = false

    const typeNextCharacter = () => {
      const currentString = strings[stringIndex]

      if (isDeleting) {
        typedText.value = currentString.substring(0, characterIndex) + '|'
        characterIndex--
      } else {
        typedText.value = currentString.substring(0, characterIndex + 1) + '|'
        characterIndex++
      }

      if (characterIndex === currentString.length) {
        isDeleting = true
      } else if (characterIndex === -1) {
        isDeleting = false
        stringIndex = (stringIndex + 1) % strings.length
      }
    }

    onMounted(() => {
      setInterval(typeNextCharacter, 150)
    })

    return { typedText }
  },
}
</script>
