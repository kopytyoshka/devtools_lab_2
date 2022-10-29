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
