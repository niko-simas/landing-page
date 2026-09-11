<script setup lang="ts">
const icons = import.meta.glob('../asssets/Icons/*.svg', { eager: true, as: 'url' })

const getIcon = (name: string) => {
  const iconMap: Record<string, string> = {
    'chevron-down': 'xmark'
  }
  const mappedName = iconMap[name] || name
  const key = `../asssets/Icons/${mappedName}.svg`
  return icons[key] || ''
}

const faqs = [
  {
    question: 'Apa itu SIMAS?',
    answer: 'SIMAS adalah sistem manajemen sekolah yang membantu sekolah mengelola dan memantau kehadiran serta aktivitas siswa secara lebih terstruktur.'
  },
  {
    question: 'Siapa saja yang dapat menggunakan SIMAS?',
    answer: 'SIMAS dapat digunakan oleh Administrator, Guru, Guru Piket, dan Orang Tua sesuai dengan akses masing-masing.'
  },
  {
    question: 'Apakah siswa memiliki akun SIMAS?',
    answer: 'Siswa tidak perlu memiliki akun. Kehadiran siswa dicatat menggunakan QR yang terhubung dengan data siswa.'
  },
  {
    question: 'Bagaimana cara siswa melakukan absensi?',
    answer: 'Siswa menggunakan QR pada kartu identitas untuk dipindai oleh Guru Piket saat datang dan pulang sekolah.'
  },
  {
    question: 'Apakah guru dapat melakukan presensi?',
    answer: 'Ya. Guru dapat melakukan presensi siswa berdasarkan jadwal dan mata pelajaran yang diajarkan.'
  },
  {
    question: 'Apakah orang tua dapat melihat kehadiran anak?',
    answer: 'Ya. Orang tua dapat melihat informasi kehadiran dan aktivitas anak melalui aplikasi.'
  }
]

const openIndices = ref<Set<number>>(new Set([0]))

const isOpen = (index: number) => openIndices.value.has(index)

const toggle = (index: number) => {
  if (openIndices.value.has(index)) {
    openIndices.value.delete(index)
  } else {
    openIndices.value.add(index)
  }
}
</script>

<template>
  <section class="flex min-h-screen w-full items-center justify-center bg-[#f8fafc] px-[65px] py-[49px]">
    <div class="flex w-full max-w-[1022px] flex-col items-center gap-[24px]">
      <!-- Header -->
      <div class="flex flex-col items-center gap-[12px]">
        <!-- Badge -->
        <div class="rounded-full bg-white px-[14px] py-[4px]">
          <span class="text-[12px] font-semibold leading-[16px] text-primary">PERTANYAAN YANG SERING DIAJUKAN</span>
        </div>

        <!-- Title -->
        <h2 class="text-center text-[36px] font-bold leading-[40px] text-[#08201d]">
          Apa itu SIMAS?
        </h2>

        <!-- Subtitle -->
        <p class="max-w-[576px] text-center text-[16px] leading-[24px] text-[#4f625f]">
          SIMAS adalah sistem manajemen sekolah yang membantu sekolah mengelola dan memantau kehadiran serta aktivitas siswa secara lebih terstruktur.
        </p>
      </div>

      <!-- Accordion Container -->
      <div class="flex w-full flex-col rounded-[24px] border border-[#d4d4d8] bg-white px-[24px]">
        <div
          v-for="(faq, index) in faqs"
          :key="faq.question"
          class="relative flex flex-col gap-[8px] py-[16px]"
        >
          <!-- Question Row -->
          <button
            class="flex w-full cursor-pointer items-center gap-[12px] pr-[24px] text-left"
            @click="toggle(index)"
          >
            <span class="flex-1 text-[14px] font-semibold leading-[20px] text-[#18181b]">
              {{ faq.question }}
            </span>

            <!-- Icon: plus when closed, xmark (rotated) when open -->
            <img
              v-if="!isOpen(index)"
              :src="getIcon('plus')"
              alt=""
              class="size-[16px] shrink-0"
            />
            <img
              v-else
              :src="getIcon('chevron-down')"
              alt=""
              class="size-[16px] shrink-0 rotate-180"
            />
          </button>

          <!-- Answer Row -->
          <div
            v-if="isOpen(index)"
            class="flex gap-[12px] pr-[24px] text-left"
          >
            <span class="flex-1 text-[14px] leading-[20px] text-[#71717a]">
              {{ faq.answer }}
            </span>
          </div>

          <!-- Divider -->
          <div
            v-if="index < faqs.length - 1"
            class="absolute bottom-0 left-0 right-0 h-px"
          >
            <div class="mx-[16px] border-t border-[#d4d4d8]" />
          </div>
        </div>
      </div>

      <!-- View All Link -->
      <div class="w-full max-w-[1022px]">
        <button class="flex items-center gap-[12px] text-left">
          <span class="text-[14px] font-medium leading-[24px] text-primary">
            Lihat Semua Pertanyaan →
          </span>
        </button>
      </div>
    </div>
  </section>
</template>
