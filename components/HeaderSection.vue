<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 text-white border-b border-white/10 transition-colors duration-300"
    :class="{ 'shadow-lg': isScrolled }"
    :style="headerBackgroundStyle"
  >
    <nav class="container mx-auto px-6 lg:px-14">
      <div class="flex items-center justify-between h-20">
        <!-- Логотип / Название -->
        <NuxtLink
          to="/"
          class="text-2xl font-black text-white hover:text-white/80 transition-colors"
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
            class="px-6 py-2 bg-white text-black font-semibold hover:bg-primary-100 transition-colors"
            @click.prevent="handleContactClick"
          >
            Связаться
          </a>
        </div>

        <!-- Мобильное меню кнопка -->
        <button
          class="md:hidden w-10 h-10 flex flex-col justify-center items-center gap-1.5 text-white"
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
        class="md:hidden pb-6 pt-4 border-t border-white/10 bg-black animate-fade-in"
      >
        <div class="flex flex-col gap-5">
          <NuxtLink
            to="/"
            class="text-white/80 hover:text-white font-medium transition-colors py-1"
            @click="closeMobileMenuAndGoHome"
          >
            Главная
          </NuxtLink>
          <NuxtLink
            to="/about"
            class="text-white/80 hover:text-white font-medium transition-colors py-1"
            @click="closeMobileMenu"
          >
            Обо мне
          </NuxtLink>
          <NuxtLink
            to="/cases"
            class="text-white/80 hover:text-white font-medium transition-colors py-1"
            @click="closeMobileMenu"
          >
            Кейсы
          </NuxtLink>
          <a
            href="#"
            class="mt-2 px-6 py-3 bg-white text-black font-semibold hover:bg-primary-100 transition-colors text-center"
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
import { ref, onMounted, onUnmounted, computed, watch } from 'vue'
const route = useRoute()

const isHome = computed(() => route.path === '/')

const isScrolled = ref(false)
const mobileMenuOpen = ref(false)
const headerFill = ref(isHome.value ? 0.5 : 1) // 0.5 = левая половина, 1 = полностью чёрный
let heroScrollEnd = 1

const computeHeroScrollEnd = () => {
  if (!process.client || !isHome.value) return
  const about = document.querySelector('#about') as HTMLElement | null
  const headerHeight =
    parseFloat(
      getComputedStyle(document.documentElement).getPropertyValue(
        '--header-height'
      )
    ) || 80
  const aboutTop = about
    ? about.getBoundingClientRect().top + window.scrollY
    : window.innerHeight

  heroScrollEnd = Math.max(aboutTop - headerHeight, 1)
}

const handleScroll = () => {
  if (!process.client) return

  const y = window.scrollY
  isScrolled.value = y > 20

  if (!isHome.value || heroScrollEnd <= 0) {
    headerFill.value = 1
    return
  }

  const raw = y / heroScrollEnd
  const progress = Math.min(1, Math.max(0, raw))
  headerFill.value = 0.5 + progress * 0.5
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
    ? 'text-white'
    : 'text-white/70 hover:text-white'
}

onMounted(() => {
  if (process.client) {
    if (isHome.value) {
      computeHeroScrollEnd()
    }
    handleScroll()
    window.addEventListener('scroll', handleScroll)
    window.addEventListener('resize', computeHeroScrollEnd)
  }
})

onUnmounted(() => {
  if (process.client) {
    window.removeEventListener('scroll', handleScroll)
    window.removeEventListener('resize', computeHeroScrollEnd)
  }
})

watch(
  () => route.path,
  () => {
    if (!process.client) return
    if (isHome.value) {
      headerFill.value = 0.5
      computeHeroScrollEnd()
      handleScroll()
    } else {
      headerFill.value = 1
    }
  }
)

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

const headerBackgroundStyle = computed(() => {
  const fill = Math.max(0, Math.min(1, headerFill.value))
  if (!isHome.value) {
    return { backgroundColor: '#000000' }
  }

  const percent = fill * 100
  return {
    backgroundImage: `linear-gradient(to right, #000 0%, #000 ${percent}%, rgba(0,0,0,0) ${percent}%, rgba(0,0,0,0) 100%)`
  }
})
</script>

<style scoped>
.animate-fade-in {
  animation: fadeIn 0.3s ease-out;
}
</style>
