<template>
  <div class="min-h-screen flex flex-col">
    <HeaderSection />
    <main class="flex-1 page-safe-top">
      <slot />
    </main>
    <FooterSection />
  </div>
</template>

<script setup lang="ts">
// Базовый лейаут с хедером и футером
</script>

