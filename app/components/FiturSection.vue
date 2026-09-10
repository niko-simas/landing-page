<script setup lang="ts">
const illustrations = import.meta.glob('~/asssets/illustrations/*', { eager: true, as: 'url' })

const getIllustration = (name: string) => {
  if (name.includes('.')) {
    const key = `/asssets/illustrations/${name}`
    return illustrations[key] || ''
  }
  const key = `/asssets/illustrations/${name}.svg`
  return illustrations[key] || ''
}

const features = [
  {
    title: 'Presensi Digital Real-Time',
    description: 'Pencatatan dan rekapitulasi kehadiran siswa serta guru secara otomatis tanpa perlu rekap manual.'
  },
  {
    title: 'Pengajuan Izin & Sakit Online',
    description: 'Orang tua dapat mengajukan izin dan sakit dengan mengunggah surat dokter dan diverifikasi oleh wali kelas.'
  },
  {
    title: 'Manajemen Tugas & Form Interaktif',
    description: 'Guru dapat membuat formulir & checklist tugas fleksibel dengan bobot nilai yang bebas diatur.'
  },
  {
    title: 'Dashboard & Analitik Sekolah',
    description: 'Pantau grafik statistik kehadiran, keaktifan kelas, dan activity log sekolah dalam satu tampilan dashboard.'
  },
  {
    title: 'Kelola Data Master',
    description: 'Kemudahan mengunggah data siswa dan guru sekaligus tanpa perlu manual satu per satu.'
  },
  {
    title: 'Pengumuman & Notifikasi Instan',
    description: 'Pengumuman resmi dari sekolah yang langsung diterima orang tua di ponsel secara real-time.'
  }
]
</script>

<template>
  <section class="flex min-h-screen w-full items-center justify-center bg-[rgba(239,244,255,0.4)] px-[48px] py-[80px]">
    <div class="flex w-full max-w-[1295px] flex-col items-center gap-[64px]">
      <!-- Header Section -->
      <div class="flex w-full max-w-[672px] flex-col items-center">
        <!-- Badge -->
        <div class="mb-[12px] rounded-full bg-[#f3f7f8] px-[14px] py-[4px]">
          <span class="text-[12px] font-semibold leading-[16px] text-primary">FITUR SIMAS</span>
        </div>

        <!-- Title -->
        <h2 class="mb-[12px] text-center text-[36px] font-bold leading-[40px] text-[#08201d]">
          Semua Fitur Kebutuhan Kehadiran Sekolah dalam Satu Sistem
        </h2>

        <!-- Subtitle -->
        <p class="text-center text-[16px] font-normal leading-[24px] text-[#4f625f]">
          SIMAS menyediakan fitur yang disesuaikan dengan kebutuhan setiap
        </p>
        <p class="text-center text-[16px] font-normal leading-[24px] text-[#4f625f]">
          peran dalam lingkungan sekolah.
        </p>
      </div>

      <!-- Features Grid -->
      <div class="grid w-full max-w-[1295px] grid-cols-3 gap-[40px] px-[80px]">
        <div
          v-for="feature in features"
          :key="feature.title"
          class="flex w-[351px] flex-col items-start gap-[16px] rounded-[16px] border border-[rgba(241,245,249,0.9)] bg-white p-[25px] shadow-[0px_4px_8px_rgba(0,135,99,0.04)]"
        >
          <!-- Image Overlay -->
          <div class="h-[144px] w-full overflow-hidden rounded-[8px]">
            <img
              :src="getIllustration('fitur-overlay.png')"
              alt=""
              class="h-full w-full object-cover"
            />
          </div>

          <!-- Content -->
          <div class="flex flex-col gap-[4px] p-[14px]">
            <h3 class="text-[16px] font-semibold leading-[24px] text-[#08201d]">
              {{ feature.title }}
            </h3>
            <p class="text-[14px] font-normal leading-[20px] text-[#4f625f]">
              {{ feature.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
