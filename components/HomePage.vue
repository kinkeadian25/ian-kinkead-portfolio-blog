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
          keeps me ticking. All complex problems have an elegant solution, and I
          may not be the one to figure them all out, but I strive to participate
          as much as I can through open source, my professional work, continuous
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
          <ul class="list-disc ml-6">
            <li class="text-slate-200">
              Collaborated closely with cross-functional teams to lead, and
              implement most of, the development of a key customer-facing
              aftermarket web application, supporting millions of customers,
              achieving a 3x increase in feature delivery per quarter through
              effective teamwork and agile methodologies.
            </li>
            <li class="text-slate-300">
              Designated as technical lead for a key over-the-air vehicle
              programming project, demonstrating expertise in developing domain
              knowledge. Participated in developing over 40 user stories and
              integration plans into a robust existing architecture spanning 3
              separate teams.
            </li>
            <li class="text-slate-200">
              Implemented a Jupyter notebook utilizing pandas, SQLAlchemy, and
              more, for unified querying across four databases, that compares
              data and suggests fixes for incident reports, drastically reducing
              issue resolution time by about 2 hours daily.
            </li>
            <li class="text-slate-200">
              Developed and integrated Kafka worker services, utilizing .NET
              Core 8, into an existing architecture supporting over-the-air
              vehicle software updates, enhancing system efficiency and
              scalability.
            </li>

            <li class="text-slate-200">
              Developed and launched a pivotal parameter filtering feature to
              accommodate the expansion to 800 changeable vehicle parameters
              within a web app that serves millions, enhancing user satisfaction
              by enabling system-specific parameter views.
            </li>
            <li class="text-slate-200">
              Delivered 7 full-stack features to production in 6 months, while
              working on and automating production support cases daily and
              maintaining zero Checkmarx vulnerabilities.
            </li>
          </ul>
        </div>
        <div class="my-4">
          <h3 class="font-semibold text-slate-200">
            Microsoft, Bremerton, WA (Remote) – Student, Oct 2022 – Feb 2023
          </h3>
          <ul class="list-disc ml-6">
            <li class="text-slate-200">
              Graduated from the Microsoft Software and Systems Academy Cloud
              App Dev program. Built cloud-based web and desktop apps, Azure
              Functions, and covered most key Azure services. Also offered
              opportunities for mentorship from Senior MS employees.
            </li>
            <li class="text-slate-200">
              Committed, reviewed, and collaborated on code and tests for the
              Microsoft-owned GitHub repository dotnet/Roslyn, the C# and VB
              compiler, which also helped fix 9 issues.
            </li>
          </ul>
        </div>
        <div class="my-4">
          <h3 class="font-semibold text-slate-200">
            US Navy, USS Nimitz – Content Development & Creative Director, Jan
            2016 – Mar 2023
          </h3>
          <ul class="list-disc ml-6">
            <li class="text-slate-200">
              Led a team of 40 sailors in creating media campaigns, reaching
              over 500,000 viewers, in collaboration with international
              partners.
            </li>
            <li class="text-slate-200">
              Developed and delivered training programs designed to foster a
              culture of open-mindedness and efficiency.
            </li>
          </ul>
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
            <li class="text-slate-200">Can Spell: C++, PHP, Go, Kotlin</li>
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
