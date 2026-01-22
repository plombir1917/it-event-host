<template>
  <section
    id="cases"
    class="py-24 md:py-32 lg:py-40 bg-primary-50 relative overflow-hidden"
  >
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <!-- Заголовок секции -->
        <div class="text-center mb-16 md:mb-20">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black text-primary-900 mb-6"
          >
            Опыт и кейсы
          </h2>
          <p
            class="text-xl md:text-2xl text-primary-600 font-light max-w-2xl mx-auto"
          >
            Реальные мероприятия, реальные результаты
          </p>
          <div class="w-24 h-1 bg-primary-900 mx-auto mt-6"></div>
        </div>

        <!-- Сетка кейсов -->
        <div class="grid md:grid-cols-2 gap-8 lg:gap-12">
          <!-- Кейс 1 -->
          <div
            class="bg-white border-2 border-primary-200 overflow-hidden hover:border-primary-900 transition-all duration-300 group"
          >
            <div class="relative aspect-video overflow-hidden">
              <NuxtImg
                src="/images/cases/first.jpg"
                alt="Всероссийский форум «ИТ-Академ» - Форум"
                class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700"
                loading="lazy"
                format="webp"
                quality="85"
                sizes="sm:100vw md:50vw lg:50vw"
                :modifiers="{ sat: -100, con: 20 }"
              />
            </div>
            <div class="p-8">
              <div class="mb-6">
                <span
                  class="inline-block px-4 py-1 bg-primary-900 text-white text-sm font-semibold mb-4"
                >
                  Форум
                </span>
                <h3
                  class="text-2xl md:text-3xl font-bold text-primary-900 mb-3"
                >
                  Всероссийский форум <br />
                  «ИТ-Академ»
                </h3>
                <p class="text-primary-600 text-sm">
                  СОК "Прометей" • 200+ участников
                </p>
              </div>
              <p class="text-primary-700 leading-relaxed mb-6">
                Ведущий главной сцены на закрытии форума. Модерация награждения
                100+ человек, интервью с ключевыми спикерами, управление Q&A
                сессиями. Положительные отзывы от организаторов и участников.
              </p>
              <div class="flex flex-wrap gap-2">
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Модерация
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Интервью
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Q&A
                </span>
              </div>
            </div>
          </div>

          <!-- Кейс 2 -->
          <div
            class="bg-white border-2 border-primary-200 overflow-hidden hover:border-primary-900 transition-all duration-300 group"
          >
            <div class="relative aspect-video overflow-hidden">
              <NuxtImg
                src="/images/cases/second.jpg"
                alt="IT-Хакатон 2025  - Хакатон"
                class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700"
                loading="lazy"
                format="webp"
                quality="85"
                sizes="sm:100vw md:50vw lg:50vw"
                :modifiers="{ sat: -100, con: 20 }"
              />
            </div>
            <div class="p-8">
              <div class="mb-6">
                <span
                  class="inline-block px-4 py-1 bg-primary-900 text-white text-sm font-semibold mb-4"
                >
                  Хакатон
                </span>
                <h3
                  class="text-2xl md:text-3xl font-bold text-primary-900 mb-3"
                >
                  IT-Хакатон 2025
                </h3>
                <p class="text-primary-600 text-sm">
                  Школа 21 • 200+ участников
                </p>
              </div>
              <p class="text-primary-700 leading-relaxed mb-6">
                Полное ведение 48-часового хакатона. Открытие, техническая
                поддержка команд, презентация проектов, награждение. Создание
                энергичной атмосферы, поддержание мотивации участников на
                протяжении всего события.
              </p>
              <div class="flex flex-wrap gap-2">
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Ведущий
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Техподдержка
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Презентации
                </span>
              </div>
            </div>
          </div>

          <!-- Кейс 3 -->
          <div
            class="bg-white border-2 border-primary-200 overflow-hidden hover:border-primary-900 transition-all duration-300 group"
          >
            <div class="relative aspect-video overflow-hidden">
              <NuxtImg
                src="/images/cases/third.jpg"
                alt="Product Launch Event - Корпоративное событие"
                class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700"
                loading="lazy"
                format="webp"
                quality="85"
                sizes="sm:100vw md:50vw lg:50vw"
                :modifiers="{ sat: -100, con: 20 }"
              />
            </div>
            <div class="p-8">
              <div class="mb-6">
                <span
                  class="inline-block px-4 py-1 bg-primary-900 text-white text-sm font-semibold mb-4"
                >
                  Корпоративное событие
                </span>
                <h3
                  class="text-2xl md:text-3xl font-bold text-primary-900 mb-3"
                >
                  Фестиваль IT-культуры
                </h3>
                <p class="text-primary-600 text-sm">
                  Разные площадки • 1000+ зрителей
                </p>
              </div>
              <p class="text-primary-700 leading-relaxed mb-6">
                Ведущий VI ежегодного фестиваля IT-культуры. В течение недели
                был проводником в атмосферу технологий, вдохновения и IT.
                Интерактивные сессии с аудиторией, высокий уровень вовлечённости
                зрителей.
              </p>
              <div class="flex flex-wrap gap-2">
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Комьюнити
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Продвижение
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Демо
                </span>
              </div>
            </div>
          </div>

          <!-- Кейс 4 -->
          <div
            class="bg-white border-2 border-primary-200 overflow-hidden hover:border-primary-900 transition-all duration-300 group"
          >
            <div class="relative aspect-video overflow-hidden">
              <NuxtImg
                src="/images/cases/fourth.jpg"
                alt="React Community Meetup - Митап"
                class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-700"
                loading="lazy"
                format="webp"
                quality="85"
                sizes="sm:100vw md:50vw lg:50vw"
                :modifiers="{ sat: -100, con: 20 }"
              />
            </div>
            <div class="p-8">
              <div class="mb-6">
                <span
                  class="inline-block px-4 py-1 bg-primary-900 text-white text-sm font-semibold mb-4"
                >
                  Митап
                </span>
                <h3
                  class="text-2xl md:text-3xl font-bold text-primary-900 mb-3"
                >
                  IT Community Meetup
                </h3>
                <p class="text-primary-600 text-sm">
                  Центр управления регионом • 150+ участников
                </p>
              </div>
              <p class="text-primary-700 leading-relaxed mb-6">
                Регулярное ведение митапов регионального IT-сообщества.
                Модерация докладов, технические дискуссии, нетворкинг-сессии.
                Создание комфортной атмосферы для обмена опытом между
                разработчиками разных уровней.
              </p>
              <div class="flex flex-wrap gap-2">
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Митап
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Нетворкинг
                </span>
                <span
                  class="px-3 py-1 bg-primary-100 text-primary-700 text-xs font-medium"
                >
                  Сообщество
                </span>
              </div>
            </div>
          </div>
        </div>

        <!-- Дополнительная информация -->
        <div class="mt-16 text-center">
          <p class="text-primary-600 text-lg">
            И это только часть опыта. Готов обсудить детали вашего проекта.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Компонент Cases секции
</script>
