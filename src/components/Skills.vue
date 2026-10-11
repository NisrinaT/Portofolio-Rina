<template>
  <section
    id="skills"
    class="relative overflow-hidden
    bg-[#07111f]
    px-6 py-24"
  >

    <!-- BACKGROUND GLOW -->
    <div
      class="pointer-events-none absolute
      -right-40 top-20
      h-96 w-96
      rounded-full
      bg-blue-600/10
      blur-[120px]"
    ></div>

    <div
      class="pointer-events-none absolute
      -left-40 bottom-0
      h-96 w-96
      rounded-full
      bg-blue-500/5
      blur-[120px]"
    ></div>

    <!-- CONTENT -->
    <div
      class="relative mx-auto
      max-w-6xl"
    >

      <!-- SECTION HEADER -->
      <div
        class="mx-auto mb-14
        max-w-3xl
        text-center"
      >

        <div
          class="mb-4
          flex items-center
          justify-center gap-3"
        >
          <span
            class="h-2 w-2
            rounded-full
            bg-blue-500
            shadow-lg
            shadow-blue-500/50"
          ></span>

          <span
            class="text-sm font-medium
            uppercase tracking-[0.2em]
            text-blue-400"
          >
            Keahlian
          </span>
        </div>

        <h2
          class="text-4xl font-bold
          tracking-tight
          text-white
          sm:text-5xl"
        >
          Skill yang Saya
          <span class="text-blue-500">
            Pelajari.
          </span>
        </h2>

        <p
          class="mx-auto mt-5
          max-w-2xl
          text-base
          leading-8
          text-slate-400
          sm:text-lg"
        >
          Beberapa teknologi dan tools yang saya pelajari
          selama menempuh pendidikan serta digunakan dalam
          berbagai project yang saya kerjakan.
        </p>

      </div>

      <!-- SKILLS GRID -->
      <div
        class="grid gap-6
        md:grid-cols-2"
      >

        <!-- UI/UX -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="flex items-start
            justify-between"
          >

            <div
              class="flex h-12 w-12
              items-center justify-center
              rounded-2xl
              bg-blue-500/10
              text-blue-400
              transition duration-300
              group-hover:bg-blue-500
              group-hover:text-white"
            >
              ✦
            </div>

            <span
              class="text-xs
              uppercase
              tracking-widest
              text-slate-600"
            >
              01
            </span>

          </div>

          <h3
            class="mt-6
            text-xl
            font-semibold
            text-white"
          >
            UI/UX Design
          </h3>

          <p
            class="mt-3
            text-sm
            leading-7
            text-slate-400"
          >
            Membuat rancangan tampilan aplikasi dan website
            dengan memperhatikan struktur, visual, serta
            kenyamanan pengguna.
          </p>

          <div
            class="mt-6
            flex flex-wrap gap-2"
          >
            <span
                v-for="skill in uiuxSkills"
                :key="skill"
                class="rounded-full
                border border-white/10
                bg-white/[0.03]
                px-3 py-1.5
                text-xs
                text-slate-300"
            >
              {{ skill }}
            </span>
          </div>

        </div>

        <!-- FRONTEND -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="flex items-start
            justify-between"
          >

            <div
              class="flex h-12 w-12
              items-center justify-center
              rounded-2xl
              bg-blue-500/10
              text-blue-400
              transition duration-300
              group-hover:bg-blue-500
              group-hover:text-white"
            >
              &lt;/&gt;
            </div>

            <span
              class="text-xs
              uppercase
              tracking-widest
              text-slate-600"
            >
              02
            </span>

          </div>

          <h3
            class="mt-6
            text-xl
            font-semibold
            text-white"
          >
            Frontend Development
          </h3>

          <p
            class="mt-3
            text-sm
            leading-7
            text-slate-400"
          >
            Mengembangkan tampilan website menggunakan
            teknologi frontend dengan struktur yang rapi
            dan responsif.
          </p>

          <div
            class="mt-6
            flex flex-wrap gap-2"
          >
            <span
              v-for="skill in frontendSkills"
              :key="skill"
              class="rounded-full
              border border-white/10
              bg-white/[0.03]
              px-3 py-1.5
              text-xs
              text-slate-300"
            >
              {{ skill }}
            </span>
          </div>

        </div>

        <!-- BACKEND -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="flex items-start
            justify-between"
          >

            <div
              class="flex h-12 w-12
              items-center justify-center
              rounded-2xl
              bg-blue-500/10
              text-blue-400
              transition duration-300
              group-hover:bg-blue-500
              group-hover:text-white"
            >
              { }
            </div>

            <span
              class="text-xs
              uppercase
              tracking-widest
              text-slate-600"
            >
              03
            </span>

          </div>

          <h3
            class="mt-6
            text-xl
            font-semibold
            text-white"
          >
            Backend Development
          </h3>

          <p
            class="mt-3
            text-sm
            leading-7
            text-slate-400"
          >
            Mempelajari pengembangan sisi server untuk
            mengolah data dan membangun fungsi pada
            aplikasi berbasis web.
          </p>

          <div
            class="mt-6
            flex flex-wrap gap-2"
          >
            <span
              v-for="skill in backendSkills"
              :key="skill"
              class="rounded-full
              border border-white/10
              bg-white/[0.03]
              px-3 py-1.5
              text-xs
              text-slate-300"
            >
              {{ skill }}
            </span>
          </div>

        </div>

        <!-- TOOLS -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="flex items-start
            justify-between"
          >

            <div
              class="flex h-12 w-12
              items-center justify-center
              rounded-2xl
              bg-blue-500/10
              text-blue-400
              transition duration-300
              group-hover:bg-blue-500
              group-hover:text-white"
            >
              ⚙
            </div>

            <span
              class="text-xs
              uppercase
              tracking-widest
              text-slate-600"
            >
              04
            </span>

          </div>

          <h3
            class="mt-6
            text-xl
            font-semibold
            text-white"
          >
            Database & Tools
          </h3>

          <p
            class="mt-3
            text-sm
            leading-7
            text-slate-400"
          >
            Tools yang saya gunakan untuk membantu proses
            pengembangan, pengelolaan database, dan
            pengerjaan project.
          </p>

          <div
            class="mt-6
            flex flex-wrap gap-2"
          >
            <span
              v-for="skill in toolsSkills"
              :key="skill"
              class="rounded-full
              border border-white/10
              bg-white/[0.03]
              px-3 py-1.5
              text-xs
              text-slate-300"
            >
              {{ skill }}
            </span>
          </div>

        </div>

      </div>

    </div>

  </section>
</template>

<script setup>
const uiuxSkills = [
  'Figma',
  'UI Design',
  'Prototyping',
  'Style Guide',
  'UI/UX Research'
]

const frontendSkills = [
  'HTML',
  'CSS',
  'JavaScript',
  'Tailwind CSS',
  'Vue.js',
  'React.js'
]

const backendSkills = [
  'PHP',
  'Laravel',
  'Node.js',
  'REST.API'
]

const toolsSkills = [
  'MySQL',
  'Git',
  'GitHub'
]
</script>