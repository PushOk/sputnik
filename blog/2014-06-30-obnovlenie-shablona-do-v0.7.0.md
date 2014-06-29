# Шаблон обновился до v0.7.0

![csssr-update](https://cloud.githubusercontent.com/assets/6207143/3424590/ad46a64e-ffd7-11e3-9046-cd77316c123f.png)


## Что нового?

### CSSCOMB

![csscomb](https://cloud.githubusercontent.com/assets/6207143/3424643/a40b1c60-ffda-11e3-87f0-4ef71bd8bfb0.png)

Добавлена утилита [`grunt-csscomb`](https://www.npmjs.org/package/grunt-csscomb) для сортировки CSS-свойств в рамках каждого селектора по заданному порядку. Конфиг и порядок свойств можно посмотреть в файле [`.csscomb.json`](https://github.com/CSSSR/csssr-project-template/blob/137bddbd6d12cab9102bc3607685cb70492047ac/.csscomb.json).

До этого пользовались утилитой [`grunt-cssbeautifier`](https://www.npmjs.org/package/grunt-cssbeautifier), но она не позволяла сортировать свойства.

### Поддержка браузеров

![browsers](https://cloud.githubusercontent.com/assets/2854701/3424295/3e6f0ddc-ffc9-11e3-88fa-4495f9151bad.jpg)

Список версий поддерживаемых браузеров теперь хранится в [`package.json`](https://github.com/CSSSR/csssr-project-template/blob/137bddbd6d12cab9102bc3607685cb70492047ac/package.json#L55-L63), откуда подхаватывает [`grunt-autoprefixer`](https://www.npmjs.org/package/grunt-autoprefixer) и ***фирменная заглушка*** для неподдерживаемых браузеров. Стоит отметить, что для подстановки версий в заглушку используется [`grunt-replace`](https://www.npmjs.org/package/grunt-replace), который заменяет паттерн в JavaScript-файлах (и не только) на заданные значения.

### Анти-кэш или версионность ресурсов

![cache](https://cloud.githubusercontent.com/assets/6207143/3424648/06e50a30-ffdb-11e3-9752-70e95622c8b0.png)

Все подключаемые ресурсы в html-файлах теперь находятся в папке `assets/x.x.x`, где `x.x.x` — это номер версии, подхватывающийся из [`package.json`](https://github.com/CSSSR/csssr-project-template/blob/137bddbd6d12cab9102bc3607685cb70492047ac/package.json#L3). После обновления версии путь до ресурсов изменится, и браузеры уже не будут брать старые файлы из кэша.

Для обновления версии проекта используется [`grunt-bump`](https://www.npmjs.org/package/grunt-bump), который обновляет версию в `package.json`.

Список доступных команд для обновления версий:

Команда | Назначение
--- | ---
`grunt bump` / `grunt bump:patch` | Патч версия: 0.0.x.
`grunt bump:minor` | Минорная версия: 0.x.0.
`grunt bump:major` | Мажорная версия: x.0.0.

Попозже определимся, каким образом будет вестись версионность, хотя она вполне очевидна.

## TODO

На подходе добавление таких утилит:
- [`grunt-combine-media-queries`](https://github.com/buildingblocks/grunt-combine-media-queries) — комбинация всех медиа-запросов;
- [`grunt-uncss`](https://github.com/addyosmani/grunt-uncss) — удаление лишних и не используемых стилей;
- [`grunt-html-inspector`](https://www.npmjs.org/package/grunt-html-inspector) — инспектор HTML, проверит ваши страницы и напишет, что следовало бы исправить.

Предложения по улучшению шаблона приветствуются.

## Заключение

Мы постоянно улучшаем наш шаблон, делая разработку удобнее. В ближайшее время будет очередное обновление.

Уже идёт работа над зеркальной версией сборщика на **Gulp**. Главное отличие от Grunt в том, что в Grunt используется конфиг, а Gulp — API. Сам Gulp работает намного быстрее, чем Grunt.

В соответствии с обновлённым шаблоном в ближайшее время обновится гид, в котором будет подробно описано, как работать с новыми фишками.
