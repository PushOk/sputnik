# Grunt - сборщик проектов

При разработке сайтов мы используем систему сборки - [Grunt](http://gruntjs.com/), которая легко расширяется.

Про Grunt можно подробно почитать по ссылкам:
* [gruntjs.com](https://gruntjs.com/) - официальный сайт Grunt.
* [Grunt для тех, кто считает штуки вроде него странными и сложными](http://frontender.info/grunt-is-not-weird-and-hard/).
* [Сборка сайтов на независимых блоках из Jade и Stylus с использованием Grunt.js](http://oleggromov.com/slides/independent-blocks-assemble/).
* [Grunt: система сборки для фронтенд-разработчиков](http://sapegin.ru/pres/grunt/).

Для старта проекта нам понадобится уже готовый шаблон - **[CSSSR Project Template](https://github.com/CSSSR/csssr-project-template)**.

Ставьте :star: Star и подписывайтесь на обновления шаблона, чтобы всегда использовать последнюю версию.


## 1. Подготовка к работе

1. Устанавливаем [Node.js](http://nodejs.org/download/), включающий в себя NPM (Node Packet Manager).
2. `npm i -g grunt-cli` - устанавливаем Grunt CLI (интерфейс командной строки).<br>
После этого следует закрыть и заново открыть окно терминала.<br>
Если при вызове команды `grunt` пишет ошибку `Command Not Found`, то нужно перезагрузиться или выйти из системы и зайти снова.
3. Устанавливаем [Git](http://git-scm.com/book/ru/Введение-Установка-Git) под Вашу ОС, если ещё не установлен.

Эти 3 шага выполняются один раз.


## 2. Приступаем к работе

1. `git clone https://github.com/CSSSR/csssr-project-template.git new-project` - cкачать в папку `new-project`.
2. `npm i` - устанавливаем пакеты.
3. `grunt` - запускаем Grunt и работаем.


## 3. Что включено в шаблон CSSSR Project Template

### 3.1. Пакеты NPM
Для повседневных задач нам достаточно:
* [`bump`](https://www.npmjs.org/package/grunt-bump) - обновление версии проекта.
* [`clean`](https://www.npmjs.org/package/grunt-contrib-clean) - очистка папки от файлов.
* [`spritesmith`](https://www.npmjs.org/package/grunt-spritesmith) - генератор спрайтов и CSS переменных.
* [`imagemin`](https://www.npmjs.org/package/grunt-contrib-imagemin) - сжатие картинок.
* [`stylus`](https://www.npmjs.org/package/grunt-contrib-stylus) - препроцессор CSS.
* [`autoprefixer`](https://www.npmjs.org/package/grunt-autoprefixer) - подстановка префиксов для заданных браузеров.
* ['combine-media-queries'](https://www.npmjs.org/package/grunt-combine-media-queries) - комбинирование медиа-запросов в CSS.
* [`csscomb`](https://www.npmjs.org/package/grunt-csscomb) - форматирование CSS.
* [`jade`](https://www.npmjs.org/package/grunt-contrib-jade) - препроцессор HTML.
* [`prettify`](https://www.npmjs.org/package/grunt-prettify) - форматирование HTML.
* [`jshint`](https://www.npmjs.org/package/grunt-contrib-jshint) - проверка JavaScript на качество кода с подсказками.
* [`copy`](https://www.npmjs.org/package/grunt-contrib-copy) - создание копий файлов.
* [`uglify`](https://www.npmjs.org/package/grunt-contrib-uglify) - минифицирование и обфускация скриптов.
* [`replace`](https://www.npmjs.org/package/grunt-replace) автозамена паттернов на заданные значения.
* [`newer`](https://www.npmjs.org/package/grunt-newer) - выполнение задач только с новыми файлами.
* [`connect`](https://www.npmjs.org/package/grunt-contrib-connect) - сервер проекта.
* [`watch`](https://www.npmjs.org/package/grunt-contrib-watch) - отслеживание изменений файлов и их компиляция.

В зависимости от проекта дополнительно могут пригодиться такие пакеты:
* Для объединения и минификации:
    * [`cssmin`](https://www.npmjs.org/package/grunt-contrib-cssmin) - минификация CSS.
    * [`concat`](https://www.npmjs.org/package/grunt-contrib-concat) - объединение скриптов в один файл.<br>
      *Если возникают ошибки при конкатенации скриптов, то нужно установить порядку их зависисмости*.
    * [`uglify`](https://www.npmjs.org/package/grunt-contrib-uglify) - обфускация скриптов.

* Препроцессоры:
    * [`coffee`](https://www.npmjs.org/package/grunt-contrib-coffee) - CoffeeScript препроцессор JavaScript.
    * [`less`](https://www.npmjs.org/package/grunt-contrib-less) - Less препроцессор CSS.
    * [`sass`](https://www.npmjs.org/package/grunt-contrib-sass)/[`compass`](https://www.npmjs.org/package/grunt-contrib-compass) - Sass препроцессор CSS.


* Если этого будет недостаточно, можно поискать подходящие по ссылкам:
    * [gruntjs.com/plugins](https://gruntjs.com/plugins)
    * [npmjs.org](https://www.npmjs.org/)


### 3.2. Структура папок и файлов

```
├── app/                               # Исходники
│   ├── images/                        # Папка изображений
│   │   ├── icons/                     # Иконки сайта
│   │   ├── sprite/                    # PNG изображения для генерации спрайта
│   │   └── sprite.png                 # Спрайт
│   ├── scripts/                       # Папка со скриптами
│   │   ├── browsehappy                # Папка с библиотеками и плагинами
│   │   │   ├── browsehappy.js         # Заглушка для неподдерживаемых браузеров
│   │   │   └── detect.min.js          # Детекция браузеров
│   │   ├── libs                       # Папка с библиотеками и плагинами
│   │   │   └── jquery-2.1.1.min.js    # jQuery
│   │   └── main.js                    # Главный скрипт
│   ├── styles/                        # Папка со стилями Stylus
│   │   ├── base/                      # Базовые стили
│   │   │   ├── common.styl            # Базовый стилевой файл
│   │   │   ├── fonts.styl             # Подключение шрифтов
│   │   │   └── normalize.styl         # Сброс стилей
│   │   ├── components/                # Компоненты (кнопки, тестовые поля и т.п.)
│   │   ├── helpers/                   # Помощники
│   │   │   ├── mixins.styl            # Миксины
│   │   │   ├── sprite.styl            # Переменные с данными спрайта
│   │   │   └── variables.styl         # Переменные
│   │   ├── partials/                  # Стили частиц страниц
│   │   │   ├── footer.styl            # Стили подвала
│   │   │   └── header.styl            # Стили шапки
│   │   ├── pages/                     # Стили страниц
│   │   |   └── main.styl              # Стили главной страницы
│   │   └── main.styl                  # Главный стилевой файл
│   ├── templates/                     # Папка с шаблонами Jade
│   │   ├── helpers/                   # Папка с помощниками
│   │   │   ├── mixins.jade            # Миксины
│   │   │   └── variables.jade         # Переменные
│   │   ├── layouts/                   # Папка с шаблонами раскладки
│   │   │   └── default.jade           # Шаблон раскладки по умолчанию
│   │   ├── partials/                  # Папка с подлючаемыми шаблонами
│   │   │   ├── footer.jade            # Шаблон подвала
│   │   │   ├── head.jade              # Шаблон с ресурсами, SEO и мета-тегами
│   │   │   ├── header.jade            # Шаблон шапки
│   │   │   └── scripts.jade           # Шаблон со скриптами
│   │   └── index.jade                 # Шаблон страницы
│   └── favicon.ico                    # Иконка сайта
├── dist/                              # Сборка для заказчика
│   ├── assets/                        # Подключаемые ресурсы
│   │   └── 0.7.3/                     # Версия ресурсов
│   │       ├── images/                # Папка изображений
│   │       ├── scripts/               # Папка скриптов
│   │       └── styles/                # Папка стилей
│   └── index.html                     # Индексный файл
├── .csscomb.json                      # Конфигурация форматирования CSS
├── .gitignore                         # Список исключённых файлов из Git
├── Gruntfile.js                       # Список задач для Grunt
├── package.json                       # Список пакетов и прочей информацией
└── readme.md                          # Документация шаблона
```

Описание для некоторых папок:
* `app/` - папка с иходниками, из которой генерируюется `dist/`.
* `app/fonts/` - папка для шрифтов, по умолчанию папки нет.
* `app/images/` - папка с фонами, паттернами и прочими стилевыми изображениями.
* `app/images/icons/` - папка со значками сайта для iOS и плитками для Windows.
* `app/images/sprite/` - папка с PNG-изображениями для генерации спрайта в `app/images/sprite.png` и файла стилей с CSS-переменными в `app/styles/sprite.styl`.
* `app/images/svg/` - папка для векторных изображений SVG, по умолчанию папки нет.
* `app/images/temp/` - папка для временного контента, например, для товаров, аватарок, обложек и т.п., по умолчанию папки нет.
* `dist/` - сборка сайта для заказчика, по умолчанию её может не быть и можно без страха и риска её удалить, т.к. она генерируется каждый раз заново, при сборке всё её содержимое удаляется, поэтому руками в неё класть ничего не нужно, при необходимости в `Grunfiles.js` можно добавить в задачу с копированием определённых файлов.


## 4. Поддержка браузеров

Для автоматической подстановки префиксов используется [Autoprefixer](https://github.com/ai/autoprefixer), поэтому достаточно указать минимальные версии браузеров. При этом самим указывать префиксы в стилях, делать для них миксины или использовать готовые не нужно.

Версии браузеров указываются в [`package.json`](https://github.com/CSSSR/csssr-project-template/blob/master/package.json#L55-L63).

```javascript
"browsers": {
    "android": 4,
    "chrome": 35,
    "firefox": 30,
    "ie": 10,
    "ios": 6,
    "opera": 12,
    "safari": 6
}
```

Версии браузера автоматически подставляются в заглушку для неподдерживаемых браузеров.

## 5. Команды для запуска с Grunt

* `grunt` - очищается папка `dist/`, компилируются и копируются файлы в `dist/`, запускается сервер с доступом к сайту по адресу [`http://127.0.0.1:3000`](http://127.0.0.1:3000) и отслеживаются изменения файлов. Для выключения нажать `ctrl + c` или закрыть консоль.
* `grunt build` - очищается папка `dist/`, компилируются и копируются файлы в `dist/` только один раз.
* `grunt serve` - запускается сервер с доступом к сайту по адресу [`http://127.0.0.1:3000`](http://127.0.0.1:3000).

Перед коммитом обязательно сделать `grunt build`, чтобы папка очистилась от лишних файлов.

Проверить можно с помощью `grunt serve`.

## 6. LiveReload - автоперезагрузка страницы после компиляции

Если необходима автоперезагрузка страницы после компиляции, то можно установить расширение [LiveReload](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei) для Chrome или раскомментировать в `Gruntfile.js` строку [`livereload: true`](https://github.com/CSSSR/csssr-project-template/blob/master/Gruntfile.js#L258) в секции `connect`, тем самым внедряя в каждую страницу скрипт для автоперезагрузки, это полезно для мобильных устройств.

## 7. Анти-кэш или версионность ресурсов

Все подключаемые ресурсы в HTML-файлах находятся в папке `assets/x.x.x`, где `x.x.x` — это номер версии, подхватывающийся из [`package.json`](https://github.com/CSSSR/csssr-project-template/blob/master/package.json#L3). После обновления версии и перекомпиляции путь до ресурсов изменится, и браузеры уже не будут брать старые файлы из кэша.

Для обновления версии проекта используется [`grunt-bump`](https://www.npmjs.org/package/grunt-bump), который обновляет версию в `package.json`.

Список доступных команд для обновления версий:

Команда | Назначение
--- | ---
`grunt bump` / `grunt bump:patch` | Патч версия: 0.0.x. Правки, фиксы.
`grunt bump:minor` | Минорная версия: 0.x.0. Добавление новой страницы, фичи.
`grunt bump:major` | Мажорная версия: x.0.0. Релиз заказчику.

Проекты стартуют с версии `0.1.0`.

## 8. Список страниц

Если на проекте страниц больше одной, то необходимо сделать список со страницами.

В качестве списка используется индексная страница `index.jade` (`index.html`).

Список страниц должен быть слегка оформлен:
* Логотип сайта.
* Ссылки по цветовой гамме сайта.
* Список и логотип должны быть отцентрированы.
* **Стили должны быть встроены в страницу, подключать внешний стилевой файл или использовать стили сайта не нужно**.
* Страница должна быть валидной и корректно отображаться на мобильных устройствах.
