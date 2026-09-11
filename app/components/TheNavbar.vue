<script setup lang="ts">
const icons = import.meta.glob('../asssets/Icons/*.svg', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  const key = `../asssets/Icons/${name}.svg`
  const mod = icons[key]
  return typeof mod === 'string' ? mod : ((mod as { default?: string })?.default ?? '')
}

const navItems = [
  { label: 'Beranda', href: '#beranda' },
  { label: 'Fitur', href: '#fitur' },
  { label: 'Efisiensi', href: '#efisiensi' },
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
      class="mx-auto flex max-w-[1280px] items-center justify-between gap-[24px] px-[25px] h-[64px]"
    >
      <!-- Logo -->
      <NuxtLink
        to="/"
        class="flex items-center gap-[8px] shrink-0"
      >
        <img
          :src="getIcon('graduation-cap')"
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
        <img
          :src="getIcon('arrow-right')"
          alt=""
          class="size-[16px]"
        />
      </button>
    </div>
  </header>
</template>
