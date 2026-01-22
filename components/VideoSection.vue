<template>
  <section
    class="py-24 md:py-32 lg:py-40 bg-primary-900 text-white relative overflow-hidden"
  >
    <!-- Декоративные элементы -->
    <div
      class="absolute inset-0 opacity-5 pointer-events-none"
      aria-hidden="true"
    >
      <div
        class="absolute top-20 left-10 w-96 h-96 bg-white rounded-full blur-3xl"
      ></div>
      <div
        class="absolute bottom-20 right-10 w-72 h-72 bg-white rounded-full blur-3xl"
      ></div>
    </div>

    <div class="container mx-auto px-6 lg:px-8 relative z-10">
      <div class="max-w-5xl mx-auto">
        <!-- Заголовок и описание -->
        <div class="text-center mb-12 md:mb-16">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black mb-6 text-white"
          >
            Энергия в действии
          </h2>
          <p
            class="text-xl md:text-2xl text-primary-200 font-light max-w-3xl mx-auto leading-relaxed"
          >
            Не просто спикер — двигатель IT-событий.
          </p>
          <div class="w-24 h-1 bg-white mx-auto mt-6"></div>
        </div>

        <!-- Видео контейнер -->
        <div
          ref="videoContainer"
          class="relative w-full bg-black rounded-sm overflow-hidden shadow-2xl opacity-0 translate-y-8 transition-all duration-1000 ease-out"
          style="aspect-ratio: 16/9"
        >
          <!-- Placeholder для загрузки -->
          <div
            v-if="!videoLoaded"
            class="absolute inset-0 flex items-center justify-center bg-primary-800 z-10"
          >
            <div class="text-center">
              <svg
                class="w-16 h-16 text-primary-300 animate-spin mx-auto mb-4"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"
                ></path>
              </svg>
              <p class="text-primary-300 text-sm">Загрузка видео...</p>
            </div>
          </div>

          <!-- Iframe с видео -->
          <ClientOnly>
            <iframe
              v-show="videoLoaded"
              src="https://vk.com/video_ext.php?oid=-189962112&id=456239212"
              class="w-full h-full absolute inset-0"
              style="background-color: #000"
              allow="autoplay; encrypted-media; fullscreen; picture-in-picture; screen-wake-lock;"
              frameborder="0"
              allowfullscreen
              @load="handleVideoLoad"
            ></iframe>
            <template #fallback>
              <div
                class="absolute inset-0 flex items-center justify-center bg-primary-800"
              >
                <p class="text-primary-300 text-sm">
                  Видео загружается...
                </p>
              </div>
            </template>
          </ClientOnly>
        </div>

        <!-- Дополнительный текст -->
        <div class="mt-12 text-center">
          <p class="text-primary-300 text-lg max-w-2xl mx-auto">
            Это не просто приглашение на хакатон — это демонстрация того, как
            программист становится движущей силой IT-событий.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const videoLoaded = ref(false)
const videoContainer = ref<HTMLElement | null>(null)
const isVisible = ref(false)

const handleVideoLoad = () => {
  videoLoaded.value = true
}

// Анимация появления при скролле
onMounted(() => {
  if (process.client && videoContainer.value) {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && !isVisible.value) {
            isVisible.value = true
            if (videoContainer.value) {
              videoContainer.value.classList.remove('opacity-0', 'translate-y-8')
              videoContainer.value.classList.add('opacity-100', 'translate-y-0')
            }
            observer.disconnect()
          }
        })
      },
      { threshold: 0.1, rootMargin: '50px' }
    )

    observer.observe(videoContainer.value)
  }
})
</script>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  animation: fadeInUp 0.8s ease-out forwards;
}
</style>
