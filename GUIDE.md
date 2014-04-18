## Коротко о главном

В наших проектах мы используем автоматизированные инструменты для облегчения разработки сайтов - Grunt c препроцессорами Jade и Stylus (и др.), систему конроля версий - Git, код и хостинг сайта разворачиваются на GitHub.
А чтобы код был удобен и понятен любому, мы придерживаемся стандарту.


## 1. Git - система контроля версий
![git](http://git-scm.com/images/logo@2x.png)
### 1.1. Установка
Если у Вас OS X - в консоли набрать `$ sudo port install git-core +doc +bash_completion +gitweb`.

Если у Вас Windows - рекомендуется [git v1.8.4](http://msysgit.googlecode.com/files/Git-1.8.4-preview20130916.exe).

### 1.2. Настройка
Чтобы было удобней работать, можно настроить алиасы для коротких команд.

**Для пользователей OS X.**

1. В консоли набрать `nano ~/.bash_profile`.
2. Добавить нужные строки.
3.  Ctrl+X  — Выйти.<br>
    Y       — Сохранить.<br>
    [Enter] — Да, заменить.


**Для пользователей Windows.**

Алиасы находятся в файле `.profile` в папке профиля `c:\users\<profile>\`, где `<profile>` - имя Вашего профиля, если такого файла нет, то его нужно создать.

**Список коротких команд:**
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

Данные алиасы не являются обязательными, настроить их можно так, как вам удобно.

После создания/изменения алиасов необходимо закрыть консоль и открыть заново, чтобы алиасы были доступны.


### 1.3. Работа с Git
Для новичков рекомендуется пройти небольшой обучающийся курс [Git How To](http://githowto.com/ru).

В основном нам понадобятся такие команды, как:
* `git clone <url> [path]` - клонирование репозитория, где `<url>` - адрес репозитория, а `[path]` - путь, в который будут заливаться файлы, можно не указывать и в текущей папке создастся новая папка с названием репозитория.
* `git checkout` или `go` - переключение по веткам.
* `git checkout -b new-branch` или `gob` - создание новой ветки `new-branch`.
* `git status` или `gs` - проверка текущего состояния файлов.
* `git add --all` или `gall` - добавление всех файлов с учётом удалённых.
* `git pull` или `gpl` - скачивание обновлений с удалённого репозитория.
* `git commit -m 'Comment.'` или `gc 'Comment.'` - коммит с комментарием
* `git push origin master` или `gpm` - заливка файлов в ветку `master`.

Для того, чтобы можно было посмотреть сайт, нужно залить код в ветку `gh-pages`. После того, как залили, сайт будет доступен по такому адресу: `https://csssr.github.io/<repository>/`, где `<repository>` - название репозитория.

Заливать очень просто: `git push origin gh-pages`.

При использовании [шаблона](https://github.com/CSSSR/csssr-project-template) используется алиас `gh` для автоматического обновления ветки и заливки.
Подробнее можно почитать [здесь](https://github.com/CSSSR/sputnik/wiki/git#beta-Автоматическое-обновление-ветки-gh-pages-и-отправка-в-репозиторий).

**Важно!** После первой заливки нужно подождать примерно 10 минут, чтобы сайт обновился и был доступен по соответсвующей ссылке. Последующие заливки почти мгновенны. Текущий статус и работоспособность GitHub можно посмотреть здесь: https://status.github.com/


## 2. Grunt


## 3. Стандарты

