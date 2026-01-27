<template>
  <section
    id="services"
    class="section-y bg-primary-50 relative overflow-hidden"
  >
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-7xl mx-auto">
        <!-- Заголовок секции -->
        <div class="text-center mb-12 md:mb-16">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black text-primary-900 mb-4"
          >
            Разные форматы, один уровень
          </h2>
          <p class="text-xl md:text-2xl text-primary-600 font-light max-w-2xl mx-auto">
            Не только IT. Бэкграунд как фишка на традиционных событиях.
          </p>
          <div class="w-24 h-1 bg-primary-900 mx-auto mt-6"></div>
        </div>

        <!-- Галерея -->
        <div
          ref="galleryContainer"
          class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-3 gap-4 md:gap-6 opacity-0 translate-y-8 transition-all duration-1000 ease-out"
        >
          <button
            v-for="(image, index) in galleryImages"
            :key="index"
            @click="openGallery(index)"
            class="group relative aspect-[4/5] md:aspect-[3/4] overflow-hidden bg-primary-100 border-2 border-primary-200 hover:border-primary-900 transition-all duration-300"
            :class="getImageClass(index)"
          >
            <NuxtImg
              v-if="image.src"
              :src="image.src"
              :alt="image.alt || `Мероприятие ${index + 1}`"
              class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700"
              loading="lazy"
              format="webp"
              quality="85"
            />
            <div
              v-else
              class="absolute inset-0 flex items-center justify-center bg-primary-50"
            >
              <div class="text-center p-4">
                <svg
                  class="w-12 h-12 text-primary-400 mx-auto mb-2"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"
                  ></path>
                </svg>
                <p class="text-xs text-primary-600">{{ image.category || 'Мероприятие' }}</p>
              </div>
            </div>
          </button>
        </div>
      </div>
    </div>

    <!-- Модальное окно галереи -->
    <ClientOnly>
      <div
        v-if="modalOpen"
        class="fixed inset-0 z-50 flex items-center justify-center bg-black/95 p-4"
        @click.self="closeModal"
      >
        <!-- Кнопка закрытия -->
        <button
          @click="closeModal"
          class="absolute top-4 right-4 text-white hover:text-primary-200 transition-colors z-10"
          aria-label="Закрыть"
        >
          <svg
            class="w-8 h-8"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            ></path>
          </svg>
        </button>

        <!-- Кнопка "Назад" -->
        <button
          v-if="currentImageIndex > 0"
          @click="previousImage"
          class="absolute left-4 top-1/2 -translate-y-1/2 text-white hover:text-primary-200 transition-colors z-10 bg-black/50 rounded-full p-3 backdrop-blur-sm"
          aria-label="Предыдущее изображение"
        >
          <svg
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M15 19l-7-7 7-7"
            ></path>
          </svg>
        </button>

        <!-- Кнопка "Вперед" -->
        <button
          v-if="currentImageIndex < validImages.length - 1"
          @click="nextImage"
          class="absolute right-4 top-1/2 -translate-y-1/2 text-white hover:text-primary-200 transition-colors z-10 bg-black/50 rounded-full p-3 backdrop-blur-sm"
          aria-label="Следующее изображение"
        >
          <svg
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M9 5l7 7-7 7"
            ></path>
          </svg>
        </button>

        <!-- Индикатор текущего изображения -->
        <div
          v-if="validImages.length > 1"
          class="absolute bottom-4 left-1/2 -translate-x-1/2 flex gap-2 z-10"
        >
          <button
            v-for="(img, index) in validImages"
            :key="index"
            @click="goToImage(index)"
            class="w-2 h-2 rounded-full transition-all"
            :class="
              index === currentImageIndex
                ? 'bg-white w-6'
                : 'bg-white/50 hover:bg-white/75'
            "
            :aria-label="`Перейти к изображению ${index + 1}`"
          ></button>
        </div>

        <!-- Изображение -->
        <div class="max-w-6xl w-full max-h-[90vh] overflow-auto">
          <NuxtImg
            v-if="currentImage"
            :src="currentImage.src"
            :alt="currentImage.alt || 'Мероприятие'"
            class="w-full h-auto"
            format="webp"
            quality="90"
          />
        </div>
      </div>
    </ClientOnly>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, computed } from 'vue'

interface GalleryImage {
  src: string
  alt?: string
  category?: string
}

// Изображения галереи (замените на реальные пути)
const galleryImages = ref<GalleryImage[]>([
  // Корпоративные мероприятия
  {
    src: '/images/events/corporate-1.jpg',
    alt: 'Корпоративное мероприятие',
    category: 'Корпоративные'
  },
  {
    src: '/images/events/corporate-2.jpg',
    alt: 'Корпоративное мероприятие',
    category: 'Корпоративные'
  },
  // Церемонии награждения
  {
    src: '/images/events/awards-1.jpg',
    alt: 'Церемония награждения',
    category: 'Награждения'
  },
  {
    src: '/images/events/awards-2.jpg',
    alt: 'Церемония награждения',
    category: 'Награждения'
  },
  // Деловые мероприятия
  {
    src: '/images/events/business-1.jpg',
    alt: 'Деловое мероприятие',
    category: 'Деловые'
  },
  // Официальные / протокольные мероприятия
  {
    src: '/images/events/business-2.jpg',
    alt: 'Деловое мероприятие',
    category: 'Деловые'
  },
])

const modalOpen = ref(false)
const currentImageIndex = ref(0)
const galleryContainer = ref<HTMLElement | null>(null)

const validImages = computed(() => {
  return galleryImages.value.filter((img) => img.src)
})

const currentImage = computed(() => {
  return validImages.value[currentImageIndex.value] || null
})

const getImageClass = (_index: number) => {
  // Равномерная сетка без разрывов: все элементы одинакового размера
  return 'md:col-span-1 md:row-span-1'
}

const openGallery = (index: number) => {
  const validIndex = validImages.value.findIndex(
    (img) => img === galleryImages.value[index]
  )
  if (validIndex === -1) return

  currentImageIndex.value = validIndex
  modalOpen.value = true
  if (process.client) {
    document.body.style.overflow = 'hidden'
  }
}

const nextImage = () => {
  if (currentImageIndex.value < validImages.value.length - 1) {
    currentImageIndex.value++
  }
}

const previousImage = () => {
  if (currentImageIndex.value > 0) {
    currentImageIndex.value--
  }
}

const goToImage = (index: number) => {
  currentImageIndex.value = index
}

const closeModal = () => {
  modalOpen.value = false
  if (process.client) {
    document.body.style.overflow = ''
  }
}

// Клавиатурная навигация
const handleKeydown = (event: KeyboardEvent) => {
  if (!modalOpen.value) return

  if (event.key === 'ArrowLeft') {
    previousImage()
  } else if (event.key === 'ArrowRight') {
    nextImage()
  } else if (event.key === 'Escape') {
    closeModal()
  }
}

// Анимация появления при скролле
onMounted(() => {
  if (process.client && galleryContainer.value) {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            if (galleryContainer.value) {
              galleryContainer.value.classList.remove(
                'opacity-0',
                'translate-y-8'
              )
              galleryContainer.value.classList.add('opacity-100', 'translate-y-0')
            }
            observer.disconnect()
          }
        })
      },
      { threshold: 0.1, rootMargin: '50px' }
    )

    observer.observe(galleryContainer.value)
  }

  // Добавляем обработчик клавиатуры
  if (process.client) {
    window.addEventListener('keydown', handleKeydown)
  }
})

onUnmounted(() => {
  if (process.client) {
    window.removeEventListener('keydown', handleKeydown)
  }
})
</script>
