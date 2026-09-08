<script setup lang="ts">
const getIconUrl = (name: string) => new URL(`~/asssets/Icons/${name}.svg`, import.meta.url).href

const route = useRoute()

const navItems = [
  { label: 'Beranda', href: '#beranda' },
  { label: 'Alur Kerja', href: '#alur-kerja' },
  { label: 'Fitur', href: '#fitur' },
  { label: 'Keunggulan', href: '#keunggulan' },
  { label: 'FAQ', href: '#faq' },
]

const activeSection = ref('beranda')

onMounted(() => {
  const sectionIds = navItems.map(item => item.href.replace('#', ''))

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          activeSection.value = entry.target.id
        }
      })
    },
    {
      rootMargin: '-40% 0px -55% 0px',
      threshold: 0,
    }
  )

  sectionIds.forEach((id) => {
    const el = document.getElementById(id)
    if (el) observer.observe(el)
  })

  onUnmounted(() => observer.disconnect())
})
</script>

<template>
  <header
    class="sticky top-0 z-50 w-full border border-white/80 bg-white/70 backdrop-blur-[12px] shadow-[0px_8px_32px_0px_rgba(0,107,78,0.08)]"
  >
    <div
      class="mx-auto flex max-w-[1280px] items-center justify-between px-[25px] py-[12px]"
    >
      <!-- Logo -->
      <NuxtLink
        to="/"
        class="flex items-center gap-[8px] shrink-0"
      >
        <img
          :src="getIconUrl('graduation-cap')"
          alt="SIMAS Logo"
          class="size-[30px]"
        />
        <span
          class="font-['Plus_Jakarta_Sans'] text-[30px] font-bold leading-[36px] text-[#049787]"
        >
          SIMAS
        </span>
      </NuxtLink>

      <!-- Desktop Menu -->
      <nav class="flex items-center gap-[24px] shrink-0">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="font-['Plus_Jakarta_Sans'] text-[14px] font-semibold leading-[20px] transition-colors"
          :class="
            activeSection === item.href.replace('#', '')
              ? 'text-[#049787] underline underline-offset-[6px] decoration-[2px]'
              : 'text-[#4F625F] hover:text-[#049787]'
          "
        >
          {{ item.label }}
        </a>
      </nav>

      <!-- CTA Button -->
      <button
        class="flex h-[36px] shrink-0 items-center gap-[6px] rounded-full bg-[#049787] px-[20px] py-[8px] font-['Plus_Jakarta_Sans'] text-[14px] font-semibold leading-[20px] text-white shadow-[0px_4px_8px_rgba(0,135,99,0.25)] transition-colors hover:bg-[#03786C]"
      >
        Ajukan Demo
        <!-- Arrow Right Icon -->
        <svg
          class="size-[16px]"
          viewBox="0 0 16 16"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M1.25 8C1.25 7.58579 1.58579 7.25 2 7.25L12.1893 7.25L9.46967 4.53033C9.17678 4.23744 9.17678 3.76256 9.46967 3.46967C9.76256 3.17678 10.2374 3.17678 10.5303 3.46967L14.5303 7.46967C14.8232 7.76256 14.8232 8.23744 14.5303 8.53033L10.5303 12.5303C10.2374 12.8232 9.76256 12.8232 9.46967 12.5303C9.17678 12.2374 9.17678 11.7626 9.46967 11.4697L12.1893 8.75L2 8.75C1.58579 8.75 1.25 8.41421 1.25 8Z"
            fill="white"
          />
        </svg>
      </button>
    </div>
  </header>
</template>
