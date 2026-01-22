# IT Event Host - Landing Page

Профессиональная landing page для ведущего-программиста IT-мероприятий.

## Технологии

- **Nuxt 3** - Vue.js фреймворк
- **TypeScript** - Типизация
- **Tailwind CSS** - Стилизация
- **Composition API** - Современный подход к компонентам

## Установка

```bash
# Установка зависимостей
npm install

# Запуск dev сервера
npm run dev

# Сборка для production
npm run build

# Предпросмотр production сборки
npm run preview
```

## Структура проекта

```
├── assets/
│   └── css/
│       └── main.css          # Глобальные стили
├── components/
│   ├── HeroSection.vue       # Главная секция
│   ├── AboutSection.vue      # О ведущем
│   ├── ServicesSection.vue   # Форматы мероприятий
│   ├── WhyMeSection.vue      # Преимущества
│   ├── CasesSection.vue      # Кейсы
│   ├── TestimonialsSection.vue # Отзывы
│   └── CTASection.vue        # Форма контакта
├── pages/
│   └── index.vue             # Главная страница
├── app.vue                   # Корневой компонент
├── nuxt.config.ts            # Конфигурация Nuxt
└── tailwind.config.js        # Конфигурация Tailwind
```

## Особенности

- ✅ Полностью адаптивный дизайн
- ✅ Премиум минималистичный стиль
- ✅ SEO-оптимизация
- ✅ Плавные анимации
- ✅ Чистая архитектура компонентов

## Настройка

### Контакты

Измените контактные данные в `components/CTASection.vue`:
- Email
- Телефон

### Контент

Все тексты находятся в компонентах и могут быть легко изменены.

## Лицензия

MIT
