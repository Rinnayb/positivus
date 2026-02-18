# Positivus — Проект веб-сайта цифрового маркетингового агентства

## Обзор проекта

**Positivus** — статический фронтенд-сайт для цифрового маркетингового агентства. Сайт включает секции: шапка, герой, услуги, кейсы, процесс работы, команда, отзывы, форма связи и подвал.

### Технологический стек

| Категория          | Технология                                           |
| ------------------ | ---------------------------------------------------- |
| **Разметка**       | HTML5 (ESM)                                          |
| **Стилизация**     | SCSS/Sass с методологией BEM                         |
| **Шрифты**         | Space Grotesk (WOFF2)                                |
| **Линтинг**        | ESLint + Stylelint (`friendly-frontend-lint-config`) |
| **Форматирование** | Prettier                                             |
| **Сборка**         | Sass (SCSS → CSS)                                    |

## Структура проекта

```
positivus/
├── index.html              # Главная страница (1297 строк)
├── package.json            # Зависимости и скрипты
├── eslint.config.js        # Конфигурация ESLint
├── prettier.config.js      # Конфигурация Prettier
├── stylelint.config.js     # Конфигурация Stylelint
├── styles/
│   ├── main.scss           # Точка входа стилей
│   ├── _variables.scss     # Переменные SCSS
│   ├── _normalize.scss     # Сброс стилей
│   ├── _globals.scss       # Глобальные стили
│   ├── _utils.scss         # Утилиты
│   └── blocks/             # BEM-компоненты (22 файла)
│       ├── _header.scss
│       ├── _hero.scss
│       ├── _services.scss
│       ├── _service-card.scss
│       ├── _banner.scss
│       ├── _studies.scss
│       ├── _process.scss
│       ├── _team.scss
│       ├── _team-card.scss
│       ├── _testimonials.scss
│       ├── _testimonial-card.scss
│       ├── _contact-us.scss
│       ├── _button.scss
│       ├── _grid.scss
│       ├── _burger-button.scss
│       ├── _cross-button.scss
│       ├── _mobile-overlay.scss
│       ├── _section.scss
│       ├── _puddle-bg.scss
│       ├── _field.scss
│       ├── _radio.scss
│       ├── _radios.scss
│       └── _pagination.scss
├── images/                 # SVG-ассеты
│   ├── logo.svg
│   ├── hero-bg.svg
│   ├── banner-bg.svg
│   ├── partners/           # Логотипы партнёров
│   ├── services/           # Иконки услуг
│   ├── team/               # Фото команды
│   └── icons/              # UI-иконки
├── fonts/                  # Шрифты
│   ├── SpaceGrotesk-Regular.woff2
│   └── SpaceGrotesk-Medium.woff2
└── dist/                   # Скомпилированный CSS (игнорируется git)
    └── main.css
```

## Сборка и запуск

### Установка зависимостей

```bash
npm install
```

### Команды разработки

| Команда                | Описание                             |
| ---------------------- | ------------------------------------ |
| `npm run sass-watch`   | Watch-режим: компиляция SCSS → CSS   |
| `npm run lint:js`      | Линтинг JavaScript/JSX               |
| `npm run lint:js:fix`  | Линтинг JS с автоисправлением        |
| `npm run lint:css`     | Линтинг SCSS/CSS                     |
| `npm run lint:css:fix` | Линтинг CSS с автоисправлением       |
| `npm run format`       | Проверка форматирования (Prettier)   |
| `npm run format:fix`   | Автоформатирование кода              |
| `npm run lint`         | Запуск CSS-линтинга и форматирования |
| `npm run lint:fix`     | Исправление всех проблем линтинга    |

### Быстрый старт

```bash
# 1. Установить зависимости
npm install

# 2. Запустить watch-режим для SCSS
npm run sass-watch

# 3. Открыть index.html в браузере
```

## Конвенции разработки

### BEM-нейминг

Проект использует методологию BEM с префиксами:

```scss
.block {
} // Блок
.block__element {
} // Элемент
.block__element--modifier {
} // Модификатор
```

Примеры:

- `.header__menu-list`
- `.service-card--green-bg`
- `.hero__partners-item`

### Структура SCSS-компонентов

Каждый блок в `styles/blocks/` следует паттерну:

```scss
.block {
  &__element {
    // стили
  }

  &__element--modifier {
    // стили модификатора
  }
}
```

### Именование файлов

- Стили блоков: `_block-name.scss` (с подчёркиванием)
- Переменные/утилиты: `_variables.scss`, `_utils.scss`
- Главный файл: `main.scss` (без подчёркивания)

### Адаптивный дизайн

В проекте используются классы видимости:

- `.hidden-mobile` — скрыть на мобильных
- `.visible-mobile` — показать только на мобильных

### Доступность (a11y)

- `.visually-hidden` — визуально скрыть, но оставить для скринридеров
- `aria-*` атрибуты для интерактивных элементов
- Семантическая разметка (`<header>`, `<main>`, `<section>`, `<article>`)

## Основные компоненты

| Компонент      | Описание                                |
| -------------- | --------------------------------------- |
| `header`       | Шапка с логотипом, навигацией и кнопкой |
| `hero`         | Главный экран с заголовком и партнёрами |
| `services`     | Сетка карточек услуг (6 штук)           |
| `service-card` | Карточка услуги с иконкой и ссылкой     |
| `banner`       | Баннер с призывом к действию            |
| `studies`      | Кейсы с примерами работ                 |
| `process`      | Аккордеон процесса работы               |
| `team`         | Карточки команды                        |
| `testimonials` | Отзывы клиентов                         |
| `contact-us`   | Форма обратной связи                    |

## Конфигурация линтинга

Все конфиги используют общий пресет `friendly-frontend-lint-config`:

- **ESLint**: `@eslint/js`, `eslint-plugin-react`, `eslint-plugin-jsx-a11y`
- **Stylelint**: `stylelint-config-standard-scss`, `stylelint-order`, `stylelint-selector-bem-pattern`
- **Prettier**: стандартные настройки через общий конфиг

## Git

Игнорируемые файлы (`.gitignore`):

```
node_modules
dist
.idea
.DS_Store
```
