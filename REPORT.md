# 1 задание
Запустите локальный веб-визуализатор репозитория.

    git instaweb
делайте так, чтобы в нём отображалось нормальное описание репозитория.

![avatar](/images/task-1.png)

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
