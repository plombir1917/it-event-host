<template>
  <section class="relative w-full hero-screen overflow-hidden">
    <!-- Декоративные элементы -->
    <div
      class="absolute inset-0 opacity-5 pointer-events-none"
      aria-hidden="true"
    >
      <div
        class="absolute top-20 left-10 w-72 h-72 bg-primary-900 rounded-full blur-3xl"
      ></div>
      <div
        class="absolute bottom-20 right-10 w-96 h-96 bg-primary-900 rounded-full blur-3xl"
      ></div>
    </div>

    <!-- FULLSCREEN split -->
    <div class="relative z-10 grid min-h-full grid-cols-1 lg:grid-cols-2">
      <!-- Левая колонка (чёрный фон + текст) -->
      <div
        class="relative bg-black text-white flex items-center bg-cover bg-center"
        style="background-image: url('/images/hero/left-bg.jpg')"
      >
        <div class="absolute inset-0 bg-black/70"></div>

        <div
          class="relative z-10 w-full text-center lg:text-left px-6 lg:px-12 py-16 lg:py-20 max-w-xl mx-auto lg:ml-auto"
        >
          <h1
            class="text-4xl sm:text-lg md:text-6xl lg:text-6xl xl:text-7xl font-black mb-6 leading-tight tracking-tight animate-fade-in-up "
          >
            Ведущий-Программист
          </h1>

          <p
            class="text-xl md:text-2xl lg:text-3xl text-primary-100 font-light mb-12 max-w-2xl mx-auto lg:mx-0 leading-relaxed animate-fade-in-up"
            style="animation-delay: 0.2s"
          >
            Айтишник на сцене. <br />
            Опытный специалист на стыке технической экспертизы и событийного бизнеса.
          </p>

          <div
            class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start items-center animate-fade-in-up"
            style="animation-delay: 0.4s"
          >
            <a
              href="#contact"
              class="group relative px-8 py-4 bg-primary-900 text-white font-semibold text-lg rounded-none transition-all duration-300 hover:bg-primary-800 hover:shadow-2xl hover:shadow-primary-900/20 hover:-translate-y-1"
            >
              <span class="relative z-10">Обсудить проект</span>
              <span
                class="absolute inset-0 bg-primary-800 scale-x-0 group-hover:scale-x-100 transition-transform origin-left duration-300"
              ></span>
            </a>

            <a
              href="#about"
              class="px-8 py-4 border-2 border-white/30 text-white font-semibold text-lg rounded-none transition-all duration-300 hover:border-white hover:bg-white/10"
            >
              Узнать больше
            </a>
          </div>

          <div
            class="mt-12 lg:mt-16 flex flex-wrap justify-center lg:justify-start gap-6 text-sm md:text-base text-primary-300 animate-fade-in"
            style="animation-delay: 0.6s"
          >
            <div class="flex items-center gap-2">
              <span class="w-2 h-2 bg-white/70 rounded-full"></span>
              <span>Конференции</span>
            </div>
            <div class="flex items-center gap-2">
              <span class="w-2 h-2 bg-white/70 rounded-full"></span>
              <span>Форумы</span>
            </div>
            <div class="flex items-center gap-2">
              <span class="w-2 h-2 bg-white/70 rounded-full"></span>
              <span>Деловые события</span>
            </div>
            <div class="flex items-center gap-2">
              <span class="w-2 h-2 bg-white/70 rounded-full"></span>
              <span>Корпоративные мероприятия</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Правая колонка: скрыта на mobile -->
      <div class="hidden lg:flex bg-primary-50 items-center justify-center">
        <div
          class="relative w-full h-full flex items-center justify-center px-6 lg:px-12 py-16 lg:py-20"
        >
          <div
            class="relative aspect-[4/5] overflow-hidden h-full w-full max-w-[800px] mr-auto"
          >
            <div
              class="absolute inset-0 opacity-[0.03] z-10"
              style="background-image: url('data:image/svg+xml,%3Csvg viewBox=\'0 0 400 400\' xmlns=\'http://www.w3.org/2000/svg\'%3E%3Cfilter id=\'noiseFilter\'%3E%3CfeTurbulence type=\'fractalNoise\' baseFrequency=\'4\' numOctaves=\'3\' stitchTiles=\'stitch\'/%3E%3C/filter%3E%3Crect width=\'100%25\' height=\'100%25\' filter=\'url(%23noiseFilter)\'/%3E%3C/svg%3E');"
            ></div>

            <NuxtImg
              src="/images/hero/portrait-no-bg.png"
              alt="Ведущий-программист на сцене"
              class="w-full h-full object-cover transition-all duration-1000"
              loading="eager"
              format="webp"
              quality="90"
              sizes="lg:50vw"
              :modifiers="{ sat: -100, con: 20 }"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- Scroll indicator (mobile) -->
    <div
      class="absolute bottom-6 left-1/2 -translate-x-1/2 animate-bounce lg:hidden z-10"
    >
      <svg
        class="w-6 h-6 text-white"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M19 14l-7 7m0 0l-7-7m7 7V3"
        />
      </svg>
    </div>

   <!-- Scroll indicator (desktop) -->
<div
  class="absolute bottom-6 inset-x-0 hidden lg:flex justify-center px-[25%] animate-bounce z-10 pointer-events-none"
>
  <svg
    class="w-6 h-6"
    fill="none"
    viewBox="0 0 24 24"
    xmlns="http://www.w3.org/2000/svg"
  >
    <defs>
      <!-- Градиент: слева белый, справа чёрный -->
      <linearGradient
        id="arrowGradient"
        x1="0%"
        y1="0%"
        x2="100%"
        y2="0%"
      >
        <stop offset="0%" stop-color="white" />
        <stop offset="50%" stop-color="white" />
        <stop offset="50%" stop-color="black" />
        <stop offset="100%" stop-color="black" />
      </linearGradient>
    </defs>

    <path
      d="M19 14l-7 7m0 0l-7-7m7 7V3"
      stroke="url(#arrowGradient)"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</div>

  </section>
</template>

<script setup lang="ts">
// Hero секция
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
  opacity: 0;
}

</style>
