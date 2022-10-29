# 1 задание
Запустите локальный веб-визуализатор репозитория.

    git instaweb
делайте так, чтобы в нём отображалось нормальное описание репозитория.

![avatar](/images/task-t.jpg)

Изменили описание с помощью команды

    nano .git/description

# 2 задание
Перенесите все коммиты, находящиеся в ветке ci, в ветку master.


Переходим в ветку ci

    git checkout ci

Вывод коммитов, которые необходимо объединить

    git rebase -i HEAD~2

меняем pick на squash(2)

открывается окно в котором мы пишем комментарий к коммиту и стираем ненужное


    git rebase master 
    git checkout master 
    git merge ci 
    git branch -d ci 

![avatar](/images/task-2.1.jpg)
![avatar](/images/task-2.2.jpg)

# 3 задание

В репозитории есть несколько альтернативных историй проекта, недоступных из текущей версии графа. Найдите последний коммит любой из версий

    git reflog

    git checkout HEAD@{99}

![avatar](/images/task-3.1.jpg)

Создаём на нём ветку old-master.

    git branch old-master HEAD
    git checkout master 


![avatar](/images/task-3.2.jpg)

# 4 задание
Определите коммит, в котором строчка 32 файла prisma/seed.ts изменялась в последний раз, и его дату.

    git blame -L 32,32 prisma/seed.ts

![avatar](/images/task-4.jpg)

# 5 задание
В проекте существует регресс, на который имеется тест, запускающийся по команде npm run test. Найдите коммит, в котором проявился регресс.

    git bisect start 

В данном задании наибольшую трудность вызвало обновление nodejs до 12 версии и запуск тестов, чтобы всё не обваливалось

Далее указываем хороший и плохой коммит

    git bisect bad <hash-commit>
    git bisect good <hash-commit>

После запускаем тест

    npm run test 

![avatar](/images/task-5.1.jpg)

Тест не упал, пишем в консолль:

    git bisect good 

после опять запускаем тест

Если тест упал пишем:

    git bisect bad 

![avatar](/images/task-5.3.jpg)


# 6 задание

В репозитории существует файл .env, содержащий конфиденциальную информацию. Удалите его из всех коммитов, где он присутствует.

    git filter-branch --tree-filter "rm -f .env" -- --all

И добавьте в .gitignore

    vim .gitignore 

![avatar](/images/task-6.1.jpg)
![avatar](/images/task-6.jpg)

# 7 задание

Сделайте так, чтобы автором коммитов в ветке feature были Вы. Для этого укажите в изменяемых коммитах почту, привязанную к GitHub, и своё ФИО.

    git gilter-branch --env-filter '
    GIT_AUTHOR_NAME=kopytyoshka
    GIT_AUTHOR_EMAIL=ilyatttt19@gmail.com
    ' fd00db2^..feature 

![avatar](/images/task-7.jpg)


# 8 задание
Включите запоминание разрешений конфликтов. Влейте ветку `feature` в `master`, разрешив конфликт при слиянии. Откатите слияние, внесите изменение в файл `README.md` и снова влейте ветку `feature` в `master` без ручного разрешения конфликта.

    git config --global rerere.enable true

Cливаем ветки

    git merge feature

После открываем README.md

    nano README.md 

Редактируем его и добавляем отслеживание, коммитим и отменяем коммит

![avatar](/images/task-8.1.jpg)

# 9 задание
Проверьте целостность репозитория и убедитесь, что с ним всё в порядке. При наличии ошибок исправьте их.

    git fsck 

![avatar](/images/task-9.jpg)
