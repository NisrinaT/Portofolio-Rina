<script setup>
import { ref, computed } from 'vue'
import { projects } from "../data/projects";

const projectsPerPage = 3

const totalPages = computed(() => {
  return Math.ceil(projects.length / projectsPerPage)
})

const slider = ref(null)
const currentSlide = ref(0)

const slideNext = () => {
  if (!slider.value) return

  if (currentSlide.value < totalPages.value - 1) {
    currentSlide.value++
    scrollToPage(currentSlide.value)
  }
}

const slidePrev = () => {
  if (!slider.value) return

  if (currentSlide.value > 0) {
    currentSlide.value--
    scrollToPage(currentSlide.value)
  }
}

const goToSlide = (index) => {
  currentSlide.value = index
  scrollToPage(index)
}

const scrollToPage = (page) => {
  if (!slider.value) return

  const sliderWidth = slider.value.clientWidth

  slider.value.scrollTo({
    left: page * sliderWidth,
    behavior: 'smooth'
  })
}
</script>

<template>
  <section
    id="projects"
    class="relative overflow-hidden
    bg-[#07111f]
    px-6 py-24"
  >

    <!-- BACKGROUND GLOW -->
    <div
      class="pointer-events-none absolute
      -left-40 top-20
      h-96 w-96
      rounded-full
      bg-blue-600/10
      blur-[120px]"
    ></div>

    <div
      class="pointer-events-none absolute
      -right-40 bottom-0
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

      <!-- HEADER -->
      <div
        class="mx-auto mb-12
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
            Proyek
          </span>
        </div>

        <h2
          class="text-4xl font-bold
          tracking-tight
          text-white
          sm:text-5xl"
        >
          Proyek yang Saya
          <span class="text-blue-500">
            Kerjakan.
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
          Beberapa proyek yang saya kerjakan selama belajar,
          mulai dari desain UI/UX hingga pengembangan aplikasi
          dan website.
        </p>

      </div>


      <!-- CAROUSEL -->
      <div class="relative">

        <!-- PREVIOUS -->
        <button
          @click="slidePrev"
          :disabled="currentSlide === 0"
          class="absolute
          -left-3 top-1/2
          z-20
          hidden
          h-10 w-10
          -translate-y-1/2
          items-center justify-center
          rounded-full
          border border-white/10
          bg-[#0d1b2e]
          text-slate-400
          shadow-lg
          transition
          hover:border-blue-500/40
          hover:bg-blue-500
          hover:text-white
          disabled:pointer-events-none
          disabled:opacity-30
          lg:flex"
        >
          ←
        </button>


          <!-- PROJECT LIST -->
          <div
            ref="slider"
            class="flex
            gap-5
            overflow-x-auto
            scroll-smooth
            snap-x snap-mandatory
            py-4
            [scrollbar-width:none]
            [&::-webkit-scrollbar]:hidden"
          >

          <!-- PROJECT CARD -->
          <router-link
            v-for="project in projects"
            :key="project.title"
            :to="`/project/${project.id}`"
            class="group
            w-[82%]
            flex-none
            snap-start
            overflow-hidden
            rounded-2xl
            border border-white/[0.08]
            bg-[#0b1728]
            transition-all duration-300
            hover:-translate-y-1
            hover:border-blue-500/30
            md:w-[calc((100%-40px)/3)]"
          >

            <!-- IMAGE -->
            <div
              class="relative
              aspect-[16/8]
              overflow-hidden
              bg-[#101d30]"
            >

              <img
                :src="Array.isArray(project.image) ? project.image[0] : project.image"
                :alt="project.title"
                class="h-full w-full
                object-cover
                transition duration-500
                group-hover:scale-105"
              />

              <!-- IMAGE OVERLAY -->
              <div
                class="absolute inset-0
                bg-gradient-to-t
                from-[#07111f]/50
                to-transparent"
              ></div>

              <!-- CATEGORY -->
              <span
                class="absolute
                left-4 top-4
                rounded-full
                border border-white/10
                bg-[#07111f]/80
                px-3 py-1
                text-[11px]
                font-medium
                text-slate-300
                backdrop-blur-md"
              >
                {{ project.category }}
              </span>

            </div>


            <!-- CARD CONTENT -->
            <div class="p-5">

              <!-- TITLE -->
              <h3
                class="text-lg
                font-semibold
                tracking-tight
                text-white
                transition
                group-hover:text-blue-400"
              >
                {{ project.title }}
              </h3>


              <!-- DESCRIPTION -->
              <p
                class="mt-2
                line-clamp-2
                text-xs
                leading-6
                text-slate-400"
              >
                {{ project.description }}
              </p>


              <!-- TECHNOLOGIES -->
              <div
                class="mt-4
                flex flex-wrap
                gap-1.5"
              >

                <span
                  v-for="tech in project.technologies"
                  :key="tech"
                  class="rounded-full
                  border border-white/[0.08]
                  bg-white/[0.03]
                  px-2.5 py-1
                  text-[10px]
                  text-slate-400"
                >
                  {{ tech }}
                </span>

              </div>

            </div>

          </router-link>

        </div>


        <!-- NEXT -->
        <button
          @click="slideNext"
          :disabled="currentSlide === totalPages - 1"
          class="absolute
          -right-3 top-1/2
          z-20
          hidden
          h-10 w-10
          -translate-y-1/2
          items-center justify-center
          rounded-full
          border border-white/10
          bg-[#0d1b2e]
          text-slate-400
          shadow-lg
          transition
          hover:border-blue-500/40
          hover:bg-blue-500
          hover:text-white
          disabled:pointer-events-none
          disabled:opacity-30
          lg:flex"
        >
          →
        </button>

      </div>

    <!-- PAGINATION-->
      <div
        class="mt-7
        flex items-center
        justify-center gap-2"
        >
        <button
            v-for="index in totalPages"
            :key="index"
            @click="goToSlide(index - 1)"
            class="h-1.5
            rounded-full
            transition-all duration-300"
            :class="
            currentSlide === index - 1
                ? 'w-7 bg-blue-500'
                : 'w-1.5 bg-slate-700 hover:bg-slate-500'
            "
            :aria-label="`Slide ${index}`"
        ></button>
        </div>


      <!-- MOBILE HINT -->
      <p
        class="mt-4
        text-center
        text-[11px]
        text-slate-600
        md:hidden"
      >
        Geser untuk melihat project lainnya →
      </p>

    </div>

  </section>
</template>