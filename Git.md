## 1. Git - система контроля версий
![git](http://git-scm.com/images/logo@2x.png)


### 1.1. Установка
Если у Вас OS X - в консоли набрать `$ sudo port install git-core +doc +bash_completion +gitweb`.

Если у Вас Windows - [git v1.9.4](http://msysgit.github.io/).



### 1.2. Настройка
Чтобы было удобней работать, можно настроить алиасы для коротких команд.

**Для пользователей OS X.**

1. В консоли набрать `nano ~/.bash_profile`.
2. Добавить нужные строки.
3.  Ctrl+X  — Выйти.<br>
    Y       — Сохранить.<br>
    [Enter] — Да, заменить.


**Для пользователей Windows.**

Алиасы находятся в файле [`.profile`](https://gist.githubusercontent.com/GC92/ad648218634f9491a5b9/raw/45704ea0b51aeb12be5930374964ff17f0290afd/.profile).

в папке профиля `c:\users\<profile>\`, где `<profile>` - имя Вашего профиля, если такого файла нет, то его нужно создать.

[**Список коротких команд:**](https://gist.github.com/GC92/ad648218634f9491a5b9)
```php
# Отображение текущего состояния.
alias gs='git status '

# Отображение коммитов с коротким названием, датой, комментарием и автором.
alias gl='git --no-pager log --pretty=format:"%h | %ad | %s%d [%an]" --graph --date=short'
alias glo=gl
alias glog=gl

# Добавление вех файлов без учёта удалённых и отображение текущего состояния.
alias ga='git add . && git status'
alias gad=ga
alias gadd=ga

# Добавление всех файлов с учётом удалённых и отображение текущего состояния.
alias gall='git add --all && git status'
alias gal=gall

# Отображает текущую ветку среди всех имеющихся.
alias gb='git branch '

# Коммит с комментарием.
# Пример: gc 'Fixed bug.'
alias gc='git commit -m '

# Заливка в ветку master.
alias gpm='git push origin master'

# Заливка в ветку gh-pages.
alias gpgh='git push origin gh-pages'

# Переключение по веткам.
# Пример: go master
alias go='git checkout '

# Создание новой ветки.
# Пример: gob new-branch
alias gob='git checkout -b '

# Автоматическое обновление ветки gh-pages и отправка в репозиторий.
# Подробнее можно почитать здесь: https://github.com/CSSSR/sputnik/wiki/git
alias gh='git checkout gh-pages && git checkout master -- .gitignore && rm -rf `ls | grep -v node_modules` && git checkout master -- public && mv public/* . && rm -rf public && git add --all && git status && git commit -m Updated. && git push origin gh-pages -f && git checkout master'

# Дополнительные алисы на случай опечатки.
alias got='git '
alias get='git '

```

Если на проекте основная ветка `master` и нужно заливать для просмотра на `gh-pages`, то можно воспользоваться [самописной функцией баша `gh-pages`](https://gist.github.com/GC92/a9697bb8deab65431249), положите файл [`.bashrc`](https://gist.githubusercontent.com/GC92/a9697bb8deab65431249/raw/0430d79df2d72b5d2ec42f5d9a9e76bcf290d18f/.bashrc) в папку профиля.

```php
# Заливка файлов в ветку gh-pages из произвольной папки и ветки
# Команда: gh-pages <branch> <path/to/folder>
# Пример: gh-pages master dist
gh-pages() {
	if [[ $1 && $2 ]]; then
		git checkout gh-pages
		git checkout $1 -- .gitignore
		rm -rf `ls | grep -v node_modules`
		git checkout $1 -- $2
		mv $2/* .
		rm -rf $2
		git add --all
		git status
		git commit -m Updated.
		git push origin gh-pages
		git checkout $1
	fi
}

```

Перед использованием команды, убедитесь, чтов репозитории есть ветка `gh-pages`, если её нет, то необходимо создать:
```
git checkout -b gh-pages`
```

Если мы наберём `gh-pages master dist`:

* `git checkout gh-pages` - переключаемся в ветку gh-pages.
* `git checkout master -- .gitignore` - копируем файл `.gitignore`.
* `` rm -rf `ls | grep -v node_modules` `` - предварительно очищаем ветку.
* `git checkout master -- dist` - копируем папку `public` из ветки `master`.
* `mv dist/* .` - перемещаем всё из папки `dist` в корень.
* `rm -rf dist` - удаляем папку `dist`.
* `git add --all` - индексируем всё.
* `git status` - отображаем изменения.
* `git commit -m Updated.` - коммитим с комментом `Updated.`.
* `git push origin gh-pages -f` - заливаем в репозиторий принудительно.
* `git checkout master` - возвращаемся в ветку `master`.

После выполнения данной функции ветка `gh-pages` автоматически обновится и зальётся на GitHub.

Данные алиасы не являются обязательными, настроить их можно так, как вам удобно.

После создания/изменения алиасов необходимо закрыть консоль и открыть заново, чтобы алиасы были доступны.



### 1.3. Работа с Git
Для новичков рекомендуется пройти небольшой обучающийся курс [Git How To](http://githowto.com/ru).

В основном нам понадобятся такие команды, как:
* `git clone <url> [path]` - клонирование репозитория, где `<url>` - адрес репозитория, а `[path]` - путь, в который будут заливаться файлы, можно не указывать и в текущей папке создастся новая папка с названием репозитория.
* `git pull origin <branch>` или `gplo <branch>` - скачивание обновлений с удалённого репозитория.
* `git checkout <branch>` или `go <branch>` - переключение по веткам.
* `git checkout -b new-branch` или `gob new-branch` - создание новой ветки `new-branch`.
* `git add --all` или `ga` - добавление всех файлов с учётом удалённых.
* `git status` или `gs` - проверка текущего состояния файлов.
* `git commit -m 'Comment.'` или `gc 'Comment.'` - коммит с комментарием
* `git push origin <branch>` или `gpo <branch>` - заливка файлов в произвольную ветку.

Для того, чтобы можно было посмотреть сайт, нужно залить код в ветку `gh-pages`. После того, как залили, сайт будет доступен по такому адресу: `https://csssr.github.io/<repository>/`, где `<repository>` - название репозитория.

Заливать очень просто: `git push origin gh-pages`.

При использовании [шаблона](https://github.com/CSSSR/csssr-project-template) можно использовать функцию `gh-pages` для автоматического обновления ветки и заливки (см. в пункте 1.2).

**Важно!** После первой заливки нужно подождать примерно 10 минут, чтобы сайт обновился и был доступен по соответсвующей ссылке. Последующие заливки почти мгновенны. Текущий статус и работоспособность GitHub можно посмотреть здесь: https://status.github.com/



## 1.4. Полезные ссылки


### 1.4.1. Разбираемся с Git
* [Git How To](http://githowto.com/ru) — это интерактивный тур, который познакомит вас с основами Git. Тур создан с пониманием того, что лучшим способом научиться чему-нибудь — сделать это своими руками.
* [Команды git](http://git-scm.com/book/commands) - полный список команд на официальном сайте
* [git - the simple guide](http://rogerdudler.github.io/git-guide/)
* [Ежедневная работа с Git](http://habrahabr.ru/post/174467/) - статья на Хабре
* [Что нам стоит Git настроить!](http://habrahabr.ru/post/164297/) - статья на Хабре



### 1.4.2. Видео
* [Git & GitHub Tutorials](https://www.youtube.com/playlist?list=PLEACDDE80A79CE8E7)



### 1.4.3. Книги
* [Pro Git](http://git-scm.com/book/ru) - официальная книга Git
* [Магия Git](http://dl.dropboxusercontent.com/u/281916/delete/book.pdf)
