<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-sm border-b border-primary-200 transition-all duration-300"
    :class="{ 'shadow-lg': isScrolled }"
  >
    <nav class="container mx-auto px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        <!-- Логотип / Название -->
        <NuxtLink
          to="/"
          class="text-2xl font-black text-primary-900 hover:text-primary-700 transition-colors"
          @click.prevent="handleLogoClick"
        >
          Захар Копич
        </NuxtLink>

        <!-- Навигационные ссылки (Desktop) -->
        <div class="hidden md:flex items-center gap-8">
          <NuxtLink
            to="/"
            class="font-medium transition-colors"
            :class="linkClass('/')"
          >
            Главная
          </NuxtLink>
          <NuxtLink
            to="/about"
            class="font-medium transition-colors"
            :class="linkClass('/about')"
          >
            Обо мне
          </NuxtLink>
          <NuxtLink
            to="/cases"
            class="font-medium transition-colors"
            :class="linkClass('/cases')"
          >
            Кейсы
          </NuxtLink>
          <a
            href="#"
            class="px-6 py-2 bg-primary-900 text-white font-semibold hover:bg-primary-800 transition-colors"
            @click.prevent="handleContactClick"
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
          <NuxtLink
            to="/"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors py-2"
            @click="closeMobileMenuAndGoHome"
          >
            Главная
          </NuxtLink>
          <NuxtLink
            to="/about"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors py-2"
            @click="closeMobileMenu"
          >
            О ведущем
          </NuxtLink>
          <NuxtLink
            to="/cases"
            class="text-primary-700 hover:text-primary-900 font-medium transition-colors py-2"
            @click="closeMobileMenu"
          >
            Кейсы
          </NuxtLink>
          <a
            href="#"
            class="px-6 py-2 bg-primary-900 text-white font-semibold hover:bg-primary-800 transition-colors text-center"
            @click.prevent="handleContactClick"
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
const route = useRoute()

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)

const handleScroll = () => {
  if (!process.client) return
  isScrolled.value = window.scrollY > 20
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}

const closeMobileMenuAndGoHome = () => {
  mobileMenuOpen.value = false
}

const linkClass = (path: string) => {
  const isActive = route.path === path
  return isActive
    ? 'text-primary-900'
    : 'text-primary-700 hover:text-primary-900'
}

onMounted(() => {
  if (process.client) {
    window.addEventListener('scroll', handleScroll)
  }
})

onUnmounted(() => {
  if (process.client) {
    window.removeEventListener('scroll', handleScroll)
  }
})

const handleLogoClick = async () => {
  if (!process.client) return

  if (route.path !== '/') {
    await navigateTo('/')
  }

  window.scrollTo({ top: 0, behavior: 'smooth' })
  closeMobileMenu()
}

const handleContactClick = async () => {
  if (!process.client) return

  if (route.path !== '/') {
    await navigateTo('/#contact')
  } else {
    const el = document.querySelector('#contact')
    if (el) {
      el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
  }
  closeMobileMenu()
}
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.3s ease-out;
}
</style>
