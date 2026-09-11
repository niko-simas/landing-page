<script setup lang="ts">
// Load all icons from app/asssets/Icons
const icons = import.meta.glob('../asssets/Icons/*.svg', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  // Map icon names to actual file names
  const iconMap: Record<string, string> = {
    mail: 'envelope',
    telephone: 'smartphone',
    favourites: 'star',
    building: 'factory'
  }
  const mappedName = iconMap[name] || name
  const key = `../asssets/Icons/${mappedName}.svg`
  return icons[key] || ''
}

const navLinks = [
  { label: 'Cara Kerja', icon: 'favourites' },
  { label: 'Fitur', icon: 'telephone' }
]

const contactLinks = [
  { label: 'Tentang Kami', icon: 'building' },
  { label: 'Email', icon: 'mail' }
]
</script>

<template>
  <footer class="bg-[#f8fafc] px-[32px] py-[64px]">
    <div class="mx-auto max-w-[1280px]">
      <!-- Footer Card -->
      <div class="relative w-full overflow-hidden rounded-[24px] border border-[rgba(188,201,197,0.5)] bg-white shadow-[0px_8px_32px_rgba(8,32,29,0.06)]">
        <div class="flex flex-col items-stretch">
          <!-- Main Content -->
          <div class="flex items-start justify-center gap-[80px] px-[48px] py-[48px]">
            <!-- Logo & Description -->
            <div class="flex w-[320px] shrink-0 flex-col items-start gap-[16px]">
              <div class="flex items-center gap-[12px]">
                <img
                  :src="getIcon('graduation-cap')"
                  alt="SIMAS"
                  class="size-[36px]"
                />
                <span class="text-[28px] font-bold leading-[32px] text-[#049787]">SIMAS</span>
              </div>
              <p class="text-[14px] font-normal leading-[22px] text-[#4f625f]">Platform manajemen siswa pemantauan aktivitas anak jadi lebih mudah untuk guru maupun orang tua.</p>
            </div>

            <!-- Links -->
            <div class="flex items-start justify-center gap-[80px]">
              <!-- Navigation -->
              <div class="flex w-[140px] shrink-0 flex-col items-start gap-[12px]">
                <h4 class="pb-[4px] text-[14px] font-semibold leading-[20px] text-[#08201d]">Navigasi</h4>
                <NuxtLink v-for="link in navLinks" :key="link.label" :to="`#${link.label.toLowerCase().replace(' ', '-')}`" class="flex items-center gap-[8px]">
                  <img :src="getIcon(link.icon)" :alt="link.label" class="size-[14px]" />
                  <span class="text-[14px] font-normal leading-[20px] text-[#4f625f]">{{ link.label }}</span>
                </NuxtLink>
              </div>

              <!-- Contact -->
              <div class="flex w-[140px] shrink-0 flex-col items-start gap-[12px]">
                <h4 class="pb-[4px] text-[14px] font-semibold leading-[20px] text-[#08201d]">Kontak</h4>
                <NuxtLink v-for="link in contactLinks" :key="link.label" :to="'#'" class="flex items-center gap-[8px]">
                  <img :src="getIcon(link.icon)" :alt="link.label" class="size-[14px]" />
                  <span class="text-[14px] font-normal leading-[20px] text-[#4f625f]">{{ link.label }}</span>
                </NuxtLink>
              </div>
            </div>
          </div>

          <!-- Bottom Bar -->
          <div class="border-t border-[rgba(188,201,197,0.5)] px-[48px] py-[16px]">
            <p class="text-center text-[12px] font-normal leading-[16px] text-[#08201d]">© 2026 SIMAS - Sistem Manajemen Siswa.</p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>
