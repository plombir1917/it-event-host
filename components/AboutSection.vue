<template>
  <section
    id="about"
    class="py-24 md:py-32 lg:py-40 bg-white relative overflow-hidden"
  >
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <!-- Заголовок секции -->
        <div class="text-center mb-16 md:mb-20">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black text-primary-900 mb-6"
          >
            Программист + Шоумен
          </h2>
          <div class="w-24 h-1 bg-primary-900 mx-auto"></div>
        </div>

        <!-- Основной контент -->
        <div class="grid md:grid-cols-2 gap-12 lg:gap-20 items-center">
          <!-- Изображение (на мобильных сверху) -->
          <div class="order-2 md:order-1">
            <div class="relative aspect-[4/5] overflow-hidden">
              <!-- Градиентный оверлей -->
              <div
                class="absolute inset-0 bg-gradient-to-b from-transparent via-transparent to-primary-900/30 z-10"
              ></div>

              <NuxtImg
                src="/images/about/about.jpg"
                alt="Обо мне"
                class="w-full h-full object-cover transition-all duration-1000"
                loading="lazy"
                format="webp"
                quality="90"
                sizes="sm:100vw md:50vw lg:50vw"
                :modifiers="{ sat: -100, con: 15 }"
              />
            </div>
          </div>

          <!-- Текстовый блок -->
          <div class="space-y-6 order-1 md:order-2">
            <p
              class="text-lg md:text-xl text-primary-700 leading-relaxed font-light"
            >
              Не просто ведущий. Программист с
              <strong class="font-semibold text-primary-900"
                >5+ годами опыта</strong
              >
              в разработке, который обладает исключительным навыками публичных выступлений.
            </p>

            <p class="text-lg md:text-xl text-primary-700 leading-relaxed">
              Моя техническая экспертиза позволяет мне:
            </p>

            <ul class="space-y-4">
              <li class="flex items-start gap-4">
                <span
                  class="flex-shrink-0 w-6 h-6 bg-primary-900 text-white rounded-full flex items-center justify-center text-sm font-bold mt-1"
                >
                  ✓
                </span>
                <span class="text-base md:text-lg text-primary-700"
                  >Глубоко понимать технические доклады и задавать правильные
                  вопросы</span
                >
              </li>
              <li class="flex items-start gap-4">
                <span
                  class="flex-shrink-0 w-6 h-6 bg-primary-900 text-white rounded-full flex items-center justify-center text-sm font-bold mt-1"
                >
                  ✓
                </span>
                <span class="text-base md:text-lg text-primary-700"
                  >Создавать атмосферу, где участники чувствуют себя
                  понятыми</span
                >
              </li>
              <li class="flex items-start gap-4">
                <span
                  class="flex-shrink-0 w-6 h-6 bg-primary-900 text-white rounded-full flex items-center justify-center text-sm font-bold mt-1"
                >
                  ✓
                </span>
                <span class="text-base md:text-lg text-primary-700"
                  >Адаптировать контент под аудиторию — от гуманитариев до
                  архитекторов</span
                >
              </li>
              <li class="flex items-start gap-4">
                <span
                  class="flex-shrink-0 w-6 h-6 bg-primary-900 text-white rounded-full flex items-center justify-center text-sm font-bold mt-1"
                >
                  ✓
                </span>
                <span class="text-base md:text-lg text-primary-700"
                  >Управлять техническими дискуссиями и панелями экспертов</span
                >
              </li>
            </ul>
          </div>

          <!-- Визуальный блок / Статистика -->
          <div class="space-y-8">
            <div
              class="bg-primary-900 text-white p-8 md:p-12 border-2 border-primary-900"
            >
              <div class="space-y-6">
                <div>
                  <div
                    class="text-5xl md:text-6xl lg:text-7xl font-black mb-2"
                  >
                    50+
                  </div>
                  <div class="text-lg md:text-xl text-primary-200">
                    Проведенных мероприятий
                  </div>
                </div>
                <div class="w-full h-px bg-primary-700"></div>
                <div>
                  <div
                    class="text-5xl md:text-6xl lg:text-7xl font-black mb-2"
                  >
                    5+
                  </div>
                  <div class="text-lg md:text-xl text-primary-200">
                    Лет в программировании
                  </div>
                </div>
                <div class="w-full h-px bg-primary-700"></div>
                <div>
                  <div
                    class="text-5xl md:text-6xl lg:text-7xl font-black mb-2"
                  >
                    100%
                  </div>
                  <div class="text-lg md:text-xl text-primary-200">
                    Компетенции
                  </div>
                </div>
              </div>
            </div>

            <!-- Дополнительная информация -->
            <div class="text-center">
              <p class="text-primary-600 text-sm md:text-base">
                JavaScript • TypeScript • Python • Go • Cloud • DevOps
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Компонент About секции
</script>
