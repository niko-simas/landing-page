<script setup lang="ts">
const getIconUrl = (name: string) => new URL(`~/asssets/Icons/${name}.svg`, import.meta.url).href

const steps = [
  {
    number: '1',
    icon: 'qr-code-scan',
    title: 'Siswa Scan QR',
    description: 'Siswa memindai kartu identitas saat tiba di gerbang sekolah.'
  },
  {
    number: '2',
    icon: 'smartphone',
    title: 'Verifikasi Cepat',
    description: 'Guru memantau data kehadiran secara langsung melalui smartphone.'
  },
  {
    number: '3',
    icon: 'file-check',
    title: 'Rekap Otomatis',
    description: 'Waktu kehadiran dicatat real-time di sistem.'
  },
  {
    number: '4',
    icon: 'bell-ring',
    title: 'Notifikasi Orang Tua',
    description: 'Notifikasi kehadiran langsung terkirim ke aplikasi orang tua'
  }
]
</script>

<template>
  <section class="border-b border-gray-100 bg-white px-[32px] py-[64px]">
    <div class="mx-auto max-w-[1280px]">
      <!-- Heading -->
      <div class="mb-[48px] flex flex-col items-center gap-[16px]">
        <h2 class="text-[30px] font-bold leading-[36px] text-[#08201d]">Cara Kerja SIMAS</h2>
        <p class="text-center text-[18px] font-medium leading-[28px] text-[#4f625f] whitespace-nowrap">Alur presensi yang cepat, akurat, dan langsung terhubung dengan orang tua.</p>
      </div>

      <!-- Steps -->
      <div class="relative flex items-start justify-center gap-[32px]">
        <!-- Connector Line -->
        <div class="absolute left-[15%] right-[15%] top-[48px] h-[2px] border-t border-dashed border-[rgba(4,151,135,0.3)]"></div>

        <div v-for="step in steps" :key="step.number" class="relative flex min-w-0 flex-[1] flex-col items-center">
          <!-- Card -->
          <div class="relative mb-[24px] flex h-[96px] w-[96px] items-center justify-center rounded-[12px] border border-[rgba(4,151,135,0.2)] bg-white p-px shadow-[0px_8px_8px_rgba(8,32,29,0.06)]">
            <img
              :src="getIconUrl(step.icon)"
              :alt="step.title"
              class="size-[40px]"
            />
            <!-- Step Number Badge -->
            <div class="absolute -right-[12px] -top-[12px] flex size-[32px] items-center justify-center rounded-full border-2 border-white bg-[#049787]">
              <span class="text-[12px] font-bold leading-[16px] text-white">{{ step.number }}</span>
            </div>
          </div>

          <!-- Title -->
          <h3 class="mb-[8px] text-center text-[20px] font-semibold leading-[28px] text-[#08201d]">{{ step.title }}</h3>

          <!-- Description -->
          <p class="max-w-[250px] text-center text-[16px] font-medium leading-[24px] text-[#4f625f]">
            {{ step.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
