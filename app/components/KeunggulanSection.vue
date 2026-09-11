<script setup lang="ts">
const icons = import.meta.glob('../asssets/Icons/*.svg', { eager: true, as: 'url' })
const illustrations = import.meta.glob('../asssets/illustrations/*', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  const iconMap: Record<string, string> = {
    'bell-ring-1': 'bell-ring',
    'bell-ring-2': 'bell-ring'
  }
  const mappedName = iconMap[name] || name
  const key = `../asssets/Icons/${mappedName}.svg`
  const mod = icons[key]
  return typeof mod === 'string' ? mod : ((mod as { default?: string })?.default ?? '')
}

const getIllustration = (name: string) => {
  const key = `../asssets/illustrations/${name}`
  const mod = illustrations[key]
  return typeof mod === 'string' ? mod : ((mod as { default?: string })?.default ?? '')
}

const benefits = [
  'Rekap kehadiran lebih jelas dengan data hadir, sakit, izin, dan alpa dalam satu tampilan',
  'Orang tua mendapatkan informasi saat anak tiba dan melakukan presensi di sekolah',
  'Terhubung dengan Guru, dan Orang Tua mendapatkan akses sesuai kebutuhan masing-masing.'
]
</script>

<template>
  <section class="flex w-full items-center justify-center bg-white px-[40px] py-[50px]">
    <div class="flex h-[741px] w-full max-w-[1280px] flex-wrap items-start justify-center gap-[64px]">
      <!-- Left Column: Floating Notification Card -->
      <div class="relative h-[679px] w-[568px] shrink-0 rounded-[24px]" style="background: linear-gradient(50.087deg, rgba(213, 227, 223, 0.3) 0%, rgba(239, 244, 255, 0.6) 50%, rgba(213, 227, 223, 0.2) 100%);">
        <!-- Floating Notification Card -->
        <div class="absolute left-[56px] top-[264px] right-[40px] rounded-[16px] bg-white p-[20px] shadow-[0px_16px_18px_rgba(0,135,99,0.18)]">
          <div class="flex items-start gap-[14px]">
            <!-- Icon -->
            <div class="flex size-[40px] shrink-0 items-center justify-center rounded-[12px] bg-[#049787] shadow-[0px_1px_1px_rgba(0,0,0,0.05)]">
              <img
                :src="getIcon('bell-ring-2')"
                alt="SIMAS"
                class="h-[17px] w-[17px]"
                style="filter: brightness(0) invert(1);"
              />
            </div>
            <!-- Text Content -->
            <div class="flex flex-[1_0_0] flex-col gap-[1px]">
              <div class="flex items-center justify-between">
                <span class="text-[12px] font-bold uppercase tracking-[0.6px] text-[#049787]">SIMAS</span>
                <span class="text-[12px] text-[#4f625f]">Baru Saja</span>
              </div>
              <p class="pt-[3px] text-[14px] font-semibold leading-[20px] text-[#08201d]">Presensi Masuk: Ananda Rayhan Pratama</p>
              <p class="text-[12px] leading-[16px] text-[#4f625f]">Ananda telah tiba di gerbang sekolah pukul 06:45 WIB.</p>
            </div>
          </div>
        </div>
      </div>

      <!-- Right Column: Pitch & Benefits -->
      <div class="flex w-[568px] shrink-0 flex-col items-start justify-center">
        <!-- Badge -->
        <div class="mb-[12px] rounded-full bg-[#f3f7f8] px-[14px] py-[4px]">
          <span class="text-[12px] font-semibold leading-[16px] text-[#049787]">RINGKASAN</span>
        </div>

        <!-- Heading -->
        <h2 class="w-full text-[36px] font-bold leading-[40px] text-[#08201d]">
          Pantau Kehadiran Siswa secara <span class="text-[#049787]">Real-time</span>, Langsung di Genggaman
        </h2>

        <!-- Description -->
        <p class="mb-[32px] mt-[16px] w-full text-[16px] font-normal leading-[24px] text-[#4f625f]">
          SIMAS membantu sekolah mencatat dan memantau kehadiran siswa, sekaligus memberikan informasi terbaru kepada orang tua secara lebih cepat dan terstruktur.
        </p>

        <!-- Benefits List -->
        <div class="flex w-full flex-col gap-[16px]">
          <div
            v-for="(benefit, index) in benefits"
            :key="index"
            class="flex items-start gap-[16px]"
          >
            <img
              :src="getIcon('circle-check')"
              alt="Check"
              class="size-[28px] shrink-0"
            />
            <p class="w-[524px] text-[16px] font-medium leading-[24px] text-[#08201d]">{{ benefit }}</p>
          </div>
        </div>

        <!-- Overlay Box -->
        <div class="mt-[40px] flex w-full items-center justify-between rounded-[16px] bg-[rgba(213,227,223,0.5)] p-[24px]">
          <div class="flex max-w-[448px] flex-col gap-[4px]">
            <div class="flex items-center gap-[4px]">
              <img
                :src="getIcon('megaphone')"
                alt="School"
                class="h-[11px] w-[13px]"
              />
              <span class="text-[12px] font-bold leading-[16px] text-[#049787]">UNTUK SEKOLAH</span>
            </div>
            <h3 class="w-full text-[20px] font-bold leading-[28px] text-[#08201d]">
              Kelola Kehadiran Lebih Mudah, Pantau Siswa Lebih Cepat
            </h3>
            <p class="w-[485px] text-[14px] font-normal leading-[20px] text-[#4f625f]">
              SIMAS membantu sekolah mencatat, memantau, dan merekap kehadiran siswa dalam satu sistem yang terintegrasi.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
