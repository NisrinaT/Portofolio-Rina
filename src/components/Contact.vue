```vue
<script setup>
import { ref } from 'vue'
import emailjs from '@emailjs/browser'

const isSending = ref(false)
const statusMessage = ref('')
const statusType = ref('')

const sendEmail = async (event) => {
  const form = event.target

  statusMessage.value = ''
  statusType.value = ''

  const serviceId = import.meta.env.VITE_EMAILJS_SERVICE_ID
  const templateId = import.meta.env.VITE_EMAILJS_TEMPLATE_ID
  const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY

  if (!serviceId || !templateId || !publicKey) {
    statusType.value = 'error'
    statusMessage.value =
      'Konfigurasi email belum lengkap. Silakan periksa file .env.'
    return
  }

  isSending.value = true

  try {
    await emailjs.sendForm(
      serviceId,
      templateId,
      form,
      { publicKey },
    )

    form.reset()

    statusType.value = 'success'
    statusMessage.value =
      'Pesan berhasil dikirim! Terima kasih sudah menghubungi saya.'
  } catch (error) {
    console.error('EmailJS error:', error)

    statusType.value = 'error'
    statusMessage.value =
      'Pesan gagal dikirim. Silakan coba lagi beberapa saat.'
  } finally {
    isSending.value = false
  }
}
</script>

<template>
  <section
    id="contact"
    class="relative overflow-hidden bg-[#07111f] px-6 py-24"
  >
    <!-- BACKGROUND ANIMATION -->
    <div class="pointer-events-none absolute inset-0 overflow-hidden">
      <div
        class="animate-glow absolute left-[28%] top-[32%] h-[430px] w-[430px] rounded-full bg-blue-600/[0.06] blur-[110px]"
      ></div>

      <div
        class="animate-glow-two absolute left-[38%] top-[42%] h-[260px] w-[260px] rounded-full bg-cyan-500/[0.05] blur-[90px]"
      ></div>

      <div
        class="animate-orbit absolute left-[30%] top-[15%] h-[390px] w-[390px] rounded-full border border-blue-400/[0.08]"
      ></div>

      <div
        class="animate-orbit-reverse absolute left-[37%] top-[24%] h-[285px] w-[285px] rounded-full border border-cyan-400/[0.07]"
      ></div>

      <div
        class="animate-core absolute left-[43%] top-[39%] h-[170px] w-[170px] rounded-full bg-blue-500/[0.07] blur-[45px]"
      ></div>

      <span
        class="animate-dot absolute left-[39%] top-[40%] h-2.5 w-2.5 rounded-full bg-blue-400 shadow-[0_0_20px_rgba(96,165,250,0.9)]"
      ></span>

      <span
        class="animate-dot-two absolute left-[51%] top-[31%] h-2 w-2 rounded-full bg-cyan-300 shadow-[0_0_18px_rgba(103,232,249,0.8)]"
      ></span>

      <span
        class="animate-dot-three absolute left-[47%] top-[64%] h-2.5 w-2.5 rounded-full bg-blue-500 shadow-[0_0_20px_rgba(59,130,246,0.8)]"
      ></span>

      <span
        class="animate-star absolute left-[47%] top-[27%] text-2xl text-blue-400"
      >
        ✦
      </span>

      <span
        class="animate-star-two absolute left-[57%] top-[57%] text-sm text-blue-300/40"
      >
        ✦
      </span>
    </div>

    <!-- MAIN CONTENT -->
    <div class="relative mx-auto max-w-6xl">
      <div class="contact-layout min-h-[calc(100vh-10rem)]">
        <!-- LEFT CONTENT -->
        <div class="contact-info">
          <div class="mb-5 flex items-center gap-3">
            <span
              class="h-2 w-2 rounded-full bg-blue-500 shadow-lg shadow-blue-500/50"
            ></span>

            <span
              class="text-xs font-medium uppercase tracking-[0.25em] text-blue-400"
            >
              Kontak
            </span>
          </div>

          <h1
            class="max-w-[540px] text-4xl font-bold leading-[1.08] tracking-tight text-white sm:text-5xl xl:text-[52px]"
          >
            Mari terhubung dan
            <span class="block text-blue-500">
              berkolaborasi.
            </span>
          </h1>

          <p class="mt-6 max-w-[430px] text-sm leading-7 text-slate-400 sm:text-base">
            Saya terbuka untuk berdiskusi mengenai project, desain UI/UX,
            pengembangan website, maupun kesempatan untuk belajar dan
            berkembang bersama.
          </p>

          <!-- CONTACT LIST -->
          <div class="mt-8 space-y-4">
            <!-- EMAIL -->
            <a href="mailto:akeerarael@gmail.com" class="contact-row group">
              <div class="contact-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.7"
                >
                  <rect x="3" y="5" width="18" height="14" rx="2" />
                  <path d="m3 7 9 6 9-6" />
                </svg>
              </div>

              <div class="min-w-0">
                <p class="contact-label">Email</p>
                <p class="contact-value">akeerarael@gmail.com</p>
              </div>

              <span class="contact-arrow">→</span>
            </a>

            <!-- WHATSAPP -->
            <a
              href="https://wa.me/qr/TTLRMTRKCALZO1"
              target="_blank"
              rel="noopener noreferrer"
              class="contact-row group"
            >
              <div class="contact-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.7"
                >
                  <path
                    d="M20 11.5a8 8 0 0 1-11.8 7L4 20l1.5-4.1A8 8 0 1 1 20 11.5Z"
                  />
                  <path
                    d="M8.5 9.2c.2 1.8 2.5 4.2 4.3 4.5.7.1 1.3-.4 1.7-.9"
                  />
                </svg>
              </div>

              <div class="min-w-0">
                <p class="contact-label">WhatsApp</p>
                <p class="contact-value">Hubungi melalui WhatsApp</p>
              </div>

              <span class="contact-arrow">→</span>
            </a>

            <!-- LOCATION -->
            <a
              href="https://maps.app.goo.gl/9BoecVWA2iDbBfpa7?g_st=ac"
              target="_blank"
              rel="noopener noreferrer"
              class="contact-row group"
            >
              <div class="contact-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.7"
                >
                  <path d="M20 10c0 5-8 11-8 11S4 15 4 10a8 8 0 1 1 16 0Z" />
                  <circle cx="12" cy="10" r="2.5" />
                </svg>
              </div>

              <div class="min-w-0">
                <p class="contact-label">Lokasi</p>
                <p class="contact-value">Jawa Timur</p>
              </div>

              <span class="contact-arrow">→</span>
            </a>

            <!-- INSTAGRAM -->
            <a
              href="https://www.instagram.com/craflwe?exln=MXJmcGY4a3Uwc291Mg=="
              target="_blank"
              rel="noopener noreferrer"
              class="contact-row group"
            >
              <div class="contact-icon">
                <svg
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="1.7"
                >
                  <rect x="3" y="3" width="18" height="18" rx="5" />
                  <circle cx="12" cy="12" r="4" />
                  <circle
                    cx="17.3"
                    cy="6.7"
                    r="1"
                    fill="currentColor"
                    stroke="none"
                  />
                </svg>
              </div>

              <div class="min-w-0">
                <p class="contact-label">Sosial Media</p>
                <p class="contact-value">Instagram</p>
              </div>

              <span class="contact-arrow">→</span>
            </a>

            <!-- GITHUB -->
            <a
              href="https://github.com/NisrinaT"
              target="_blank"
              rel="noopener noreferrer"
              class="contact-row group"
            >
              <div class="contact-icon">
                <svg viewBox="0 0 24 24" fill="currentColor">
                  <path
                    d="M12 .8a11.2 11.2 0 0 0-3.54 21.83c.56.1.77-.24.77-.54v-2.1c-3.13.68-3.79-1.5-3.79-1.5-.51-1.3-1.25-1.65-1.25-1.65-1.02-.7.08-.69.08-.69 1.13.08 1.72 1.16 1.72 1.16 1 .1.65 1.76 2.98 1.24.1-.72.39-1.21.7-1.49-2.5-.28-5.13-1.25-5.13-5.57 0-1.23.44-2.23 1.16-3.02-.12-.28-.5-1.43.11-2.98 0 0 .95-.3 3.08 1.15a10.7 10.7 0 0 1 5.6 0c2.13-1.45 3.08-1.15 3.08-1.15.61 1.55.23 2.7.11 2.98.72.79 1.16 1.79 1.16 3.02 0 4.33-2.64 5.28-5.15 5.56.4.35.75 1.04.75 2.1v3.1c0 .3.2.65.78.54A11.2 11.2 0 0 0 12 .8Z"
                  />
                </svg>
              </div>

              <div class="min-w-0">
                <p class="contact-label">GitHub</p>
                <p class="contact-value">Lihat profil saya</p>
              </div>

              <span class="contact-arrow">→</span>
            </a>
          </div>

          <!-- ROLE -->
          <div class="mt-8 flex flex-wrap items-center gap-3">
            <span class="h-px w-12 bg-blue-500/50"></span>
            <span class="text-[9px] uppercase tracking-[0.22em] text-blue-400">
              UI/UX Design
            </span>
            <span class="text-blue-500">•</span>
            <span class="text-[9px] uppercase tracking-[0.22em] text-blue-400">
              Web Development
            </span>
          </div>
        </div>

        <!-- RIGHT FORM -->
        <div
          class="contact-form rounded-2xl border border-blue-500/30 bg-[#08172a]/60 p-7 shadow-2xl shadow-blue-950/10 backdrop-blur-xl sm:p-8"
        >
          <p
            class="text-xs font-medium uppercase tracking-[0.25em] text-blue-400"
          >
            Kirim Pesan
          </p>

          <h2
            class="mt-4 max-w-sm text-3xl font-semibold leading-tight text-white sm:text-[34px]"
          >
            Ada yang ingin
            <span class="text-blue-500">disampaikan?</span>
          </h2>

          <p class="mt-5 max-w-md text-sm leading-7 text-slate-400">
            Isi form berikut, saya akan segera merespons pesan kamu
            secepatnya.
          </p>

          <!-- FORM EMAILJS -->
          <form
            class="mt-8 space-y-4"
            @submit.prevent="sendEmail"
          >
            <div class="grid gap-4 sm:grid-cols-2">
              <div class="form-box">
                <label for="contact-name">Nama</label>
                <input
                  id="contact-name"
                  type="text"
                  name="name"
                  placeholder="Masukkan nama kamu"
                  autocomplete="name"
                  required
                  :disabled="isSending"
                />
              </div>

              <div class="form-box">
                <label for="contact-email">Email</label>
                <input
                  id="contact-email"
                  type="email"
                  name="email"
                  placeholder="Masukkan email kamu"
                  autocomplete="email"
                  required
                  :disabled="isSending"
                />
              </div>
            </div>

            <div class="form-box">
              <label for="contact-message">Pesan</label>
              <textarea
                id="contact-message"
                name="message"
                rows="6"
                placeholder="Tulis pesan kamu di sini..."
                required
                :disabled="isSending"
              ></textarea>
            </div>

            <!-- STATUS -->
            <p
              v-if="statusMessage"
              role="status"
              aria-live="polite"
              class="text-sm leading-6"
              :class="
                statusType === 'success'
                  ? 'text-emerald-400'
                  : 'text-red-400'
              "
            >
              {{ statusMessage }}
            </p>

            <!-- SUBMIT BUTTON -->
            <div class="flex justify-end pt-2">
              <button
                type="submit"
                :disabled="isSending"
                class="group flex items-center gap-4 rounded-full bg-blue-600 px-7 py-3.5 text-sm font-semibold text-white shadow-lg shadow-blue-600/20 transition duration-300 hover:-translate-y-1 hover:bg-blue-500 disabled:cursor-not-allowed disabled:opacity-60 disabled:hover:translate-y-0"
              >
                {{ isSending ? 'Mengirim...' : 'Kirim Pesan' }}

                <span
                  v-if="!isSending"
                  class="transition duration-300 group-hover:translate-x-1"
                >
                  →
                </span>

                <svg
                  v-else
                  class="h-4 w-4 animate-spin"
                  viewBox="0 0 24 24"
                  fill="none"
                >
                  <circle
                    cx="12"
                    cy="12"
                    r="9"
                    stroke="currentColor"
                    stroke-width="3"
                    class="opacity-25"
                  />
                  <path
                    d="M21 12a9 9 0 0 0-9-9"
                    stroke="currentColor"
                    stroke-width="3"
                    stroke-linecap="round"
                  />
                </svg>
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* LAYOUT */
.contact-layout {
  display: grid;
  grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.85fr);
  align-items: center;
  column-gap: 40px;
  width: 100%;
}

.contact-info {
  width: 100%;
  min-width: 0;
}

.contact-form {
  width: 100%;
  min-width: 0;
  max-width: 100%;
  justify-self: stretch;
  box-sizing: border-box;
}

/* CONTACT ROW */
.contact-row {
  display: flex;
  align-items: center;
  width: 100%;
  max-width: 100%;
  min-width: 0;
  gap: 13px;
  text-decoration: none;
  transition: transform 0.3s ease;
}

.contact-row:hover {
  transform: translateX(4px);
}

/* ICON */
.contact-icon {
  display: flex;
  height: 40px;
  width: 40px;
  flex-shrink: 0;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  background: rgba(59, 130, 246, 0.1);
  color: #60a5fa;
  transition:
    background 0.3s ease,
    box-shadow 0.3s ease;
}

.contact-icon svg {
  height: 19px;
  width: 19px;
}

.contact-row:hover .contact-icon {
  background: rgba(59, 130, 246, 0.18);
  box-shadow: 0 0 18px rgba(59, 130, 246, 0.12);
}

/* CONTACT TEXT */
.contact-label {
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: #60a5fa;
}

.contact-value {
  margin-top: 4px;
  font-size: 15px;
  line-height: 1.6;
  color: #cbd5e1;
  overflow-wrap: anywhere;
  transition: color 0.3s ease;
}

.contact-row:hover .contact-value {
  color: white;
}

/* ARROW */
.contact-arrow {
  margin-left: auto;
  margin-right: 60px;
  flex-shrink: 0;
  color: #3b82f6;
  font-size: 17px;
  opacity: 0.7;
  transition:
    transform 0.3s ease,
    opacity 0.3s ease;
}

.contact-row:hover .contact-arrow {
  transform: translateX(4px);
  opacity: 1;
}

/* FORM FIELD */
.form-box {
  width: 100%;
  min-width: 0;
  box-sizing: border-box;
  border: 1px solid rgba(96, 165, 250, 0.25);
  border-radius: 11px;
  background: rgba(7, 17, 31, 0.45);
  padding: 13px 14px;
  transition:
    border-color 0.3s ease,
    background 0.3s ease,
    box-shadow 0.3s ease;
}

.form-box:focus-within {
  border-color: rgba(59, 130, 246, 0.7);
  background: rgba(7, 17, 31, 0.75);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.07);
}

.form-box label {
  display: block;
  font-size: 11px;
  font-weight: 600;
  color: #e2e8f0;
}

/* INPUT & TEXTAREA */
.form-box input,
.form-box textarea {
  display: block;
  width: 100%;
  min-width: 0;
  box-sizing: border-box;
  margin-top: 7px;
  padding: 2px 0;
  border: none;
  border-radius: 0;
  outline: none;
  background-color: transparent !important;
  font-family: inherit;
  font-size: 13px;
  line-height: 1.7;
  color: #cbd5e1;
  -webkit-appearance: none;
  appearance: none;
}

.form-box input {
  height: 27px;
}

.form-box textarea {
  min-height: 130px;
  resize: vertical;
}

.form-box input::placeholder,
.form-box textarea::placeholder {
  color: #64748b;
  opacity: 1;
}

/* FIX CHROME AUTOFILL */
.form-box input:-webkit-autofill,
.form-box input:-webkit-autofill:hover,
.form-box input:-webkit-autofill:focus,
.form-box textarea:-webkit-autofill,
.form-box textarea:-webkit-autofill:hover,
.form-box textarea:-webkit-autofill:focus {
  -webkit-text-fill-color: #cbd5e1;
  caret-color: #cbd5e1;
  -webkit-box-shadow: 0 0 0 1000px #091629 inset;
  box-shadow: 0 0 0 1000px #091629 inset;
  border-radius: 0;
  transition: background-color 9999s ease-out;
}

.form-box input:disabled,
.form-box textarea:disabled {
  cursor: not-allowed;
  opacity: 0.6;
}

/* BACKGROUND ANIMATION */
.animate-glow {
  animation: glowMove 8s ease-in-out infinite alternate;
}

.animate-glow-two {
  animation: glowMoveTwo 6s ease-in-out infinite alternate;
}

.animate-orbit {
  animation: orbitMove 18s linear infinite;
}

.animate-orbit-reverse {
  animation: orbitReverse 14s linear infinite;
}

.animate-core {
  animation: coreMove 6s ease-in-out infinite;
}

.animate-dot {
  animation: dotMove 5s ease-in-out infinite;
}

.animate-dot-two {
  animation: dotMoveTwo 6s ease-in-out infinite;
}

.animate-dot-three {
  animation: dotMoveThree 7s ease-in-out infinite;
}

.animate-star {
  animation: starMove 4s ease-in-out infinite;
}

.animate-star-two {
  animation: starMoveTwo 5s ease-in-out infinite;
}

/* KEYFRAMES */
@keyframes glowMove {
  0% { transform: translate(0, 0) scale(0.85); }
  50% { transform: translate(45px, -25px) scale(1.08); }
  100% { transform: translate(-30px, 30px) scale(0.95); }
}

@keyframes glowMoveTwo {
  0% { transform: translate(0, 0) scale(0.8); }
  50% { transform: translate(-30px, 25px) scale(1.15); }
  100% { transform: translate(25px, -30px) scale(0.9); }
}

@keyframes orbitMove {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes orbitReverse {
  from { transform: rotate(360deg); }
  to { transform: rotate(0deg); }
}

@keyframes coreMove {
  0%, 100% {
    transform: scale(0.85);
    opacity: 0.5;
  }
  50% {
    transform: scale(1.15);
    opacity: 0.9;
  }
}

@keyframes dotMove {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(28px, -20px); }
}

@keyframes dotMoveTwo {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(-20px, 25px); }
}

@keyframes dotMoveThree {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(18px, 20px); }
}

@keyframes starMove {
  0%, 100% {
    transform: translateY(0) rotate(0deg);
    opacity: 0.45;
  }
  50% {
    transform: translateY(-12px) rotate(15deg);
    opacity: 1;
  }
}

@keyframes starMoveTwo {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}

/* RESPONSIVE */
@media (max-width: 1100px) {
  .contact-layout {
    grid-template-columns: minmax(0, 1fr) minmax(0, 0.8fr);
    column-gap: 32px;
  }

  .contact-arrow {
    margin-right: 30px;
  }
}

@media (max-width: 850px) {
  .contact-layout {
    grid-template-columns: minmax(0, 1fr);
    row-gap: 40px;
  }

  .contact-info,
  .contact-form {
    width: 100%;
    max-width: 100%;
  }

  .contact-row {
    max-width: 100%;
  }

  .contact-arrow {
    margin-right: 0;
  }
}

@media (max-width: 640px) {
  #contact {
    padding-top: 72px;
    padding-bottom: 72px;
  }

  .contact-layout {
    row-gap: 32px;
  }

  .contact-form {
    padding: 24px;
  }

  .contact-row {
    max-width: 100%;
  }
}

/* REDUCED MOTION */
@media (prefers-reduced-motion: reduce) {
  .animate-glow,
  .animate-glow-two,
  .animate-orbit,
  .animate-orbit-reverse,
  .animate-core,
  .animate-dot,
  .animate-dot-two,
  .animate-dot-three,
  .animate-star,
  .animate-star-two {
    animation: none;
  }

  .contact-row,
  .contact-icon,
  .contact-value,
  .contact-arrow,
  .form-box {
    transition: none;
  }
}
</style>
```