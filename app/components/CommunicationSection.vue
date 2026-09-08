<script setup lang="ts">
const getIconUrl = (name: string) => new URL(`~/asssets/Icons/${name}.svg`, import.meta.url).href

const benefits = [
  'Notifikasi kehadiran anak saat tiba di sekolah',
  'Pesan aman, hanya terlihat oleh orang tua yang bersangkutan',
  'Laporan perkembangan anak dikirim secara berkala'
]
</script>

<template>
  <section class="border-b border-gray-100 bg-white px-[32px] py-[64px]">
    <div class="mx-auto flex max-w-[1200px] items-center justify-center gap-[64px]">
      <!-- Left: Notification Card -->
      <div class="flex w-[500px] shrink-0 items-center justify-center">
        <div class="relative w-full max-w-[420px] rounded-[16px] border border-[#e5fff9] bg-white/80 p-[24px] shadow-[0px_8px_24px_rgba(8,32,29,0.08)] backdrop-blur-[8px]">
          <!-- Notification Item -->
          <div class="flex items-center gap-[16px] rounded-[12px] border border-[rgba(4,151,135,0.15)] bg-white p-[16px] shadow-[0px_2px_8px_rgba(8,32,29,0.04)]">
            <div class="relative flex size-[48px] shrink-0 items-center justify-center rounded-full bg-[rgba(4,151,135,0.1)]">
              <img
                :src="getIconUrl('bell-ring-2')"
                alt="Bell"
                class="size-[20px]"
              />
            </div>
            <div class="flex flex-col gap-[2px]">
              <span class="text-[14px] font-bold leading-[20px] text-[#08201d]">Notifikasi Kedatangan</span>
              <span class="text-[14px] font-normal leading-[20px] text-[#4f625f]">Ananda telah tiba di sekolah</span>
              <span class="text-[14px] font-normal leading-[20px] text-[#049787]">07:15 WIB</span>
            </div>
          </div>
          <!-- Caption -->
          <p class="mt-[16px] text-center text-[12px] italic leading-[16px] text-[#ff383c]">Muncul otomatis di layar smartphone Anda</p>
        </div>
      </div>

      <!-- Right: Content -->
      <div class="flex max-w-[580px] flex-col items-start gap-[24px]">
        <h2 class="text-[30px] font-bold leading-[36px] text-[#08201d]">Tetap Terhubung dengan Aktivitas Anak</h2>
        <p class="text-[18px] font-medium leading-[28px] text-[#4f625f]">Dapatkan kabar terbaru lewat notifikasi langsung yang muncul di smartphone Anda.</p>

        <!-- Benefits List -->
        <div class="mt-[8px] flex flex-col items-start gap-[16px]">
          <div v-for="benefit in benefits" :key="benefit" class="flex items-center gap-[12px]">
            <img
              :src="getIconUrl('circle-check')"
              alt="Check"
              class="size-[24px]"
            />
            <span class="text-[16px] font-medium leading-[24px] text-[#4f625f]">{{ benefit }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
