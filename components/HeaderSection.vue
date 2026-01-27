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

        <!-- Desktop navigation -->
        <div class="hidden md:flex items-center gap-8">
          <NuxtLink
            to="/"
            class="font-medium transition-all"
            :style="navLinkStyle('/')"
          >
            Главная
          </NuxtLink>

          <NuxtLink
            to="/about"
            class="font-medium transition-all"
            :style="navLinkStyle('/about')"
          >
            Обо мне
          </NuxtLink>

          <NuxtLink
            to="/cases"
            class="font-medium transition-all"
            :style="navLinkStyle('/cases')"
          >
            Кейсы
          </NuxtLink>

          <!-- CTA -->
          <a
            href="#"
            class="px-6 py-2 font-semibold transition-colors"
            :style="ctaStyle"
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
          <span
            class="block w-6 h-0.5 bg-current transition-all"
            :class="mobileMenuOpen ? 'rotate-45 translate-y-2' : ''"
          />
          <span
            class="block w-6 h-0.5 bg-current transition-all"
            :class="mobileMenuOpen ? 'opacity-0' : ''"
          />
          <span
            class="block w-6 h-0.5 bg-current transition-all"
            :class="mobileMenuOpen ? '-rotate-45 -translate-y-2' : ''"
          />
        </button>
      </div>

      <!-- Mobile menu -->
      <div
        v-if="mobileMenuOpen"
        class="md:hidden pb-6 pt-4 border-t border-white/10 bg-black animate-fade-in"
      >
        <div class="flex flex-col gap-5">
          <NuxtLink
            to="/"
            class="text-white/80 hover:text-white"
            @click="closeMobileMenuAndGoHome"
          >
            Главная
          </NuxtLink>
          <NuxtLink
            to="/about"
            class="text-white/80 hover:text-white"
            @click="closeMobileMenu"
          >
            Обо мне
          </NuxtLink>
          <NuxtLink
            to="/cases"
            class="text-white/80 hover:text-white"
            @click="closeMobileMenu"
          >
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

// стартовое состояние для desktop
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

/* ===== СТИЛИ ===== */

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

/* 🎯 NAV + active underline */
const navLinkStyle = (path: string) => {
  const isActive = route.path === path

  // базовый цвет (везде)
  let color = '#ffffff'

  // динамический цвет ТОЛЬКО на главной и desktop
  if (!isMobile.value && isHome.value) {
    const t = Math.min(1, Math.max(0, (headerFill.value - 0.5) / 0.5))
    const v = Math.round(255 * t)
    color = `rgb(${v}, ${v}, ${v})`
  }

  return {
    color,
    fontWeight: isActive ? '600' : '500',
    boxShadow: isActive
      ? `inset 0 -2px 0 0 ${color}`
      : 'inset 0 -2px 0 0 transparent',
    transition: 'color 0.3s, box-shadow 0.3s'
  }
}

/* 🎯 CTA кнопка */
const ctaStyle = computed(() => {
  if (isMobile.value || !isHome.value) {
    return { backgroundColor: '#fff', color: '#000' }
  }

  const t = Math.min(1, Math.max(0, (headerFill.value - 0.5) / 0.5))
  const v = Math.round(255 * t)
  const bg = `rgb(${v}, ${v}, ${v})`
  const text = v > 128 ? '#000' : '#fff'

  return {
    backgroundColor: bg,
    color: text
  }
})

/* ===== ACTIONS ===== */

const toggleMobileMenu = () => (mobileMenuOpen.value = !mobileMenuOpen.value)
const closeMobileMenu = () => (mobileMenuOpen.value = false)
const closeMobileMenuAndGoHome = closeMobileMenu

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
