<script setup lang="ts">
// Landing Page - SIMAS
useSeoMeta({
  title: 'SIMAS - Sistem Informasi Akademik Sekolah',
  description: 'Sistem Informasi Akademik Sekolah untuk mendukung kebutuhan informasi dan aktivitas akademik.',
})
</script>

<template>
  <div class="min-h-screen bg-white">
    <TheNavbar />

    <main>
      <!-- Hero Section -->
      <section id="beranda">
        <HeroSection />
      </section>

      <!-- Tantangan Section -->
      <section id="tantangan">
        <ChallengesSection />
      </section>

      <!-- Fitur Section -->
      <section id="fitur">
        <FiturSection />
      </section>

      <!-- Efisiensi Section -->
      <section id="efisiensi">
        <EfisiensiSection />
      </section>

      <!-- Keunggulan Section -->
      <section id="keunggulan">
        <KeunggulanSection />
      </section>

      <!-- Komunikasi Section -->
      <section id="komunikasi">
        <CommunicationSection />
      </section>
    </main>

    <TheFooter />
  </div>
</template>
