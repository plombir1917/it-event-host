<template>
  <section
    id="education"
    class="py-24 md:py-32 lg:py-40 bg-primary-50 relative overflow-hidden"
  >
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <!-- Заголовок секции -->
        <div class="text-center mb-16 md:mb-20">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black text-primary-900 mb-6"
          >
            Профессиональная база
          </h2>
          <p class="text-xl md:text-2xl text-primary-600 font-light max-w-2xl mx-auto">
            Образование, опыт преподавания и текущая практика
          </p>
          <div class="w-24 h-1 bg-primary-900 mx-auto mt-6"></div>
        </div>

        <!-- Основной контент -->
        <div
          ref="contentContainer"
          class="grid md:grid-cols-2 gap-12 lg:gap-20 items-start opacity-0 translate-y-8 transition-all duration-1000 ease-out"
        >
          <!-- Текстовый блок -->
          <div class="space-y-8">
            <!-- Высшее образование -->
            <div>
              <h3 class="text-2xl md:text-3xl font-bold text-primary-900 mb-4">
                Высшее образование
              </h3>
              <p class="text-base md:text-lg text-primary-700 leading-relaxed mb-2">
                Липецкий государственный технический университет (ЛГТУ)
              </p>
              <p class="text-base md:text-lg text-primary-700 leading-relaxed">
                Бакалавриат и магистратура с отличием
              </p>
            </div>

            <!-- Опыт преподавания -->
            <div>
              <h3 class="text-2xl md:text-3xl font-bold text-primary-900 mb-4">
                Опыт преподавания
              </h3>
              <p class="text-base md:text-lg text-primary-700 leading-relaxed mb-2">
                Официальный преподаватель в ЛГТУ (1 год)
              </p>
              <p class="text-base md:text-lg text-primary-700 leading-relaxed">
                Преподавал программирование студентам среднего профессионального
                образования (СПО). Опыт работы с аудиторией и передачи технических
                знаний.
              </p>
            </div>

            <!-- Дополнительное образование -->
            <div>
              <h3 class="text-2xl md:text-3xl font-bold text-primary-900 mb-4">
                Дополнительное образование
              </h3>
              <p class="text-base md:text-lg text-primary-700 leading-relaxed mb-2">
                Повышение квалификации в Яндекс
              </p>
              <p class="text-base md:text-lg text-primary-700 leading-relaxed">
                Удостоверение о повышении квалификации по программе «Бэкенд на
                Node.js для фронтенд-разработчиков»
              </p>
            </div>

            <!-- Текущая позиция -->
            <div class="bg-primary-900 text-white p-6 md:p-8 border-2 border-primary-900">
              <h3 class="text-2xl md:text-3xl font-bold mb-4">Текущая позиция</h3>
              <p class="text-lg md:text-xl text-primary-200 font-semibold mb-3">
                Ведущий программист
              </p>
              <p class="text-base md:text-lg text-primary-200 leading-relaxed mb-2">
                Отдел разработки программного обеспечения
              </p>
              <p class="text-base md:text-lg text-primary-200 leading-relaxed mb-2">
                ОБУ ИТЦ — Областное бюджетное учреждение «Информационно-технический
                центр»
              </p>
              <p class="text-sm md:text-base text-primary-300 mt-4">
                Опыт работы: 3 года и продолжается
              </p>
            </div>
          </div>

          <!-- Документы -->
          <div class="space-y-6">
            <!-- Дипломы -->
            <div>
              <h4 class="text-lg font-semibold text-primary-900 mb-4">
                Документы об образовании
              </h4>
              <div class="grid grid-cols-2 gap-4">
                <button
                  @click="openModal('diploma-bachelor')"
                  class="group relative aspect-[3/4] overflow-hidden bg-primary-100 border-2 border-primary-200 hover:border-primary-900 transition-all duration-300"
                >
                  <NuxtImg
                    v-if="documents.diplomaBachelor"
                    :src="documents.diplomaBachelor"
                    alt="Диплом бакалавра"
                    class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-500"
                    loading="lazy"
                    format="webp"
                    quality="85"
                  />
                  <div
                    v-else
                    class="absolute inset-0 flex items-center justify-center"
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
                          d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
                        ></path>
                      </svg>
                      <p class="text-xs text-primary-600">Диплом бакалавра</p>
                    </div>
                  </div>
                </button>
                <button
                  @click="openModal('diploma-master')"
                  class="group relative aspect-[3/4] overflow-hidden bg-primary-100 border-2 border-primary-200 hover:border-primary-900 transition-all duration-300"
                >
                  <NuxtImg
                    v-if="documents.diplomaMaster"
                    :src="documents.diplomaMaster"
                    alt="Диплом магистра"
                    class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-500"
                    loading="lazy"
                    format="webp"
                    quality="85"
                  />
                  <div
                    v-else
                    class="absolute inset-0 flex items-center justify-center"
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
                          d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
                        ></path>
                      </svg>
                      <p class="text-xs text-primary-600">Диплом магистра</p>
                    </div>
                  </div>
                </button>
              </div>
            </div>

            <!-- Сертификаты Яндекс (галерея) -->
            <div>
              <h4 class="text-lg font-semibold text-primary-900 mb-4">
                Сертификаты Яндекс
              </h4>
              <div class="grid grid-cols-2 gap-4">
                <button
                  v-for="(cert, index) in documents.certificates"
                  :key="index"
                  @click="openCertificateGallery(index)"
                  class="group relative aspect-[4/3] overflow-hidden bg-primary-100 border-2 border-primary-200 hover:border-primary-900 transition-all duration-300"
                >
                  <NuxtImg
                    v-if="cert"
                    :src="cert"
                    :alt="`Сертификат Яндекс ${index + 1}`"
                    class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-500"
                    loading="lazy"
                    format="webp"
                    quality="85"
                  />
                  <div
                    v-else
                    class="absolute inset-0 flex items-center justify-center"
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
                          d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"
                        ></path>
                      </svg>
                      <p class="text-xs text-primary-600">
                        Сертификат {{ index + 1 }}
                      </p>
                    </div>
                  </div>
                </button>
              </div>
            </div>

            <!-- Резюме -->
            <div>
              <h4 class="text-lg font-semibold text-primary-900 mb-4">
                Резюме
              </h4>
              <a
                :href="documents.resume || '#'"
                target="_blank"
                rel="noopener noreferrer"
                class="group flex items-center gap-3 p-4 bg-white border-2 border-primary-200 hover:border-primary-900 transition-all duration-300"
              >
                <svg
                  class="w-8 h-8 text-primary-600 group-hover:text-primary-900 transition-colors"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M7 21h10a2 2 0 002-2V9.414a1 1 0 00-.293-.707l-5.414-5.414A1 1 0 0012.586 3H7a2 2 0 00-2 2v14a2 2 0 002 2z"
                  ></path>
                </svg>
                <div class="flex-1">
                  <p class="font-semibold text-primary-900">Резюме (PDF)</p>
                  <p class="text-sm text-primary-600">Открыть документ</p>
                </div>
                <svg
                  class="w-5 h-5 text-primary-400 group-hover:text-primary-900 transition-colors"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
                  ></path>
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Модальное окно для просмотра документов -->
    <ClientOnly>
      <div
        v-if="modalOpen"
        class="fixed inset-0 z-50 flex items-center justify-center bg-black/90 p-4"
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

        <!-- Навигация для галереи (только для сертификатов) -->
        <template v-if="isCertificateGallery">
          <!-- Кнопка "Назад" -->
          <button
            v-if="currentGalleryIndex > 0"
            @click="previousImage"
            class="absolute left-4 top-1/2 -translate-y-1/2 text-white hover:text-primary-200 transition-colors z-10 bg-black/50 rounded-full p-3"
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
            v-if="
              currentGalleryIndex <
              (certificateGallery.length || documents.certificates.length) - 1
            "
            @click="nextImage"
            class="absolute right-4 top-1/2 -translate-y-1/2 text-white hover:text-primary-200 transition-colors z-10 bg-black/50 rounded-full p-3"
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
            class="absolute bottom-4 left-1/2 -translate-x-1/2 flex gap-2 z-10"
          >
            <button
              v-for="(cert, index) in certificateGallery"
              :key="index"
              @click="goToImage(index)"
              class="w-2 h-2 rounded-full transition-all"
              :class="
                index === currentGalleryIndex
                  ? 'bg-white w-6'
                  : 'bg-white/50 hover:bg-white/75'
              "
              :aria-label="`Перейти к изображению ${index + 1}`"
            ></button>
          </div>
        </template>

        <!-- Изображение -->
        <div class="max-w-4xl w-full max-h-[90vh] overflow-auto">
          <NuxtImg
            v-if="currentDocument"
            :src="currentDocument"
            :alt="currentDocumentTitle"
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
import { ref, onMounted, onUnmounted } from 'vue'

// Пути к документам (замените на реальные пути)
const documents = ref({
  diplomaBachelor: '', // '/documents/diploma-bachelor.jpg'
  diplomaMaster: '', // '/documents/diploma-master.jpg'
  certificates: [
    '', ''
    // '/documents/certificate-yandex-1.jpg',
    // '/documents/certificate-yandex-2.jpg',
    // '/documents/certificate-yandex-3.jpg'
  ] as string[],
  resume: '' // '/documents/resume.pdf'
})

const modalOpen = ref(false)
const currentDocument = ref<string | null>(null)
const currentDocumentTitle = ref('')
const isCertificateGallery = ref(false)
const certificateGallery = ref<string[]>([])
const currentGalleryIndex = ref(0)

const openModal = (docType: string) => {
  const docMap: Record<string, { src: string; title: string }> = {
    'diploma-bachelor': {
      src: documents.value.diplomaBachelor || '',
      title: 'Диплом бакалавра'
    },
    'diploma-master': {
      src: documents.value.diplomaMaster || '',
      title: 'Диплом магистра'
    }
  }

  const doc = docMap[docType]
  if (doc && doc.src) {
    currentDocument.value = doc.src
    currentDocumentTitle.value = doc.title
    isCertificateGallery.value = false
    modalOpen.value = true
    if (process.client) {
      document.body.style.overflow = 'hidden'
    }
  }
}

const openCertificateGallery = (startIndex: number) => {
  const validCertificates = documents.value.certificates.filter((cert) => cert)
  if (validCertificates.length === 0) return

  certificateGallery.value = validCertificates
  currentGalleryIndex.value = startIndex
  currentDocument.value = validCertificates[startIndex]
  currentDocumentTitle.value = `Сертификат Яндекс ${startIndex + 1}`
  isCertificateGallery.value = true
  modalOpen.value = true
  if (process.client) {
    document.body.style.overflow = 'hidden'
  }
}

const nextImage = () => {
  if (
    currentGalleryIndex.value <
    certificateGallery.value.length - 1
  ) {
    currentGalleryIndex.value++
    currentDocument.value =
      certificateGallery.value[currentGalleryIndex.value]
    currentDocumentTitle.value = `Сертификат Яндекс ${currentGalleryIndex.value + 1}`
  }
}

const previousImage = () => {
  if (currentGalleryIndex.value > 0) {
    currentGalleryIndex.value--
    currentDocument.value =
      certificateGallery.value[currentGalleryIndex.value]
    currentDocumentTitle.value = `Сертификат Яндекс ${currentGalleryIndex.value + 1}`
  }
}

const goToImage = (index: number) => {
  currentGalleryIndex.value = index
  currentDocument.value = certificateGallery.value[index]
  currentDocumentTitle.value = `Сертификат Яндекс ${index + 1}`
}

const closeModal = () => {
  modalOpen.value = false
  currentDocument.value = null
  currentDocumentTitle.value = ''
  isCertificateGallery.value = false
  certificateGallery.value = []
  currentGalleryIndex.value = 0
  if (process.client) {
    document.body.style.overflow = ''
  }
}

const contentContainer = ref<HTMLElement | null>(null)

// Клавиатурная навигация для галереи
const handleKeydown = (event: KeyboardEvent) => {
  if (!modalOpen.value || !isCertificateGallery.value) return

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
  if (process.client && contentContainer.value) {
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            if (contentContainer.value) {
              contentContainer.value.classList.remove(
                'opacity-0',
                'translate-y-8'
              )
              contentContainer.value.classList.add('opacity-100', 'translate-y-0')
            }
            observer.disconnect()
          }
        })
      },
      { threshold: 0.1, rootMargin: '50px' }
    )

    observer.observe(contentContainer.value)
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
