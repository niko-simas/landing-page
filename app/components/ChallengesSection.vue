<script setup lang="ts">
const icons = import.meta.glob('~/asssets/Icons/*.svg', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  const key = `/asssets/Icons/${name}.svg`
  return icons[key] || ''
}

const leftChallenges = [
  {
    icon: 'file-text',
    title: 'Pencatatan Masih Manual',
    description: 'Proses pencatatan kehadiran membutuhkan waktu dan rentan terjadi kesalahan.'
  },
  {
    icon: 'file-check',
    title: 'Data Sulit Dipantau',
    description: 'Informasi kehadiran siswa, guru, dan aktivitas sekolah tidak selalu tersedia dalam satu tampilan.'
  }
]

const rightChallenges = [
  {
    icon: 'calendar',
    title: 'Informasi Terlambat',
    description: 'Orang tua tidak selalu mendapatkan informasi kehadiran anak secara cepat.'
  },
  {
    icon: 'layout-header-cursor',
    title: 'Rekap Membutuhkan Waktu',
    description: 'Data kehadiran perlu diperiksa dan direkap kembali untuk mendapatkan gambaran kondisi siswa.'
  }
]
</script>

<template>
  <section class="relative h-screen min-h-[720px] w-full overflow-hidden bg-white">
    <!-- Main Content -->
    <div class="relative z-10 flex h-full w-full items-center">
      <div class="mx-auto flex h-full w-full max-w-[1280px] flex-col items-center justify-center gap-[48px] px-[40px]">
        <!-- Heading -->
        <div class="flex flex-col items-center gap-[12px]">
          <!-- Badge -->
          <div class="flex items-center justify-center rounded-full bg-[#f3f7f8] px-[14px] py-[4px]">
            <span class="text-center text-[12px] font-semibold leading-[16px] text-[#008763]">TANTANGAN SEKOLAH</span>
          </div>

          <!-- Title -->
          <h2 class="w-full text-center text-[40px] font-bold leading-[48px] text-[#0d1c2e]">
            <span class="block">Pengelolaan Absensi Manual</span>
            <span class="block">Memperlambat Pemantauan Siswa</span>
          </h2>

          <!-- Description -->
          <p class="w-full max-w-[656px] text-center text-[16px] font-normal leading-[24px] text-[#54615e]">
            Proses pencatatan yang masih manual membuat guru membutuhkan lebih banyak waktu untuk mencatat, memeriksa, dan merekap kehadiran siswa.
          </p>
        </div>

        <!-- Challenge Cards -->
        <div class="flex h-[330px] w-full items-start justify-center gap-[32px]">
          <!-- Left Card -->
          <div class="flex h-[330px] w-[460px] flex-col items-center justify-between rounded-[16px] border border-[rgba(4,151,135,0.26)] border-solid bg-white p-[25px]">
            <div class="flex w-full flex-col gap-[24px]">
              <div
                v-for="(challenge, index) in leftChallenges"
                :key="index"
                class="flex h-[120px] w-full flex-col justify-center gap-[4px] rounded-[12px] bg-[#f3f7f8] p-[14px]"
              >
                <div class="flex items-center gap-[6px]">
                  <img :src="getIcon(challenge.icon)" :alt="challenge.title" class="size-[16px]" />
                  <span class="text-[16px] font-semibold leading-[24px] text-[#08201d] whitespace-nowrap">{{ challenge.title }}</span>
                </div>
                <p class="text-[14px] font-normal leading-[20px] text-[#4f625f]">{{ challenge.description }}</p>
              </div>
            </div>
          </div>

          <!-- Right Card -->
          <div class="flex h-[330px] w-[460px] flex-col items-start justify-between rounded-[16px] border border-[rgba(4,151,135,0.26)] border-solid bg-white p-[25px]">
            <div class="flex w-full flex-col gap-[24px]">
              <div
                v-for="(challenge, index) in rightChallenges"
                :key="index"
                class="flex h-[120px] w-full flex-col justify-center gap-[4px] rounded-[12px] bg-[#f3f7f8] p-[14px]"
              >
                <div class="flex items-center gap-[6px]">
                  <img :src="getIcon(challenge.icon)" :alt="challenge.title" class="size-[16px]" />
                  <span class="text-[16px] font-semibold leading-[24px] text-[#08201d] whitespace-nowrap">{{ challenge.title }}</span>
                </div>
                <p class="text-[12px] font-normal leading-[16px] text-[#4f625f]">{{ challenge.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
