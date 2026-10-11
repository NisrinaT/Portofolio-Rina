```vue
<script setup>
import { computed, ref, watch } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { projects } from '../data/projects.js'

const route = useRoute()
const router = useRouter()

const project = computed(() =>
  projects.find((item) => String(item.id) === String(route.params.id))
)

const projectImages = computed(() => {
  if (!project.value) return []

  if (Array.isArray(project.value.image)) {
    return project.value.image
  }

  if (Array.isArray(project.value.images)) {
    return project.value.images
  }

  return project.value.image ? [project.value.image] : []
})

const currentImage = ref(0)
const isImageModalOpen = ref(false)

watch(
  () => route.params.id,
  () => {
    currentImage.value = 0
    isImageModalOpen.value = false
  }
)

function nextImage() {
  if (!projectImages.value.length) return

  currentImage.value =
    (currentImage.value + 1) % projectImages.value.length
}

function previousImage() {
  if (!projectImages.value.length) return

  currentImage.value =
    (currentImage.value - 1 + projectImages.value.length) %
    projectImages.value.length
}

function selectImage(index) {
  currentImage.value = index
}

function openImageModal() {
  if (projectImages.value.length) {
    isImageModalOpen.value = true
  }
}

function closeImageModal() {
  isImageModalOpen.value = false
}

// Menentukan nama project yang bisa diklik di deskripsi
const linkedProjectName = computed(() => {
  if (!project.value?.projectLink) return null

  const title = project.value.title || ''

  if (/\binnerly\b/i.test(title)) return 'Innerly'
  if (/\bvoxa\b/i.test(title)) return 'Voxa'

  return null
})

// Deskripsi tetap mengambil data dari projects.js
const descriptionParts = computed(() => {
  const description = project.value?.description || ''
  const name = linkedProjectName.value

  if (!name) {
    return [{ text: description, isLink: false }]
  }

  const parts = description.split(new RegExp(`(${name})`, 'gi'))

  return parts.map((part) => ({
    text: part,
    isLink: part.toLowerCase() === name.toLowerCase()
  }))
})
</script>

<template>
  <main class="min-h-screen bg-[#0B1120] px-5 py-12 text-white sm:px-8 lg:px-16">
    <div class="mx-auto max-w-6xl">
      <button
        @click="router.back()"
        class="mb-8 inline-flex items-center gap-2 text-sm text-gray-400 transition hover:text-[#FFC107]"
      >
        <span aria-hidden="true">←</span>
        Kembali
      </button>

      <div
        v-if="project"
        class="grid items-start gap-10 lg:grid-cols-2 lg:gap-14"
      >
        <!-- Slider gambar -->
        <section class="min-w-0">
          <div
            class="relative overflow-hidden rounded-2xl border border-white/10 bg-[#131C2E]"
          >
            <div class="aspect-[4/3]">
              <img
                v-if="projectImages.length"
                :key="projectImages[currentImage]"
                :src="projectImages[currentImage]"
                :alt="`${project.title} - gambar ${currentImage + 1}`"
                class="h-full w-full cursor-zoom-in object-cover"
                @click="openImageModal"
              />

              <div
                v-else
                class="flex h-full items-center justify-center text-sm text-gray-500"
              >
                Gambar belum tersedia
              </div>
            </div>

            <!-- Panah kiri -->
            <button
              v-if="projectImages.length > 1"
              @click="previousImage"
              aria-label="Foto sebelumnya"
              class="absolute left-3 top-1/2 flex h-9 w-9 -translate-y-1/2 items-center justify-center rounded-full bg-black/45 text-white backdrop-blur-sm transition hover:bg-[#FFC107] hover:text-black"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="18"
                height="18"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path d="m15 18-6-6 6-6" />
              </svg>
            </button>

            <!-- Panah kanan -->
            <button
              v-if="projectImages.length > 1"
              @click="nextImage"
              aria-label="Foto selanjutnya"
              class="absolute right-3 top-1/2 flex h-9 w-9 -translate-y-1/2 items-center justify-center rounded-full bg-black/45 text-white backdrop-blur-sm transition hover:bg-[#FFC107] hover:text-black"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="18"
                height="18"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path d="m9 18 6-6-6-6" />
              </svg>
            </button>

            <!-- Nomor gambar -->
            <div
              v-if="projectImages.length > 1"
              class="absolute bottom-3 right-3 rounded-full bg-black/50 px-3 py-1 text-xs text-white backdrop-blur-sm"
            >
              {{ currentImage + 1 }} / {{ projectImages.length }}
            </div>
          </div>

          <!-- Pagination dots -->
          <div
            v-if="projectImages.length > 1"
            class="mt-4 flex justify-center gap-2"
          >
            <button
              v-for="(image, index) in projectImages"
              :key="image + index"
              @click="selectImage(index)"
              :aria-label="`Tampilkan gambar ${index + 1}`"
              :class="[
                'h-2 rounded-full transition-all duration-300',
                currentImage === index
                  ? 'w-6 bg-[#FFC107]'
                  : 'w-2 bg-white/30 hover:bg-white/60'
              ]"
            ></button>
          </div>

          <!-- Thumbnail -->
          <div
            v-if="projectImages.length > 1"
            class="thumbnail-slider mt-4 flex gap-3 overflow-x-auto pb-2"
          >
            <button
              v-for="(image, index) in projectImages"
              :key="image + '-thumb-' + index"
              @click="selectImage(index)"
              :class="[
                'h-16 w-24 shrink-0 overflow-hidden rounded-lg border-2 transition',
                currentImage === index
                  ? 'border-[#FFC107]'
                  : 'border-white/10 opacity-60 hover:opacity-100'
              ]"
            >
              <img
                :src="image"
                :alt="`Thumbnail ${index + 1}`"
                class="h-full w-full object-cover"
              />
            </button>
          </div>
        </section>

        <!-- Detail proyek -->
        <section class="min-w-0">
          <p
            class="mb-3 text-sm font-medium uppercase tracking-[0.2em] text-[#FFC107]"
          >
            {{ project.category }}
          </p>

          <h1 class="mb-5 text-3xl font-bold leading-tight sm:text-4xl">
            {{ project.title }}
          </h1>

          <!-- Deskripsi dengan link Voxa / Innerly -->
          <p class="leading-7 text-gray-400">
            <template
              v-for="(part, index) in descriptionParts"
              :key="index"
            >
              <a
                v-if="part.isLink"
                :href="project.projectLink"
                target="_blank"
                rel="noopener noreferrer"
                class="text-[#FFC107] transition hover:underline"
              >{{ part.text }}</a>

              <template v-else>{{ part.text }}</template>
            </template>
          </p>

          <!-- Tools & Technologies -->
          <div class="mt-8">
            <h2 class="mb-4 text-lg font-semibold">
              Tools & Technologies
            </h2>

            <div class="flex flex-wrap gap-2">
              <span
                v-for="technology in project.technologies || []"
                :key="technology"
                class="rounded-lg border border-white/10 bg-white/5 px-3 py-2 text-sm text-gray-300"
              >
                {{ technology }}
              </span>
            </div>
          </div>
        </section>
      </div>

      <div v-else class="py-20 text-center">
        <h1 class="text-2xl font-bold">Proyek tidak ditemukan</h1>
        <p class="mt-3 text-gray-400">
          Proyek yang kamu cari tidak tersedia.
        </p>
      </div>
    </div>
  </main>

  <!-- Popup gambar ukuran utuh -->
  <Teleport to="body">
    <div
      v-if="isImageModalOpen"
      class="fixed inset-0 z-[100] flex items-center justify-center bg-black/90 p-4 sm:p-8"
      @click.self="closeImageModal"
      @keydown.esc="closeImageModal"
    >
      <!-- Tombol tutup -->
      <button
        @click="closeImageModal"
        aria-label="Tutup gambar"
        class="absolute right-5 top-5 z-10 flex h-10 w-10 items-center justify-center rounded-full bg-white/10 text-white transition hover:bg-[#FFC107] hover:text-black"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="22"
          height="22"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
        >
          <path d="m18 6-12 12" />
          <path d="m6 6 12 12" />
        </svg>
      </button>

      <!-- Gambar ditampilkan utuh -->
      <img
        :src="projectImages[currentImage]"
        :alt="`${project.title} - gambar ukuran asli`"
        class="max-h-[90vh] max-w-full rounded-lg object-contain"
        @click.stop
      />
    </div>
  </Teleport>
</template>

<style scoped>
.thumbnail-slider {
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.thumbnail-slider::-webkit-scrollbar {
  display: none;
}
</style>
```