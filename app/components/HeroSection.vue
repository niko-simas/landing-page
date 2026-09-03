<script setup lang="ts">
</script>

<template>
  <section class="relative min-h-[604px] overflow-hidden bg-[#f8fafc] pb-[64px] pt-[80px] px-[60px]">
    <!-- Gradient Overlay at bottom -->
    <div class="pointer-events-none absolute inset-x-0 bottom-0 h-[120px] bg-gradient-to-b from-transparent to-white"></div>

    <div class="relative z-10 flex h-full w-full items-center justify-center gap-[80px]">
      <!-- Left Content -->
      <div class="flex w-[578px] max-w-[600px] shrink-0 flex-col gap-[32px]">
        <!-- Badge/Pill -->
        <div class="flex w-[197px] items-center gap-[8px] rounded-full border border-[rgba(4,151,135,0.2)] bg-[#D9F3EE] px-[13px] py-[7px]">
          <div class="size-[8px] shrink-0 rounded-full bg-[#049787]"></div>
          <span class="text-[12px] font-medium leading-[20px] text-[#049787] whitespace-nowrap">Platform Manajemen Siswa</span>
        </div>

        <!-- Heading -->
        <div class="flex flex-col">
          <h1 class="text-[48px] font-bold leading-[48px] text-[#08201d]">Kelola Sekolah</h1>
          <h1 class="text-[48px] font-bold leading-[48px] text-[#049787]">Lebih Mudah, Cepat, dan Terhubung</h1>
        </div>

        <!-- Description -->
        <div class="max-w-[520px]">
          <p class="text-[18px] font-medium leading-[28px] text-[#4F625F]">
            Pantau presensi dan aktivitas siswa dalam satu platform terintegrasi yang mudah digunakan oleh guru maupun orang tua.
          </p>
        </div>
      </div>

      <!-- Right Illustration -->
      <div class="shrink-0">
        <img
          src="/asssets/illustrations/student.svg"
          alt="Student Illustration"
          class="h-[450px] w-[550px] object-contain"
        />
      </div>
    </div>
  </section>
</template>
