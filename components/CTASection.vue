<template>
  <section
    id="contact"
    class="py-24 md:py-32 lg:py-40 bg-primary-900 text-white relative overflow-hidden"
  >
    <!-- Декоративные элементы -->
    <div
      class="absolute inset-0 opacity-10 pointer-events-none"
      aria-hidden="true"
    >
      <div
        class="absolute top-20 right-10 w-96 h-96 bg-white rounded-full blur-3xl"
      ></div>
      <div
        class="absolute bottom-20 left-10 w-72 h-72 bg-white rounded-full blur-3xl"
      ></div>
    </div>

    <div class="container mx-auto px-6 lg:px-8 relative z-10">
      <div class="max-w-4xl mx-auto">
        <!-- Заголовок секции -->
        <div class="text-center mb-12 md:mb-16">
          <h2
            class="text-4xl md:text-5xl lg:text-6xl font-black mb-6 text-white"
          >
            Готовы обсудить проект?
          </h2>
          <p class="text-xl md:text-2xl text-primary-200 font-light max-w-2xl mx-auto">
            Давайте создадим незабываемое IT-мероприятие вместе
          </p>
          <div class="w-24 h-1 bg-white mx-auto mt-6"></div>
        </div>

        <!-- Форма контакта -->
        <div class="bg-white/10 backdrop-blur-sm border-2 border-white/20 p-8 md:p-12">
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div class="grid md:grid-cols-2 gap-6">
              <!-- Имя -->
              <div>
                <label
                  for="name"
                  class="block text-sm font-semibold text-white mb-2"
                >
                  Имя *
                </label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  required
                  class="w-full px-4 py-3 bg-white/10 border-2 border-white/20 text-white placeholder-primary-300 focus:outline-none focus:border-white transition-colors"
                  placeholder="Ваше имя"
                />
              </div>

              <!-- Email -->
              <div>
                <label
                  for="email"
                  class="block text-sm font-semibold text-white mb-2"
                >
                  Email *
                </label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  required
                  class="w-full px-4 py-3 bg-white/10 border-2 border-white/20 text-white placeholder-primary-300 focus:outline-none focus:border-white transition-colors"
                  placeholder="your@email.com"
                />
              </div>
            </div>

            <!-- Компания -->
            <div>
              <label
                for="company"
                class="block text-sm font-semibold text-white mb-2"
              >
                Компания / Организация
              </label>
              <input
                id="company"
                v-model="form.company"
                type="text"
                class="w-full px-4 py-3 bg-white/10 border-2 border-white/20 text-white placeholder-primary-300 focus:outline-none focus:border-white transition-colors"
                placeholder="Название компании"
              />
            </div>

            <!-- Тип мероприятия -->
            <div>
              <label
                for="eventType"
                class="block text-sm font-semibold text-white mb-2"
              >
                Тип мероприятия
              </label>
              <select
                id="eventType"
                v-model="form.eventType"
                class="w-full px-4 py-3 bg-white/10 border-2 border-white/20 text-white focus:outline-none focus:border-white transition-colors"
              >
                <option value="" class="bg-primary-900">Выберите тип</option>
                <option value="conference" class="bg-primary-900">
                  Конференция
                </option>
                <option value="hackathon" class="bg-primary-900">
                  Хакатон
                </option>
                <option value="corporate" class="bg-primary-900">
                  Корпоративное событие
                </option>
                <option value="meetup" class="bg-primary-900">Митап</option>
                <option value="tech-show" class="bg-primary-900">
                  Tech Show
                </option>
                <option value="other" class="bg-primary-900">Другое</option>
              </select>
            </div>

            <!-- Сообщение -->
            <div>
              <label
                for="message"
                class="block text-sm font-semibold text-white mb-2"
              >
                Сообщение *
              </label>
              <textarea
                id="message"
                v-model="form.message"
                required
                rows="5"
                class="w-full px-4 py-3 bg-white/10 border-2 border-white/20 text-white placeholder-primary-300 focus:outline-none focus:border-white transition-colors resize-none"
                placeholder="Расскажите о вашем мероприятии..."
              ></textarea>
            </div>

            <!-- Кнопка отправки -->
            <div class="pt-4">
              <button
                type="submit"
                class="w-full md:w-auto px-8 py-4 bg-white text-primary-900 font-bold text-lg hover:bg-primary-100 transition-all duration-300 hover:shadow-2xl hover:shadow-white/20"
              >
                Отправить запрос
              </button>
            </div>
          </form>

          <!-- Альтернативные способы связи -->
          <div class="mt-12 pt-8 border-t border-white/20">
            <p class="text-center text-primary-200 mb-6">
              Или свяжитесь напрямую:
            </p>
            <div
              class="flex flex-col sm:flex-row gap-4 justify-center items-center"
            >
              <a
                href="mailto:contact@example.com"
                class="flex items-center gap-2 text-white hover:text-primary-200 transition-colors"
              >
                <svg
                  class="w-5 h-5"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                  ></path>
                </svg>
                <span>kopich.zakhar@yandex.ru</span>
              </a>
              <span class="hidden sm:inline text-white/30">•</span>
              <a
                href="tel:+79991234567"
                class="flex items-center gap-2 text-white hover:text-primary-200 transition-colors"
              >
                <svg
                  class="w-5 h-5"
                  fill="none"
                  stroke="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
                  ></path>
                </svg>
                <span>+7 (920) 247-xx-xx</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  company: '',
  eventType: '',
  message: ''
})

const handleSubmit = () => {
  // Здесь должна быть логика отправки формы
  // Например, отправка на API или email
  console.log('Form submitted:', form.value)
  alert('Спасибо за ваш запрос! Я свяжусь с вами в ближайшее время.')

  // Сброс формы
  form.value = {
    name: '',
    email: '',
    company: '',
    eventType: '',
    message: ''
  }
}
</script>
