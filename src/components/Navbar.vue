<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const navItems = [
  { name: 'Beranda', href: '#home' },
  { name: 'Tentang', href: '#about' },
  { name: 'Keahlian', href: '#skills' },
  { name: 'Proyek', href: '#projects' },
  { name: 'Kontak', href: '#contact' }
]
</script>

<template>
  <nav class="fixed left-0 right-0 top-0 z-50 px-5 pt-5">
  <div
    class="mx-auto flex max-w-6xl items-center justify-between
    rounded-full border border-white/10
    bg-[#0b1628]/75 px-6 py-2.5
    shadow-lg shadow-black/10
    backdrop-blur-xl"
  >

    <!-- Logo -->
    <a
      href="#home"
      class="text-lg font-bold tracking-tight text-white
      transition duration-300 hover:text-blue-400"
    >
      Portofolio
      <span class="text-blue-500">Rina</span>
    </a>


    <!-- Navigation -->
    <div class="hidden items-center gap-8 md:flex">
      <a
        v-for="item in navItems"
        :key="item.name"
        :href="item.href"
        class="text-sm font-medium text-slate-400
        transition duration-300
        hover:text-white"
      >
        {{ item.name }}
      </a>
    </div>


    <!-- CTA -->
    <a
      href="#contact"
      class="hidden rounded-full
      border border-blue-500/30
      bg-blue-500/10
      px-5 py-2.5
      text-sm font-semibold
      text-blue-400
      transition duration-300
      hover:border-blue-400/50
      hover:bg-blue-500
      hover:text-white
      md:block"
    >
      Hubungi Saya
    </a>


    <!-- Mobile -->
    <button
      @click="menuOpen = !menuOpen"
      class="text-xl text-white md:hidden"
    >
      ☰
    </button>

  </div>


  <!-- Mobile Menu -->
  <div
    v-if="menuOpen"
    class="mx-auto mt-2 max-w-6xl
    rounded-2xl border border-white/10
    bg-[#0b1628] p-3
    shadow-2xl md:hidden"
  >

    <a
      v-for="item in navItems"
      :key="item.name"
      :href="item.href"
      @click="menuOpen = false"
      class="block rounded-xl px-4 py-3
      text-sm text-slate-400
      transition hover:bg-white/5
      hover:text-white"
    >
      {{ item.name }}
    </a>

  </div>

</nav>
</template>