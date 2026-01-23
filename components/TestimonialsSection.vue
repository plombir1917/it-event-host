<template>
  <section class="py-24 md:py-32 lg:py-40 bg-white relative overflow-hidden">
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <!-- Заголовок секции -->
        <div class="text-center mb-16 md:mb-20">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black text-primary-900 mb-6"
          >
            Отзывы
          </h2>
          <p
            class="text-xl md:text-2xl text-primary-600 font-light max-w-2xl mx-auto"
          >
            Что говорят организаторы и участники
          </p>
          <div class="w-24 h-1 bg-primary-900 mx-auto mt-6"></div>
        </div>

        <!-- Сетка отзывов -->
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- Отзыв 1 -->
          <div class="bg-primary-50 border-2 border-primary-200 p-8">
            <div class="mb-6">
              <div class="flex gap-1 mb-4">
                <span class="text-primary-900 text-xl">★★★★★</span>
              </div>
              <p class="text-primary-700 leading-relaxed italic mb-6">
                "Он уверенно ведёт и людей, и проекты: в коде - как архитектор,
                на сцене - как харизматичный ведущий. Думает на шаг вперёд,
                говорит по делу и зажигает интерес к ИТ даже у тех, кто ещё
                вчера боялся слова «алгоритм». Перспективный, точный,
                современный. Если будущее можно скомпилировать - он уже это
                делает."
              </p>
            </div>
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <NuxtImg
                  src="/images/reviews/first.jpg"
                  alt="Арсений Болдырев"
                  class="w-12 h-12 rounded-full object-cover"
                  loading="lazy"
                  format="webp"
                  quality="85"
                  :modifiers="{ sat: -100 }"
                />
              </div>
              <div>
                <div class="font-bold text-primary-900">Арсений Болдырев</div>
                <div class="text-sm text-primary-600">
                  Директор АНО <br />"Область будущего"
                </div>
              </div>
            </div>
          </div>

          <!-- Отзыв 2 -->
          <div class="bg-primary-50 border-2 border-primary-200 p-8">
            <div class="mb-6">
              <div class="flex gap-1 mb-4">
                <span class="text-primary-900 text-xl">★★★★★</span>
              </div>
              <p class="text-primary-700 leading-relaxed italic mb-6">
                "Регулярно ведет и модерирует мероприятия, связанные со спортивным программированием, киберспортом и цифровыми технологиями.
                Его отличает способность компетентно вести профессиональную дискуссию, оперируя подходящей терминологией."
              </p>
            </div>
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <NuxtImg
                  src="/images/reviews/second.jpg"
                  alt="Данил Сапронов"
                  class="w-12 h-12 rounded-full object-cover"
                  loading="lazy"
                  format="webp"
                  quality="85"
                  :modifiers="{ sat: -100 }"
                />
              </div>
              <div>
                <div class="font-bold text-primary-900">Данил Сапронов</div>
                <div class="text-sm text-primary-600">
Директор ГОБПОУ <br> «Колледж искусственного интеллекта в машиностроительной отрасли»
                </div>
              </div>
            </div>
          </div>

          <!-- Отзыв 3 -->
          <div class="bg-primary-50 border-2 border-primary-200 p-8">
            <div class="mb-6">
              <div class="flex gap-1 mb-4">
                <span class="text-primary-900 text-xl">★★★★★</span>
              </div>
              <p class="text-primary-700 leading-relaxed italic mb-6">
                "Как участник конференции, я был впечатлён. Ведущий понимал
                технические доклады, задавал уточняющие вопросы, создавал
                атмосферу, где разработчики чувствовали себя понятыми. Это
                редкость."
              </p>
            </div>
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <NuxtImg
                  src="/images/reviews/.jpg"
                  alt="Иван Козлов"
                  class="w-12 h-12 rounded-full object-cover grayscale"
                  loading="lazy"
                  format="webp"
                  quality="85"
                  :modifiers="{ sat: -100 }"
                />
              </div>
              <div>
                <div class="font-bold text-primary-900">Иван Козлов</div>
                <div class="text-sm text-primary-600">Senior Developer</div>
              </div>
            </div>
          </div>

          <!-- Отзыв 4 -->
          <div
            class="bg-primary-900 text-white border-2 border-primary-900 p-8"
          >
            <div class="mb-6">
              <div class="flex gap-1 mb-4">
                <span class="text-white text-xl">★★★★★</span>
              </div>
              <p class="text-primary-200 leading-relaxed italic mb-6">
                "Мы работали с разными ведущими, но этот — особенный. Его
                техническая экспертиза позволила ему не просто вести
                мероприятие, а создавать контент вместе со спикерами.
                Рекомендую."
              </p>
            </div>
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <NuxtImg
                  src="/images/reviews/.jpg"
                  alt="Мария Волкова"
                  class="w-12 h-12 rounded-full object-cover grayscale opacity-80"
                  loading="lazy"
                  format="webp"
                  quality="85"
                  :modifiers="{ sat: -100 }"
                />
              </div>
              <div>
                <div class="font-bold">Мария Волкова</div>
                <div class="text-sm text-primary-300">
                  Event Manager, BigTech Corp
                </div>
              </div>
            </div>
          </div>

          <!-- Отзыв 5 -->
          <div class="bg-primary-50 border-2 border-primary-200 p-8">
            <div class="mb-6">
              <div class="flex gap-1 mb-4">
                <span class="text-primary-900 text-xl">★★★★★</span>
              </div>
              <p class="text-primary-700 leading-relaxed italic mb-6">
                "Гибкость и адаптивность — это про него. Когда возникли
                технические проблемы, он справился с ситуацией профессионально,
                не потеряв темп мероприятия. Настоящий профессионал."
              </p>
            </div>
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <NuxtImg
                  src="/images/reviews/.jpg"
                  alt="Сергей Новиков"
                  class="w-12 h-12 rounded-full object-cover grayscale"
                  loading="lazy"
                  format="webp"
                  quality="85"
                  :modifiers="{ sat: -100 }"
                />
              </div>
              <div>
                <div class="font-bold text-primary-900">Сергей Новиков</div>
                <div class="text-sm text-primary-600">CTO, Startup Inc</div>
              </div>
            </div>
          </div>

          <!-- Отзыв 6 -->
          <div class="bg-primary-50 border-2 border-primary-200 p-8">
            <div class="mb-6">
              <div class="flex gap-1 mb-4">
                <span class="text-primary-900 text-xl">★★★★★</span>
              </div>
              <p class="text-primary-700 leading-relaxed italic mb-6">
                "Он не просто ведущий — он программист на сцене. Это чувствуется
                в каждом слове, в каждом вопросе. Аудитория это ценит. Мы
                обязательно пригласим его снова."
              </p>
            </div>
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <NuxtImg
                  src="/images/reviews/.jpg"
                  alt="Елена Соколова"
                  class="w-12 h-12 rounded-full object-cover grayscale"
                  loading="lazy"
                  format="webp"
                  quality="85"
                  :modifiers="{ sat: -100 }"
                />
              </div>
              <div>
                <div class="font-bold text-primary-900">Елена Соколова</div>
                <div class="text-sm text-primary-600">Community Lead</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Компонент Testimonials секции
</script>
