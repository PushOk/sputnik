# 2. Grunt - сборщик проектов

При разработке сайтов мы используем систему сборки - [Grunt](http://gruntjs.com/), которая легко расширяется.

Про Grunt можно подробно почитать по ссылкам:
* [gruntjs.com](https://gruntjs.com/) - официальный сайт Grunt.
* [Grunt для тех, кто считает штуки вроде него странными и сложными](http://frontender.info/grunt-is-not-weird-and-hard/).
* [Сборка сайтов на независимых блоках из Jade и Stylus с использованием Grunt.js](http://oleggromov.com/slides/independent-blocks-assemble/).
* [Grunt: система сборки для фронтенд-разработчиков](http://sapegin.ru/pres/grunt/).

Для старта проекта нам понадобится уже готовый шаблон - **[CSSSR Project Template](https://github.com/CSSSR/csssr-project-template)**.

Ставьте :star: Star и подписывайтесь на обновления шаблона, чтобы всегда использовать последнюю версию.


## 2.1. Подготовка к работе

1. Устанавливаем [Node.js](http://nodejs.org/download/), включающий в себя NPM (Node Packet Manager).
2. `npm i -g grunt-cli` - устанавливаем Grunt CLI (интерфейс командной строки).<br>
После этого следует закрыть и заново открыть окно терминала.<br>
Если при вызове команды `grunt` пишет ошибку `Command Not Found`, то нужно перезагрузиться или выйти из системы и зайти снова.
3. Устанавливаем [Git](http://git-scm.com/book/ru/Введение-Установка-Git) под Вашу ОС, если ещё не установлен.

Эти 3 шага выполняются один раз.


## 2.2. Приступаем к работе

1. `git clone https://github.com/CSSSR/csssr-project-template.git new-project` - cкачать в папку `new-project`.
2. `npm i` - устанавливаем пакеты.
3. `grunt` - запускаем Grunt и работаем.


## 2.3. Что включено в шаблон CSSSR Project Template

### 2.3.1. Пакеты NPM
Для повседневных задач нам достаточно:
* [`clean`](https://www.npmjs.org/package/grunt-contrib-clean) - очистка папки от файлов.
* [`spritesmith`](https://www.npmjs.org/package/grunt-spritesmith) - генератор спрайтов и CSS переменных.
* [`imagemin`](https://www.npmjs.org/package/grunt-contrib-imagemin) - сжатие картинок.
* [`stylus`](https://www.npmjs.org/package/grunt-contrib-stylus) - препроцессор CSS.
* [`autoprefixer`](https://www.npmjs.org/package/grunt-autoprefixer) - подстановка префиксов для заданных браузеров.
* [`cssbeautifier`](https://www.npmjs.org/package/grunt-cssbeautifier) - форматирование CSS.
* [`jade`](https://www.npmjs.org/package/grunt-contrib-jade) - препроцессор HTML.
* [`prettify`](https://www.npmjs.org/package/grunt-prettify) - форматирование HTML.
* [`jshint`](https://www.npmjs.org/package/grunt-contrib-jshint) - проверка JavaScript на качество кода с подсказками.
* [`copy`](https://www.npmjs.org/package/grunt-contrib-copy) - создание копий файлов.
* [`newer`](https://www.npmjs.org/package/grunt-newer) - выполнение задач только с новыми файлами.
* [`connect`](https://www.npmjs.org/package/grunt-contrib-connect) - сервер проекта.
* [`watch`](https://www.npmjs.org/package/grunt-contrib-watch) - отслеживание изменений файлов и их компиляция.

В зависимости от проекта дополнительно могут пригодиться такие пакеты:
* Для объединения и минификации:
    * [`cssmin`](https://www.npmjs.org/package/grunt-contrib-cssmin) - минификация CSS.
    * [`concat`](https://www.npmjs.org/package/grunt-contrib-concat) - объединение скриптов в один файл.
    * [`uglify`](https://www.npmjs.org/package/grunt-contrib-uglify) - обфускация скриптов.

* Препроцессоры:
    * [`coffee`](https://www.npmjs.org/package/grunt-contrib-coffee) - CoffeeScript препроцессор JavaScript.
    * [`less`](https://www.npmjs.org/package/grunt-contrib-less) - Less препроцессор CSS.
    * [`sass`](https://www.npmjs.org/package/grunt-contrib-sass)/[`compass`](https://www.npmjs.org/package/grunt-contrib-compass) - Sass препроцессор CSS.


* Если этого будет недостаточно, можно поискать подходящие по ссылкам:
    * [gruntjs.com/plugins](https://gruntjs.com/plugins)
    * [npmjs.org](https://www.npmjs.org/)


### 2.3.2. Структура папок и файлов

```
├── app/                               # Исходники
│   ├── images/                        # Папка изображений
│   │   ├── icons/                     # Иконки сайта
│   │   ├── sprite/                    # PNG изображения для генерации спрайта
│   │   ├── temp/                      # Папка для временного контента
│   │   └── sprite.png                 # Спрайт
│   ├── scripts/                       # Папка со скриптами
│   │   ├── libs                       # Папка с библиотеками и плагинами
│   │   │   └── jquery-2.1.1.min.js    # jQuery
│   │   └── main.js                    # Главный скрипт
│   ├── styles/                        # Папка со стилями Stylus
│   │   ├── main.styl                  # Главный стилевой файл
│   │   ├── normalize.styl             # Сброс стилей
│   │   └── sprite.styl                # Переменные с данными спрайта
│   ├── templates/                     # Папка с шаблонами Jade
│   │   ├── partials/                  # Папка с подлючаемыми шаблонами
│   │   │   ├── footer.jade            # Шаблон подвала
│   │   │   ├── head.jade              # Шаблон с ресурсами, SEO и мета-тегами
│   │   │   ├── header.jade            # Шаблон шапки
│   │   │   ├── layout.jade            # Шаблон вывода
│   │   │   └── scripts.jade           # Шаблон со скриптами
│   │   └── index.jade                 # Шаблон страницы
│   └── favicon.ico                    # Иконка сайта
├── dist/                              # Сборка для заказчика
│   ├── images/                        # Папка изображений
│   ├── scripts/                       # Папка скриптов
│   ├── styles/                        # Папка стилей
│   └── index.html                     # Индексный файл
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
* `app/images/temp/` - папка для временного контента, например, для товаров, аватарок, обложек и т.п.
* `dist/` - сборка сайта для заказчика, по умолчанию её может не быть и можно не боясь её удалить, т.к. она генерируется каждый раз заново, при сборке всё её содержимое удаляется, поэтому руками в неё класть ничего не нужно, при необходимости в `Grunfiles.js` можно добавить в задачу с копированием определённые файлы.


## 2.4. Настройка Autoprefixer

Для автоматической подстановки префиксов используется [Autoprefixer](https://github.com/ai/autoprefixer), поэтому достаточно указать минимальные версии браузеров. При этом самим указывать префиксы в стилях, делать для них миксины или использовать готовые не нужно.

[Guntfile.js](https://github.com/CSSSR/csssr-project-template/blob/master/Gruntfile.js#L54-L69)

```javascript
autoprefixer: {
    options: {
        browsers: [
            'ie 9',
            'ff 27',
            'opera 12',
            'safari 6',
            'chrome 32',
            'android 4',
            'ios 5'
        ]
    },
    all: {
        src: ['dist/styles/**/*.css']
    }
},

```


## 2.5. Команды для запуска с Grunt

* `grunt` - очищается папка `dist/`, компилируются и копируются файлы в `dist/`, запускается сервер с доступом к сайту по адресу [`http://127.0.0.1:3000`](http://127.0.0.1:3000) и отслеживаются изменения файлов. Для выключения нажать `ctrl + c` или закрыть консоль.
* `grunt build` - очищается папка `dist/`, компилируются и копируются файлы в `dist/` только один раз.
* `grunt serve` - запускается сервер с доступом к сайту по адресу [`http://127.0.0.1:3000`](http://127.0.0.1:3000).

Перед коммитом обязательно сделать `grunt build`, чтобы папка очистилась от лишних файлов.

Проверить можно с помощью `grunt serve`.

## 2.6. Список страниц

Если на проекте страниц больше одной, то необходимо сделать список со страницами.

В качестве списка используется индексная страница `index.jade` (`index.html`).

Список страниц должен быть слегка оформлен:
* Логотип сайта.
* Ссылки по цветовой гамме сайта.
* Список и логотип должны быть отцентрированы.
* Стили должны быть встроены в страницу, подключать внешний стилевой файл или использовать стили сайта не нужно.
* Страница должна быть валидной и отображаться нормально на мобильных устройствах.


## 2.7. Jade - препроцессор HTML

На проекте используется шаблонизатор [Jade](http://jade-lang.com/) для компиляции в HTML.

Полезные ссылки для ознакомления:
* [jade-lang.com](http://jade-lang.com/) - документация Jade.
* [naltatis.github.io/jade-syntax-docs](http://naltatis.github.io/jade-syntax-docs/) - ещё одна документация Jade.
* [html2jade.org](http://html2jade.org/) - конвертация HTML в Jade и Jade в HTML.


## 2.7.1. Назначение папок

* `app/templates/` - здесь находятся все страницы для компиляции (например, `index.jade`).
* `app/templates/partials/` - папка шаблонов общих частиц, которые подключаются в страницы, чтобы не дублировать их в каждой.


## 2.7.2. Подключение частиц в страницы

* [`include header`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/partials/layout.jade#L6) - используется для подключения частиц страницы, например, для шапок и подвалов.
* [`extends partials/layout`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/index.jade#L1) - используется для внедрения контент в расширяемый шаблон. [`partials/layout.jade`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/partials/layout.jade).
* [`block content`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/index.jade#L6) - используется для добавления строк кода в определённое место [другого шаблона](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/partials/layout.jade#L7).

Во всех случаях через пробел указывается путь от текущего расположения до шаблона без расширения `.jade`.


## 2.7.3. Теги, классы и идентификаторы

- Классы и идентификаторы пишутся в начале, а не в атрибутах. Указывать тег `div` не нужно, т.к. он используется по умолчанию.
```jade
//- Плохо
div(class='carousel' id="carousel")
nav(class='nav nav_pos_left')
div(id="carousel")

//- Хорошо
.carousel
nav.nav.nav_pos_left
#carousel
```

- Идентификатор ставится после классов.
```jade
//- Плохо
.carousel#carousel.carousel_theme_dark
#carousel.carousel

//- Хорошо
.carousel.carousel_theme_dark#carousel
.carousel#carousel
```


## 2.7.4. Атрибуты элемента и их значения

- Для нескольких атрибутов запятая не нужна.
```jade
//- Плохо
input.input-text(type='text', name='project', value='csssr', required)

//- Хорошо
input.input-text(type='text' name='project' value='csssr' required)
```

- Используйте одинарные кавычки для текстовых значений.
```jade
//- Плохо
input.input-text(type="text" name="project" value="csssr" required)

//- Хорошо
input.input-text(type='text' name='project' value='csssr' required)
```

- Не давайте необязательные значения атрибутам.
```jade
//- Плохо
input.input-checkbox(type='checkbox' name='browser[]' value='chrome' checked='checked')

//- Хорошо
input.input-checkbox(type='checkbox' name='browser[]' value='chrome' checked)
```

- Распологайте одиночные атрибуты в последнюю очередь.
```jade
//- Плохо
input.input-checkbox(type='checkbox' checked name='browser[]' value='chrome')

//- Хорошо
input.input-checkbox(type='checkbox' name='browser[]' value='chrome' checked)
```

- Для числовых значений кавычки не нужны.
```jade
//- Плохо
input.input-text(type="text" name="price" value="24999")

//- Хорошо
input.input-text(type='text' name='price' value=24999)
```

- Переносите атрибуты новую строку, если их много и/или значения длинные.
```jade
//- Плохо
input.input-text(type='text' name='project' value='csssr' data-required='Это поле обязательно для заполнения!'  data-hint='Допустимы только символы латинского алфавита `[a-z-A-Z]` и числа `[0-9]`.' required)

//- Хорошо
input.input-text(
   type='text'
   name='project'
   value='csssr'
   data-required='Это поле обязательно для заполнения!'
   data-hint='Допустимы только символы латинского алфавита `[a-z-A-Z]` и числа `[0-9]`.'
   required
)
```

## 2.7.5. Переносы строк

- Добавляйте перенос строки для однотипных блоков с множественным вложением элементов. В лучшем случае используйте [миксин (mixin)](http://jade-lang.com/reference/#mixins).
```jade
//- Плохо
.project
   .project__name Lorem
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.
.project
   .project__name Ipsum.
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.

//- Хорошо
.project
   .project__name Lorem
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.

.project
   .project__name Ipsum.
   .project__desc
      | Lorem ipsum dolor sit amet, consectetur adipisicing elit.
      | Unde doloremque neque facilis sed repudiandae tempore ipsum provident officia eaque quas.
```

- Строчные элементы можно записывать на одной строке через двоеточие `:`.
```jade
//- Хорошо
ul.nav
   li.nav__item
      a.nav__item-link(href='/') Главная
   li.nav__item
      a.nav__item-link(href='/projects') Проекты
   li.nav__item
      a.nav__item-link(href='/contacts') Контакты

//- Лучше
ul.nav
   li.nav__item: a.nav__item-link(href='/') Главная
   li.nav__item: a.nav__item-link(href='/projects') Проекты
   li.nav__item: a.nav__item-link(href='/contacts') Контакты
```

## 2.7.6. Комментарии

- Комментарии в Jade, которые не должны попасть в HTML записываются через `//-`.
```jade
// Этот комментарий попадёт в HTML.

//- Этот комментарий не попадёт в HTML.
```

- Простые или условные комментарии можно записывать прямо в HTML-формате.
```html
<!--[if IE]>
meta(name='imagetoolbar' content='no')
meta(name='msthemecompatible' content='no')
<![endif]-->

<!--noindex-->
Это содержимое не будет индексироваться поисковиком.
<!--/noindex-->
```


## 2.7.7. Пиши меньше, делай больше или используйте mixin!

Для однотипных и повторяющихся строк кода имеет смысл сделать [миксин (mixin)](http://jade-lang.com/reference/#mixins) и указать только данные.
```html
mixin tools(list)
    ul.list
        each item in list
            li.list__item
                span.mark= item[0]
                = ' - ' + item[1]

+tools([
    ['spritesmith', 'генератор спрайтов и CSS переменных'],
    ['imagemin', 'сжатие картинок']
])
```

Скомпилирует

```html
<ul class="list">
    <li class="list__item">
        <span class="mark">spritesmith</span> - генератор спрайтов и CSS переменных
    </li>
    <li class="list__item">
        <span class="mark">imagemin</span> - сжатие картинок
    </li>
</ul>
```

## 2.7.8. Выделение активного пункта в меню навигации

Пример реализации можно посмотреть [здесь](https://github.com/CSSSR/sputnik/wiki/Jade:-Примеры#Активный-пункт-навигации).
