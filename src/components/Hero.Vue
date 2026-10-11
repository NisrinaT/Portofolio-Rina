<template>
  <section
    id="home"
    class="relative min-h-screen overflow-hidden
    bg-[#07111f] px-6 pt-28"
  >

    <!-- ========================================
         BACKGROUND
    ========================================= -->

    <!-- Blue Glow -->
    <div
      class="pointer-events-none absolute -left-40 top-20
      h-96 w-96 rounded-full
      bg-blue-600/10
      blur-[120px]
      animate-float"
    ></div>

    <div
      class="pointer-events-none absolute -right-40 bottom-0
      h-[500px] w-[500px] rounded-full
      bg-blue-500/10
      blur-[140px]
      animate-float-reverse"
    ></div>


    <!-- Grid -->
    <div
      class="pointer-events-none absolute inset-0 opacity-[0.035]"
      style="
        background-image:
          linear-gradient(#60a5fa 1px, transparent 1px),
          linear-gradient(90deg, #60a5fa 1px, transparent 1px);
        background-size: 60px 60px;
      "
    ></div>


    <!-- Top Line -->
    <div
      class="absolute left-0 right-0 top-0 h-px
      bg-gradient-to-r
      from-transparent
      via-blue-500/40
      to-transparent"
    ></div>


    <!-- ========================================
         MAIN CONTENT
    ========================================= -->

    <div
      class="relative mx-auto grid
      min-h-[calc(100vh-112px)]
      max-w-6xl
      items-center
      gap-12
      lg:grid-cols-[1.1fr_0.9fr]"
    >


      <!-- ====================================
           LEFT CONTENT
      ===================================== -->

      <div>

        <!-- Label -->
        <div
          class="animate-fade-up mb-5
          flex items-center gap-3"
        >

          <span
            class="h-2 w-2 rounded-full
            bg-blue-500
            shadow-lg
            shadow-blue-500/50"
          ></span>

          <span
            class="text-sm font-medium
            uppercase tracking-[0.2em]
            text-blue-400"
          >
            Portofolio Pribadi
          </span>

        </div>


        <!-- ====================================
             MAIN TITLE
        ===================================== -->

      <h1
        class="title-hero
        text-5xl font-bold
        leading-[1.05]
        tracking-tight
        text-white
        sm:text-6xl
        lg:text-7xl"
        >

        <span
            class="hero-line hero-line-1 block"
        >
            Halo, saya
        </span>


        <span
            class="hero-line hero-line-2 mt-2 block text-slate-300"
        >

            Nisrina

            <span class="text-blue-500">
            Tsabitah.
            </span>

        </span>

        </h1>


        <!-- ====================================
             DESCRIPTION
        ===================================== -->

        <p
          class="animate-fade-up-delay-2
          mt-7 max-w-xl
          text-base leading-8
          text-slate-400
          sm:text-lg"
        >
          Saya seorang pelajar
          <span class="font-medium text-slate-200">
            Rekayasa Perangkat Lunak
          </span>
          yang tertarik pada UI/UX Design
          dan pengembangan website.
        </p>


        <!-- ====================================
             BUTTONS
        ===================================== -->

        <div
          class="animate-fade-up-delay-3
          mt-8 flex flex-wrap gap-4"
        >

          <!-- Primary -->
          <a
            href="#projects"
            class="group flex items-center gap-3
            rounded-xl
            bg-blue-600
            px-6 py-3.5
            text-sm font-semibold
            text-white
            shadow-lg
            shadow-blue-600/20
            transition duration-300
            hover:-translate-y-1
            hover:bg-blue-500
            hover:shadow-blue-500/30"
          >

            Lihat Proyek

            <span
              class="transition duration-300
              group-hover:translate-x-1"
            >
              →
            </span>

          </a>


          <!-- Secondary -->
          <a
            href="#about"
            class="rounded-xl
            border border-white/10
            bg-white/[0.03]
            px-6 py-3.5
            text-sm font-semibold
            text-slate-300
            transition duration-300
            hover:-translate-y-1
            hover:border-blue-500/40
            hover:bg-blue-500/10
            hover:text-white"
          >
            Tentang Saya
          </a>

        </div>

      </div>


      <!-- ====================================
           RIGHT PROFILE
      ===================================== -->

      <div
        class="relative hidden
        h-[500px]
        lg:block"
      >

        <!-- Glow -->
        <div
          class="absolute left-1/2 top-1/2
          h-80 w-80
          -translate-x-1/2
          -translate-y-1/2
          rounded-full
          bg-blue-600/15
          blur-[100px]
          animate-pulse-soft"
        ></div>


        <!-- Outer Circle -->
        <div
          class="absolute left-1/2 top-1/2
          h-[400px] w-[400px]
          -translate-x-1/2
          -translate-y-1/2
          rounded-full
          border border-blue-500/15"
        ></div>


        <!-- Inner Circle -->
        <div
          class="absolute left-1/2 top-1/2
          h-[340px] w-[340px]
          -translate-x-1/2
          -translate-y-1/2
          rounded-full
          border border-white/5"
        ></div>


        <!-- ====================================
             PHOTO
        ===================================== -->

        <div
          class="absolute left-1/2 top-1/2
          h-[390px] w-[300px]
          -translate-x-1/2
          -translate-y-1/2
          overflow-hidden
          rounded-[2rem]
          border border-blue-400/30
          bg-[#0d1b2e]
          shadow-2xl
          shadow-blue-950/40
          rotate-2
          transition-all duration-500
          hover:rotate-0
          hover:scale-[1.02]
          hover:border-blue-400/50"
        >

          <img
            src="/images/profile.jpg"
            alt="Foto Nisrina Tsabitah"
            class="h-full w-full object-cover"
          />


          <!-- Gradient -->
          <div
            class="absolute inset-x-0 bottom-0
            h-40
            bg-gradient-to-t
            from-[#07111f]
            via-[#07111f]/60
            to-transparent"
          ></div>


          <!-- Name -->
          <div
            class="absolute bottom-6 left-6"
          >

            <p
              class="mt-1 text-lg
              font-semibold text-white"
            >
              Nisrina Tsabitah
            </p>

          </div>

        </div>


        <!-- ====================================
             FOKUS UTAMA CARD
        ===================================== -->

        <div
          class="absolute right-2 top-8
          z-20
          rounded-2xl
          border border-white/10
          bg-[#0d1b2e]/90
          px-5 py-4
          shadow-xl
          shadow-black/20
          backdrop-blur-xl
          animate-float"
        >

          <div class="flex items-center gap-3">

            <!-- Icon -->
            <div
              class="flex h-9 w-9
              shrink-0
              items-center justify-center
              rounded-xl
              bg-blue-500/10
              text-blue-400"
            >
              ✦
            </div>


            <!-- Text -->
            <div>

              <p
                class="text-xs text-slate-500"
              >
                Fokus Utama
              </p>

              <p
                class="mt-1 text-sm
                font-semibold text-white"
              >
                UI/UX Design
              </p>

            </div>

          </div>

        </div>


        <!-- Decorative Dot -->
        <div
          class="absolute right-20 bottom-24
          h-3 w-3 rounded-full
          bg-blue-500
          shadow-lg
          shadow-blue-500/50
          animate-pulse-soft"
        ></div>

      </div>

    </div>


    <!-- ========================================
         SCROLL
    ========================================= -->

    <div
      class="absolute bottom-7 left-1/2
      hidden -translate-x-1/2
      items-center gap-3
      md:flex"
    >

      <span
        class="text-[10px]
        uppercase
        tracking-[0.3em]
        text-slate-600"
      >
        Scroll untuk menjelajah
      </span>

      <span class="text-slate-600">
        ↓
      </span>

    </div>

  </section>
</template>