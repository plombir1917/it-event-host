<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-sm border-b border-primary-200 transition-all duration-300"
    :class="{ 'shadow-lg': isScrolled }"
  >
    <nav class="container mx-auto px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        <!-- Логотип / Название -->
        <a
          href="#"
          class="text-2xl font-black text-primary-900 hover:text-primary-700 transition-colors"
          @click.prevent="scrollToTop"
        >
          Захар Копич
        </a>

        <!-- Навигационные ссылки (Desktop) -->
        <div class="hidden md:flex items-center gap-8">
          <a
            href="#about"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors"
            @click.prevent="scrollTo('#about')"
          >
            Обо мне
          </a>
          <a
            href="#services"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors"
            @click.prevent="scrollTo('#services')"
          >
            Форматы
          </a>
          <a
            href="#cases"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors"
            @click.prevent="scrollTo('#cases')"
          >
            Кейсы
          </a>
          <a
            href="#contact"
            class="px-6 py-2 bg-primary-900 text-white font-semibold hover:bg-primary-800 transition-colors"
            @click.prevent="scrollTo('#contact')"
          >
            Связаться
          </a>
        </div>

        <!-- Мобильное меню кнопка -->
        <button
          class="md:hidden w-10 h-10 flex flex-col justify-center items-center gap-1.5 text-primary-900"
          @click="toggleMobileMenu"
          aria-label="Toggle menu"
        >
          <span
            class="block w-6 h-0.5 bg-current transition-all duration-300"
            :class="mobileMenuOpen ? 'rotate-45 translate-y-2' : ''"
          ></span>
          <span
            class="block w-6 h-0.5 bg-current transition-all duration-300"
            :class="mobileMenuOpen ? 'opacity-0' : ''"
          ></span>
          <span
            class="block w-6 h-0.5 bg-current transition-all duration-300"
            :class="mobileMenuOpen ? '-rotate-45 -translate-y-2' : ''"
          ></span>
        </button>
      </div>

      <!-- Мобильное меню -->
      <div
        v-if="mobileMenuOpen"
        class="md:hidden pb-6 pt-4 border-t border-primary-200 animate-fade-in"
      >
        <div class="flex flex-col gap-4">
          <a
            href="#about"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors py-2"
            @click.prevent="scrollTo('#about')"
          >
            О ведущем
          </a>
          <a
            href="#services"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors py-2"
            @click.prevent="scrollTo('#services')"
          >
            Форматы
          </a>
          <a
            href="#cases"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors py-2"
            @click.prevent="scrollTo('#cases')"
          >
            Кейсы
          </a>
          <a
            href="#contact"
            class="px-6 py-2 bg-primary-900 text-white font-semibold hover:bg-primary-800 transition-colors text-center"
            @click.prevent="scrollTo('#contact')"
          >
            Связаться
          </a>
        </div>
      </div>
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20
}

const scrollTo = (selector: string) => {
  const element = document.querySelector(selector)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' })
    mobileMenuOpen.value = false
  }
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
  mobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.3s ease-out;
}
</style>
