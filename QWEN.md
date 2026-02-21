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
├── index.html              # Главная страница (1470 строк)
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
│   ├── _fonts.scss         # Подключение шрифтов
│   ├── helpers/            # Миксины и медиа-запросы
│   │   ├── _index.scss     # Экспорт helpers
│   │   ├── _media.scss     # Медиа-запросы (breakpoints)
│   │   └── _mixins.scss    # Общие миксины
│   └── blocks/             # BEM-компоненты (26 файлов)
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
│       ├── _footer.scss
│       ├── _soc1als.scss
│       ├── _subscribe-form.scss
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
│   ├── logo-light.svg
│   ├── hero-bg.svg
│   ├── banner-bg.svg
│   ├── contact-us-bg.svg
│   ├── partners/           # Логотипы партнёров
│   ├── services/           # Иконки услуг
│   ├── team/               # Фото команды
│   └── icons/              # UI-иконки
├── fonts/                  # Шрифты
│   ├── SpaceGrotesk-Medium.woff2
│   └── SpaceGrotesk-Regular.woff2
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

В проекте используются брейкпоинты из `_media.scss`:

| Брейкпоинт      | Значение  | Миксин            |
| --------------- | --------- | ----------------- |
| Desktop above   | 1281px+   | `@include desktop-above` |
| Desktop         | ≤1280px   | `@include desktop` |
| Tablet above    | 1024px+   | `@include tablet-above` |
| Tablet          | ≤1023px   | `@include tablet` |
| Mobile above    | 768px+    | `@include mobile-above` |
| Mobile          | ≤767px    | `@include mobile` |
| Mobile S above  | 481px+    | `@include mobile-s-above` |
| Mobile S        | ≤480px    | `@include mobile-s` |

Классы видимости:

- `.hidden-mobile` — скрыть на мобильных
- `.visible-mobile` — показать только на мобильных

### Доступность (a11y)

- `.visually-hidden` — визуально скрыть, но оставить для скринридеров
- `aria-*` атрибуты для интерактивных элементов
- Семантическая разметка (`<header>`, `<main>`, `<section>`, `<article>`)

## Основные компоненты

| Компонент          | Описание                                |
| ------------------ | --------------------------------------- |
| `header`           | Шапка с логотипом, навигацией и кнопкой |
| `hero`             | Главный экран с заголовком и партнёрами |
| `services`         | Сетка карточек услуг (6 штук)           |
| `service-card`     | Карточка услуги с иконкой и ссылкой     |
| `banner`           | Баннер с призывом к действию            |
| `studies`          | Кейсы с примерами работ                 |
| `process`          | Аккордеон процесса работы               |
| `team`             | Карточки команды                        |
| `testimonials`     | Отзывы клиентов                         |
| `contact-us`       | Форма обратной связи                    |
| `footer`           | Подвал с навигацией и соцсетями         |
| `soc1als`          | Иконки социальных сетей                 |
| `subscribe-form`   | Форма подписки                          |

## CSS-переменные

Основные переменные определены в `_variables.scss`:

```scss
--color-green: #b9ff66;
--color-grey: #f3f3f3;
--color-grey-alt: #898989;
--color-dark: #191a23;
--color-dark-alt: #292a32;
--color-white: #ffffff;

--border-radius: 14px;
--border-radius-small: 7px;
--border-radius-large: 45px;

--font-family-base: 'Space Grotesk', sans-serif;

--container-width: 1240px;
--container-padding-x: 20px;

--section-padding-y: 70px;
--input-height: 59px;
--button-height: 68px;
```

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
