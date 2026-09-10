<script setup lang="ts">
// Same pattern as other components
const icons = import.meta.glob('~/asssets/Icons/*.svg', { eager: true, as: 'url' })
const illustrations = import.meta.glob('~/asssets/illustrations/*', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  const key = `/asssets/Icons/${name}.svg`
  return icons[key] || ''
}

const getIllustration = (name: string) => {
  // Handle both .svg and .png extensions
  if (name.includes('.')) {
    const key = `/asssets/illustrations/${name}`
    return illustrations[key] || ''
  }
  const key = `/asssets/illustrations/${name}.svg`
  return illustrations[key] || ''
}
</script>

<template>
  <section class="relative h-screen min-h-[720px] w-full overflow-hidden">
    <!-- Background Gradient -->
    <div class="pointer-events-none absolute inset-0 z-0">
      <svg
        viewBox="0 0 1278 718"
        preserveAspectRatio="xMidYMid slice"
        class="h-full w-full"
        xmlns="http://www.w3.org/2000/svg"
      >
        <defs>
          <radialGradient
            id="heroGradient"
            gradientUnits="userSpaceOnUse"
            cx="0"
            cy="0"
            r="10"
            gradientTransform="matrix(125.65 57.85 -102.97 193.91 74.103 173.5)"
          >
            <stop stop-color="rgba(108,189,161,0.4)" offset="0" />
            <stop stop-color="rgba(162,216,193,0.7)" offset="0.29808" />
            <stop stop-color="rgba(216,243,224,1)" offset="0.59615" />
            <stop stop-color="rgba(162,216,193,0.8875)" offset="0.69712" />
            <stop stop-color="rgba(108,189,162,0.775)" offset="0.79808" />
            <stop stop-color="rgba(54,162,130,0.6625)" offset="0.89904" />
            <stop stop-color="rgba(27,149,115,0.60625)" offset="0.94952" />
            <stop stop-color="rgba(0,135,99,0.55)" offset="1" />
          </radialGradient>
        </defs>
        <rect x="0" y="0" height="100%" width="100%" fill="url(#heroGradient)" />
      </svg>
    </div>

    <!-- Main Content Container -->
    <div class="relative z-10 flex h-full w-full items-center">
      <div class="mx-auto flex h-full w-full max-w-[1440px] items-center justify-between gap-32 px-[40px]">
        <!-- Left Content: Text & CTAs -->
        <div class="flex w-full max-w-[672px] shrink-0 items-center">
          <!-- Main Card Container - Exact Figma Design -->
          <div
            class="relative w-full rounded-3xl border border-white/80 bg-white/35 p-10 backdrop-blur-[20px] shadow-[0px_24px_50px_0px_rgba(0,107,78,0.12)] before:absolute before:inset-0 before:rounded-3xl before:bg-white/35 before:backdrop-blur-[20px] before:pointer-events-none"
          >
            <!-- Inner shadow overlay -->
            <div class="pointer-events-none absolute inset-0 rounded-3xl shadow-[inset_0px_4px_16px_1px_rgba(255,255,255,0.8)]"></div>

            <!-- Content wrapper with gap -->
            <div class="relative flex flex-col gap-4">
              <!-- Badge Pill -->
              <div
                class="inline-flex w-fit items-center rounded-full border border-white/95 bg-white/70 px-[17px] py-[7px] backdrop-blur-[6px]"
              >
                <span class="whitespace-nowrap text-sm font-semibold leading-[20px] text-primary">
                  Platform Sistem Manajemen Siswa (SIMAS)
                </span>
              </div>

              <!-- Heading -->
              <div class="w-full shrink-0">
                <h1 class="text-[56px] font-extrabold leading-[68px] tracking-[-1.68px] text-[#0d1c2e]">
                  Kelola Seluruh Operasional Sekolah dalam <span class="text-primary">Sekolah Satu Platform Terpadu</span>
                </h1>
              </div>

              <!-- Description -->
              <div class="max-w-[576px] shrink-0">
                <p class="text-lg font-normal leading-7 text-[#4f625f]">
                  Membantu sekolah mengelola kehadiran, aktivitas guru, data siswa, dan pemantauan siswa dalam satu sistem yang terhubung lebih praktis, terstruktur, dan mudah dipantau.
                </p>
              </div>

              <!-- CTA Buttons -->
              <div class="flex items-center gap-3 border-t border-[rgba(226,232,240,0.6)] pt-[25px]">
                <!-- Primary CTA -->
                <button
                  class="shrink-0 rounded-full bg-primary px-8 py-3.5 text-sm font-semibold leading-[20px] tracking-[0.14px] text-white shadow-[0px_4px_8px_rgba(0,135,99,0.28)] transition-all hover:opacity-90"
                >
                  Coba Ajukan Demo
                </button>

                <!-- Secondary CTA -->
                <button
                  class="shrink-0 rounded-full border border-primary bg-white/75 px-6 py-[15px] text-sm font-semibold leading-[20px] tracking-[0.14px] text-primary backdrop-blur-[6px] transition-all hover:opacity-90"
                >
                  Hubungi Tim SIMAS
                </button>
              </div> 
           </div> 
          </div>
        </div>

        <!-- Right Content: App Image with Floating Cards -->
        <div class="relative flex h-full w-full max-w-[555px] items-center justify-center">
          <!-- App Image Container -->
          <div class="relative">
            <!-- App Image -->
            <img
              :src="getIllustration('simasmobileapp.png')"
              alt="SIMAS App"
              class="h-[650px] w-auto object-contain"
            />

            <!-- Floating Card 1: Integrasi Laporan (Bottom Left) -->
            <div
              class="absolute -left-[180px] top-[440px] z-20 w-[188px] rounded-2xl border border-white/80 bg-white/20 p-[14px] shadow-[0px_4px_16px_0px_rgba(0,107,78,0.04)] before:absolute before:inset-0 before:rounded-2xl before:bg-white/50 before:backdrop-blur-[12px] before:pointer-events-none"
            >
              <div class="relative flex flex-col gap-1">
                <div class="mb-1 flex items-center gap-1.5">
                  <img
                    :src="getIcon('file-check')"
                    alt="Integrasi Laporan"
                    class="h-4 w-4 shrink-0"
                  />
                  <span class="text-base font-extrabold text-[#0d1c2e]">Integrasi Laporan</span>
                </div>
                <p class="text-xs font-normal leading-[19.2px] text-[#4f625f]">
                  Format Standar & Siap Cetak Dapodik
                </p>
              </div>
            </div>

            <!-- Floating Card 2: Tugas SIMAS (Top Right of Phone) -->
            <div
              class="absolute left-[280px] top-[40px] z-20 w-[188px] rounded-2xl border border-white/80 bg-white/20 p-[14px] shadow-[0px_4px_16px_0px_rgba(0,107,78,0.04)] before:absolute before:inset-0 before:rounded-2xl before:bg-white/50 before:backdrop-blur-[12px] before:pointer-events-none"
            >
              <div class="relative flex flex-col gap-1">
                <div class="mb-1 flex items-center gap-1.5">
                  <img
                    :src="getIcon('pencil-to-square')"
                    alt="Tugas SIMAS"
                    class="h-4 w-4 shrink-0"
                  />
                  <span class="text-base font-extrabold text-[#0d1c2e]">Tugas SIMAS</span>
                </div>
                <p class="text-xs font-normal leading-[19.2px] text-[#4f625f]">
                  Pengelolaan & Evaluasi Terstruktur
                </p>
              </div>
            </div>

            <!-- Floating Card 3: Presensi Digital (Bottom Right of Phone) -->
            <div
              class="absolute left-[280px] top-[420px] z-20 w-[188px] rounded-2xl border border-white/80 bg-white/20 p-[14px] shadow-[0px_4px_16px_0px_rgba(0,107,78,0.04)] before:absolute before:inset-0 before:rounded-2xl before:bg-white/50 before:backdrop-blur-[12px] before:pointer-events-none"
            >
              <div class="relative flex flex-col gap-1">
                <div class="mb-1 flex items-center gap-1.5">
                  <img
                    :src="getIcon('clock-arrow-rotate-left')"
                    alt="Presensi Digital"
                    class="h-4 w-4 shrink-0"
                  />
                  <span class="text-base font-extrabold text-[#0d1c2e]">Presensi Digital</span>
                </div>
                <p class="text-xs font-normal leading-[19.2px] text-[#4f625f]">
                  Kehadiran Siswa Real-Time & Akurat
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
