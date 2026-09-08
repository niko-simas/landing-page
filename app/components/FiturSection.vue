<script setup lang="ts">
const getIconUrl = (name: string) => new URL(`~/asssets/Icons/${name}.svg`, import.meta.url).href

const features = [
  {
    icon: 'baseline-cast-for-education',
    title: 'Presensi Kedatangan',
    description: 'Pindai cepat di gerbang sekolah untuk mencatat jam tiba siswa dalam waktu singkat.'
  },
  {
    icon: 'list-check',
    title: 'Presensi Kelas',
    description: 'Memudahkan guru mencatat status kehadiran siswa secara langsung dari smartphone di kelas.'
  },
  {
    icon: 'bell-ring-1',
    title: 'Notifikasi Orang Tua',
    description: 'Status kehadiran siswa terkirim otomatis ke smartphone orang tua, saat di gerbang maupun saat di kelas.'
  }
]
</script>

<template>
  <section class="border-b border-gray-100 bg-[#f8fafc] px-[32px] py-[64px]">
    <div class="mx-auto max-w-[1280px]">
      <!-- Heading -->
      <div class="mb-[48px] flex flex-col items-center gap-[16px]">
        <h2 class="text-[30px] font-bold leading-[36px] text-[#08201d]">Fitur Aktivitas Akademik</h2>
        <p class="text-center text-[18px] font-medium leading-[28px] text-[#4f625f] whitespace-nowrap">Satu sistem untuk semua catatan kehadiran dan aktivitas siswa.</p>
      </div>

      <!-- Cards -->
      <div class="flex items-stretch justify-center gap-[32px]">
        <div v-for="feature in features" :key="feature.title" class="flex min-w-0 flex-[1] flex-col items-start gap-[8px] rounded-[12px] border border-[rgba(188,201,197,0.3)] bg-[#e5fff9] p-[32px]">
          <img
            :src="getIconUrl(feature.icon)"
            :alt="feature.title"
            class="mb-[8px] size-[30px]"
          />
          <h3 class="text-[20px] font-semibold leading-[28px] text-[#08201d]">{{ feature.title }}</h3>
          <p class="text-[16px] font-medium leading-[24px] text-[#4f625f]">{{ feature.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>
