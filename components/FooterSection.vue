<template>
  <footer class="bg-primary-900 text-white py-12 md:py-16">
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="grid md:grid-cols-3 gap-8 md:gap-12 mb-8">
          <!-- О проекте -->
          <div>
            <h3 class="text-xl font-bold mb-4">Копич Захар</h3>
            <p class="text-primary-300 text-sm leading-relaxed">
              Профессиональный ведущий мероприятий. <br> Мост между аудиторией и бизнесом.
            </p>
          </div>

          <!-- Навигация -->
          <div>
            <h3 class="text-xl font-bold mb-4">Навигация</h3>
            <nav class="flex flex-col gap-3">
              <a
                href="#about"
                class="text-primary-300 hover:text-white transition-colors text-sm"
                @click.prevent="scrollTo('#about')"
              >
                Обо мне
              </a>
              <a
                href="#services"
                class="text-primary-300 hover:text-white transition-colors text-sm"
                @click.prevent="scrollTo('#services')"
              >
                Форматы мероприятий
              </a>
              <a
                href="#cases"
                class="text-primary-300 hover:text-white transition-colors text-sm"
                @click.prevent="scrollTo('#cases')"
              >
                Кейсы
              </a>
              <a
                href="#contact"
                class="text-primary-300 hover:text-white transition-colors text-sm"
                @click.prevent="scrollTo('#contact')"
              >
                Связаться
              </a>
            </nav>
          </div>

          <!-- Контакты -->
          <div>
            <h3 class="text-xl font-bold mb-4">Контакты</h3>
            <div class="flex flex-col gap-3 text-sm">
              <a
                href="mailto:kopich.zakhar@yandex.ru"
                class="text-primary-300 hover:text-white transition-colors flex items-center gap-2"
              >
                <svg
                  class="w-4 h-4"
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
                kopich.zakhar@yandex.ru
              </a>
              <a
                href="https://t.me/plombir1917"
                target="_blank"
                rel="noopener noreferrer"
                class="text-primary-300 hover:text-white transition-colors flex items-center gap-2"
              >
                <svg
                  class="w-4 h-4"
                  fill="currentColor"
                  viewBox="0 0 24 24"
                >
                  <path
                    d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"
                  />
                </svg>
                Связаться в Telegram
              </a>
            </div>
          </div>
        </div>

        <!-- Разделитель -->
        <div class="w-full h-px bg-primary-700 mb-8"></div>

        <!-- Копирайт -->
        <div class="text-center">
          <p class="text-primary-400 text-sm">
            © {{ currentYear }} Захар Копич. Все права защищены.
          </p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
const currentYear = new Date().getFullYear()

const scrollTo = (selector: string) => {
  const element = document.querySelector(selector)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}
</script>
