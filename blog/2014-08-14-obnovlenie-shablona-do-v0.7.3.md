# Шаблон обновился до v0.7.3

## Что нового?

### Комбинирование медиа-запросов

Добавлен обработчик CSS для комбинирование медиа-запросов [`grunt-combine-media-queries`](https://github.com/buildingblocks/grunt-combine-media-queries). Если в стилях находятся несколько секций с одним и тем же медиа-запросом, то они скомбинируются в одну, все медиазапросы помещаются в  конец файла.

### Примесь для спрайтов с Retina-картинками

Добавлена примесь (mixin) для спрайтов с Retina-картинками, находится в [`mixins.styl`](https://github.com/CSSSR/csssr-project-template/blob/master/app/styles/helpers/mixins.styl#L22). Картинки соответственно должны быть по размеру `x2`. В Stylus премись используется с названием `sprite2`.

Пример использования:
```stylus
.share
    // ...

    &-fb
        sprite2 $share-fb
    
    &-tw
        sprite2 $share-tw
    
    &-vk
        sprite2 $share-vk
```

### Layouts

Немного изменена структура в папке [`templates`](https://github.com/CSSSR/csssr-project-template/tree/master/app/templates), как можно заметить, добавилась папка
[`layouts`](https://github.com/CSSSR/csssr-project-template/tree/master/app/templates/layouts). Она предназначена для расширяемых шаблонов Jade - раскладок, в которых расположены все главные блоки по заданному порядку. Это удобно, когда у нас есть несколько уникальных страниц и можем переключать раскладки по необходимости.

По умолчанию используется [`layouts/default.jade`](https://github.com/CSSSR/csssr-project-template/blob/master/app/templates/layouts/default.jade).

## Заключение

Кроме всего этого в шаблоне были исправлены небольшие ошибки в конфигурации `Gruntfile.js`.
Хотелось ещё добавить [`grunt-html-inspector`](https://www.npmjs.org/package/grunt-html-inspector), но он не смог запуститься под Windows, причём зависимости были установлены, минус в том, что необходимо установить их глобально и прописывать в `PATH`. Можно ещё с этим поразбираться или поискать другой инструмент.

На этом всё.