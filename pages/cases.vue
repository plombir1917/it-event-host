<template>
  <div class="page-safe-top">
    <CasesSection />
    <ServicesSection/>
    <TestimonialsSection />
  </div>
</template>

<script setup lang="ts">
import ServicesSection from '~/components/ServicesSection.vue';

useSeoMeta({
  title: 'Кейсы и отзывы | Захар Копич',
  description:
    'Реальные кейсы IT-мероприятий и отзывы организаторов: форумы, хакатоны, фестивали и митапы.'
})
</script>

