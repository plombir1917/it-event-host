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
    'Реальные кейсы мероприятий и отзывы организаторов: форумы, конференции, фестивали и корпоративные события.'
})
</script>

