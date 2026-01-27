<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 text-white border-b border-white/10"
    :class="[
      { 'shadow-lg': isScrolled },
      isReady && 'transition-colors duration-300'
    ]"
    :style="headerBackgroundStyle"
  >
    <nav class="container mx-auto px-6 lg:px-14">
      <div class="flex items-center justify-between h-20">
        <!-- Логотип -->
        <NuxtLink
          to="/"
          class="text-2xl font-black text-white hover:text-white/80 transition-colors"
          @click.prevent="handleLogoClick"
        >
          Захар Копич
        </NuxtLink>

        <!-- Desktop nav -->
        <div class="hidden md:flex items-center gap-8">
          <NuxtLink to="/" class="font-medium" :class="linkClass('/')">
            Главная
          </NuxtLink>
          <NuxtLink to="/about" class="font-medium" :class="linkClass('/about')">
            Обо мне
          </NuxtLink>
          <NuxtLink to="/cases" class="font-medium" :class="linkClass('/cases')">
            Кейсы
          </NuxtLink>
          <a
            href="#"
            class="px-6 py-2 bg-white text-black font-semibold hover:bg-primary-100 transition-colors"
            @click.prevent="handleContactClick"
          >
            Связаться
          </a>
        </div>

        <!-- Mobile burger -->
        <button
          class="md:hidden w-10 h-10 flex flex-col justify-center items-center gap-1.5 text-white"
          @click="toggleMobileMenu"
          aria-label="Toggle menu"
        >
          <span class="block w-6 h-0.5 bg-current transition-all"
            :class="mobileMenuOpen ? 'rotate-45 translate-y-2' : ''" />
          <span class="block w-6 h-0.5 bg-current transition-all"
            :class="mobileMenuOpen ? 'opacity-0' : ''" />
          <span class="block w-6 h-0.5 bg-current transition-all"
            :class="mobileMenuOpen ? '-rotate-45 -translate-y-2' : ''" />
        </button>
      </div>

      <!-- Mobile menu -->
      <div
        v-if="mobileMenuOpen"
        class="md:hidden pb-6 pt-4 border-t border-white/10 bg-black animate-fade-in"
      >
        <div class="flex flex-col gap-5">
          <NuxtLink to="/" class="text-white/80 hover:text-white"
            @click="closeMobileMenuAndGoHome">
            Главная
          </NuxtLink>
          <NuxtLink to="/about" class="text-white/80 hover:text-white"
            @click="closeMobileMenu">
            Обо мне
          </NuxtLink>
          <NuxtLink to="/cases" class="text-white/80 hover:text-white"
            @click="closeMobileMenu">
            Кейсы
          </NuxtLink>
          <a
            href="#"
            class="mt-2 px-6 py-3 bg-white text-black font-semibold text-center"
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
import { ref, computed, onMounted, onUnmounted, watch } from 'vue'

const route = useRoute()

const isHome = computed(() => route.path === '/')
const isScrolled = ref(false)
const mobileMenuOpen = ref(false)
const isMobile = ref(false)
const isReady = ref(false)

// 👇 КЛЮЧЕВОЕ: стартовое состояние для desktop
const headerFill = ref(isHome.value ? 0.5 : 1)

let heroScrollEnd = 1

const updateIsMobile = () => {
  isMobile.value = window.innerWidth < 1024
}

const computeHeroScrollEnd = () => {
  if (!isHome.value) return
  const about = document.querySelector('#about') as HTMLElement | null
  heroScrollEnd = about
    ? about.getBoundingClientRect().top + window.scrollY - 80
    : window.innerHeight
}

const handleScroll = () => {
  const y = window.scrollY
  isScrolled.value = y > 20

  if (isMobile.value || !isHome.value) {
    headerFill.value = 1
    return
  }

  const progress = Math.min(1, y / heroScrollEnd)
  headerFill.value = 0.5 + progress * 0.5
}

onMounted(() => {
  updateIsMobile()
  computeHeroScrollEnd()
  handleScroll()

  isReady.value = true

  window.addEventListener('resize', () => {
    updateIsMobile()
    computeHeroScrollEnd()
    handleScroll()
  })

  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

watch(() => route.path, handleScroll)

const headerBackgroundStyle = computed(() => {
  if (isMobile.value || !isHome.value) {
    return { backgroundColor: '#000' }
  }

  const percent = headerFill.value * 100
  return {
    backgroundImage: `linear-gradient(
      to right,
      #000 0%,
      #000 ${percent}%,
      rgba(0,0,0,0) ${percent}%,
      rgba(0,0,0,0) 100%
    )`
  }
})

const toggleMobileMenu = () => (mobileMenuOpen.value = !mobileMenuOpen.value)
const closeMobileMenu = () => (mobileMenuOpen.value = false)
const closeMobileMenuAndGoHome = closeMobileMenu

const linkClass = (path: string) =>
  route.path === path ? 'text-white' : 'text-white/70 hover:text-white'

const handleLogoClick = async () => {
  if (route.path !== '/') await navigateTo('/')
  window.scrollTo({ top: 0, behavior: 'smooth' })
  closeMobileMenu()
}

const handleContactClick = async () => {
  if (route.path !== '/') {
    await navigateTo('/#contact')
  } else {
    document.querySelector('#contact')?.scrollIntoView({ behavior: 'smooth' })
  }
  closeMobileMenu()
}
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.3s ease-out;
}
</style>
