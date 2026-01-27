<template>
  <section
    id="contact"
    class="section-y bg-primary-900 text-white relative overflow-hidden"
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
                href="mailto:kopich.zakhar@yandex.ru"
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
                href="https://t.me/plombir1917"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center gap-2 text-white hover:text-primary-200 transition-colors"
              >
                <svg
                  class="w-5 h-5"
                  fill="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"
                  />
                </svg>
                <span>Написать в Telegram</span>
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
