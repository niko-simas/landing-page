<script setup lang="ts">
const navItems = [
  { label: 'Cara Kerja', href: '#cara-kerja' },
  { label: 'Fitur', href: '#fitur' },
  { label: 'Kontak', href: '#kontak' },
]
</script>

<template>
  <header class="w-full border-b border-gray-100 bg-white">
    <div class="mx-auto flex max-w-[1230px] items-center justify-between px-[32px] py-[16px]">
      <!-- Logo -->
      <NuxtLink to="/" class="relative flex items-center gap-[8px] shrink-0 w-[30px] h-[30px]">
        <img
          src="/asssets/Icons/graduation-cap.svg"
          alt="SIMAS Logo"
          class="size-[30px]"
        />
        <span class="text-[30px] font-bold leading-[36px] text-[#049787]">SIMAS</span>
      </NuxtLink>

      <!-- Desktop Menu -->
      <div class="flex items-center gap-[32px] shrink-0">
        <NuxtLink
          v-for="item in navItems"
          :key="item.href"
          :to="item.href"
          class="flex flex-col items-start pb-[2px] text-[16px] font-semibold leading-[24px] text-[#4F625F] transition-colors hover:text-[#049787]"
        >
          {{ item.label }}
        </NuxtLink>
      </div>

      <!-- CTA Button -->
      <button
        class="flex h-[40px] shrink-0 items-center justify-center gap-[8px] rounded-[12px] bg-[#049787] px-[12px] py-[6px] text-[14px] font-semibold leading-[20px] text-white transition-colors hover:bg-[#03786C]"
      >
        Mulai Sekarang
      </button>
    </div>
  </header>
</template>
