<script setup lang="ts">
const icons = import.meta.glob('~/asssets/Icons/*.svg', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  const key = `/asssets/Icons/${name}.svg`
  return icons[key] || ''
}

const beforeItems = [
  'Format pengumpulan data siswa, guru, dan orang tua tidak seragam karena beda templat Excel di tiap kelas.',
  'Rekap absensi gerbang dan jam pelajaran masih terpisah, sehingga siswa terlambat atau pulang awal sulit terpantau.',
  'Tanpa verifikasi identitas resmi, rawan terjadi klaim akun anak oleh pihak yang tidak bertanggung jawab.'
]

const afterItems = [
  'Import data siswa dan orang tua secara cepat dengan templat terpusat yang rapi.',
  'Pantau kehadiran gerbang dan jam pelajaran secara real-time, lengkap dengan toleransi keterlambatan dan dispensasi.',
  'Orang tua unggah bukti izin dari HP, persetujuan cukup 1 klik, dan rekap nilai/tugas terhitung otomatis.'
]
</script>

<template>
  <section class="relative flex h-screen min-h-[720px] w-full items-center justify-center overflow-hidden bg-[#f8fafc] px-[65px] py-[49px]">
    <div class="flex w-full max-w-[1295px] flex-col items-center gap-[12px]">
      <!-- Badge -->
      <div class="rounded-full bg-white px-[14px] py-[4px]">
        <span class="text-[12px] font-semibold leading-[16px] text-[#049787]">TRANSFORMASI OPERASIONAL SEKOLAH</span>
      </div>

      <!-- Title -->
      <h2 class="max-w-[576px] text-center text-[36px] font-bold leading-[40px] text-[#08201d]">
        Bandingkan Efisiensi Sebelum & Sesudah Menggunakan SIMAS
      </h2>

      <!-- Subtitle -->
      <div class="flex flex-col items-center text-center">
        <p class="text-[16px] font-normal leading-[24px] text-[#4f625f]">Atasi kebingungan format data manual keterlambatan laporan dan,</p>
        <p class="text-[16px] font-normal leading-[24px] text-[#4f625f]">ketidakpastian wali murid.</p>
      </div>

      <!-- Comparison Cards -->
      <div class="flex w-full items-start justify-center gap-[32px] pt-[40px]">
        <!-- Before Card -->
        <div class="flex flex-[1_1_0] flex-col gap-[16px] rounded-[16px] border border-[rgba(248,113,113,0.2)] bg-white p-[33px]">
          <!-- Card Header -->
          <div>
            <h3 class="text-[20px] font-semibold leading-[28px] text-[#d64545]">Sebelum Menggunakan SIMAS</h3>
          </div>

          <!-- List Items -->
          <div class="flex flex-col gap-[16px]">
            <div
              v-for="(item, index) in beforeItems"
              :key="index"
              class="flex items-start gap-[12px]"
            >
              <img
                :src="getIcon('circle-xmark')"
                alt=""
                class="size-[24px] shrink-0"
              />
              <p class="text-[14px] font-normal leading-[20px] text-[#4f625f]">{{ item }}</p>
            </div>
          </div>
        </div>

        <!-- After Card -->
        <div class="flex flex-[1_1_0] flex-col gap-[16px] rounded-[16px] border border-[rgba(0,135,99,0.3)] bg-white p-[33px] shadow-[0px_12px_16px_rgba(0,135,99,0.08)]">
          <!-- Card Header -->
          <div>
            <h3 class="text-[20px] font-semibold leading-[28px] text-[#049787]">Sesudah Menggunakan SIMAS</h3>
          </div>

          <!-- List Items -->
          <div class="flex flex-col gap-[16px]">
            <div
              v-for="(item, index) in afterItems"
              :key="index"
              class="flex items-start gap-[12px]"
            >
              <img
                :src="getIcon('circle-check')"
                alt=""
                class="size-[24px] shrink-0"
              />
              <p class="text-[14px] font-normal leading-[20px] text-[#4f625f]">{{ item }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
