<template>
  <footer class="bg-primary-900 text-white py-12 md:py-16">
    <div class="container mx-auto px-6 lg:px-8">
      <div class="max-w-6xl mx-auto">
        <div class="grid md:grid-cols-3 gap-8 md:gap-12 mb-8">
          <!-- О проекте -->
          <div>
            <h3 class="text-xl font-bold mb-4">IT Event Host</h3>
            <p class="text-primary-300 text-sm leading-relaxed">
              Профессиональный ведущий IT-мероприятий. Программист на сцене с
              технической экспертизой и харизмой.
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
                О ведущем
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
                href="mailto:contact@example.com"
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
                contact@example.com
              </a>
              <a
                href="tel:+79991234567"
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
                    d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
                  ></path>
                </svg>
                +7 (999) 123-45-67
              </a>
            </div>
          </div>
        </div>

        <!-- Разделитель -->
        <div class="w-full h-px bg-primary-700 mb-8"></div>

        <!-- Копирайт -->
        <div class="text-center">
          <p class="text-primary-400 text-sm">
            © {{ currentYear }} IT Event Host. Все права защищены.
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
