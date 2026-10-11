<template>
  <section
    id="about"
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
      -right-40 bottom-20
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
        class="mx-auto mb-14 max-w-3xl text-center"
      >

        <div
          class="mb-4 flex items-center justify-center gap-3"
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
            Tentang Saya
          </span>
        </div>

        <h2
          class="text-4xl font-bold
          tracking-tight
          text-white
          sm:text-5xl"
        >
          Mengenal Saya
          <span class="text-blue-500">Lebih Dekat.</span>
        </h2>

        <p
          class="mt-5
          text-base
          leading-8
          text-slate-400
          sm:text-lg"
        >
          Saya adalah pelajar Rekayasa Perangkat Lunak
          yang memiliki ketertarikan pada desain antarmuka
          dan pengembangan website.
        </p>

      </div>

      <!-- ABOUT GRID -->
      <div
        class="grid gap-6
        lg:grid-cols-3"
      >

        <!-- PROFIL -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          backdrop-blur-sm
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="mb-6 flex
            h-12 w-12
            items-center justify-center
            rounded-2xl
            bg-blue-500/10
            text-xl text-blue-400
            transition duration-300
            group-hover:bg-blue-500
            group-hover:text-white"
          >
            ✦
          </div>

          <h3
            class="text-xl
            font-semibold
            text-white"
          >
            Profil Singkat
          </h3>

          <p
            class="mt-4
            text-sm
            leading-7
            text-slate-400"
          >
            Saya terbiasa mempelajari dasar-dasar
            pemrograman dan membuat berbagai project
            sederhana selama belajar di jurusan
            Rekayasa Perangkat Lunak.
          </p>

        </div>

        <!-- YANG DIPELAJARI -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          backdrop-blur-sm
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="mb-6 flex
            h-12 w-12
            items-center justify-center
            rounded-2xl
            bg-blue-500/10
            text-xl text-blue-400
            transition duration-300
            group-hover:bg-blue-500
            group-hover:text-white"
          >
            ◇
          </div>

          <h3
            class="text-xl
            font-semibold
            text-white"
          >
            Yang Saya Pelajari
          </h3>

          <p
            class="mt-4
            text-sm
            leading-7
            text-slate-400"
          >
            Selama belajar di sekolah, saya mempelajari
            HTML, CSS, JavaScript, PHP, database,
            serta dasar pengembangan aplikasi web.
          </p>

        </div>

        <!-- FOKUS -->
        <div
          class="group
          rounded-3xl
          border border-white/10
          bg-white/[0.03]
          p-7
          backdrop-blur-sm
          transition duration-500
          hover:-translate-y-1
          hover:border-blue-500/30
          hover:bg-blue-500/[0.04]"
        >

          <div
            class="mb-6 flex
            h-12 w-12
            items-center justify-center
            rounded-2xl
            bg-blue-500/10
            text-xl text-blue-400
            transition duration-300
            group-hover:bg-blue-500
            group-hover:text-white"
          >
            ◎
          </div>

          <h3
            class="text-xl
            font-semibold
            text-white"
          >
            Fokus Saya
          </h3>

          <p
            class="mt-4
            text-sm
            leading-7
            text-slate-400"
          >
            Saat ini saya lebih tertarik untuk
            mengembangkan kemampuan di bidang
            UI/UX Design dan membuat tampilan
            website yang menarik serta nyaman digunakan.
          </p>

        </div>

      </div>

     <!-- BOTTOM INFO -->
    <div
      class="mt-6
      rounded-3xl
      border border-white/10
      bg-[#0d1b2e]/60
      p-7
      backdrop-blur-sm
      transition duration-500
      hover:border-blue-500/20"
    >
      <p
        class="text-xs
        uppercase
        tracking-[0.2em]
        text-blue-400"
      >
        Saat Ini
      </p>

      <h3
        class="mt-2
        text-xl
        font-semibold
        text-white"
      >
        Terus belajar dan mengembangkan skill.
      </h3>

      <p
        class="mt-3
        w-full
        text-sm
        leading-7
        text-slate-400"
      >
      Saat ini saya terus mengembangkan kemampuan di bidang
  desain dan pengembangan website melalui berbagai project
  yang saya kerjakan selama belajar. Saya juga tertarik untuk
  mempelajari hal-hal baru, meningkatkan kemampuan dalam
  membuat tampilan yang rapi dan nyaman digunakan, serta
  mendapatkan pengalaman yang dapat membantu saya berkembang
  menjadi lebih baik.
      </p>
    </div>

        </div>

  </section>
</template>