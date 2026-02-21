# Positivus

Статический сайт цифрового маркетингового агентства.

![Positivus](./images/hero-bg.svg)

## 🚀 Быстрый старт

```bash
# Установка зависимостей
npm install

# Запуск компиляции SCSS в режиме наблюдения
npm run sass-watch

# Открыть index.html в браузере
```

## 🛠 Технологии

| Категория | Технология |
|-----------|------------|
| Разметка | HTML5 |
| Стилизация | SCSS/Sass (BEM) |
| Шрифты | Space Grotesk |
| Линтинг | ESLint + Stylelint |
| Форматирование | Prettier |

## 📦 Основные команды

```bash
npm run sass-watch      # Watch-режим SCSS → CSS
npm run lint            # Проверка кода
npm run lint:fix        # Исправление ошибок
npm run format:fix      # Форматирование кода
```

## 📁 Структура

```
positivus/
├── index.html          # Главная страница
├── styles/
│   ├── main.scss       # Точка входа стилей
│   ├── blocks/         # BEM-компоненты
│   └── helpers/        # Миксины и медиа-запросы
├── images/             # SVG-ассеты
├── fonts/              # Шрифты
└── dist/               # Скомпилированный CSS
```

## 📐 Адаптивность

- Desktop: 1280px+
- Tablet: 768px – 1280px
- Mobile: 375px – 768px

## 📄 Лицензия

ISC
