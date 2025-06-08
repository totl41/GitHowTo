# GitHowTo
Изучаю GIT

https://githowto.com/ru/

Git How To — это интерактивный тур, который познакомит вас с основами Git. Тур создан с пониманием того, что лучшим способом научиться чему-нибудь — сделать это своими руками. Кстати, если вы знаете английский и Ruby, вам может быть удобней пройти курс на Git Immersion

## 1. Финальные приготовления

**Установка имени и электронной почты**
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
**Имя ветки по умолчанию**
git config --global init.defaultBranch main
**Корректная обработка окончаний строк**
Для пользователей Unix/Mac:
git config --global core.autocrlf input
git config --global core.safecrlf warn
Для пользователей Windows:
git config --global core.autocrlf true
git config --global core.safecrlf warn

## 2. Создание проекта

mkdir work
cd work
touch hello.html
git init
git add hello.html
git commit -m "Initial Commit"

## 3. Проверка состояния

**Проверьте состояние репозитория**
git status
git branch -m master main

## 4. Внесение изменений

git status

## 5. Индексация изменений

git add hello.html
git status

## 6. Индексация и коммит

git add a.html
git add b.html
git commit -m "Changes for a and b"

git add c.html
git commit -m "Unrelated change to c"

## 7. Коммит изменений

**Сделайте коммит сейчас и проверьте состояние.**
git commit
**Проверьте состояние**
git status

## 8. Изменения, а не файлы

**Первое изменение: Добавьте стандартные теги страницы**
**Добавьте это изменение**
git add hello.html
**Проверьте текущий статус**
git status
**Коммит**
git commit -m "Added standard HTML page tags"
git status
**Добавьте второе изменение**
git add .
git status
**Сделайте коммит второго изменения**
git commit -m "Added HTML header"

## 9. История

git log
**01Однострочная история**
git log --pretty=oneline
**02Контроль отображения записей**
git log --oneline --max-count=2
git log --oneline --since="5 minutes ago"
git log --oneline --until="5 minutes ago"
git log --oneline --author="Your Name"
git log --oneline --all
**03Изощряемся**
git log --all --pretty=format:"%h %cd %s (%an)" --since="7 days ago"
**04Конечный формат лога**
git log --pretty=format:"%h %ad | %s%d [%an]" --date=short
git config --global format.pretty '%h %ad | %s%d [%an]'
git config --global log.date short

## 10. Получение старых версий

Научиться возвращать рабочую директорию к любому предыдущему состоянию.
**01Получите хеши предыдущих коммитов**
git log
git checkout <hash>
cat hello.html
**02Вернитесь к последней версии в ветке main**
git switch main
cat hello.html

## 11. Создание тегов версий

**01Создайте тег первой версии**
git tag v1
git log
**02Теги для предыдущих версий**
git checkout v1^
cat hello.html
git tag v1-beta
git log
**03Переключение по имени тега**
git checkout v1
git checkout v1-beta
**04Просмотр тегов с помощью команды tag**
git tag
**05Просмотр Тегов в логах**
git log main --all

## 12. Отмена локальных изменений (до индексации)

**01Переключитесь на ветку main**
git switch main
**02Измените hello.html**
**03Проверьте состояние**
git status
**04Отмена изменений в рабочем каталоге**
git restore hello.html
git status
cat hello.html

## 13. Отмена проиндексированных изменений (перед коммитом)

**01Измените файл и проиндексируйте изменения**
git add hello.html
**02Проверьте состояние**
git status
**03Восстановление индекса**
git restore --staged hello.html
**04Восстановление рабочего каталога**
git restore hello.html
git status

## 14. Отмена коммитов

**01Отмена коммитов**
Иногда вы понимаете, что новые коммиты являются неверными, и хотите их отменить. Есть несколько способов решения этого вопроса, здесь мы будем использовать самый безопасный.
Мы отменим коммит путем создания нового коммита, отменяющего нежелательные изменения.
**02Измените файл и сделайте коммит**
git add hello.html
git commit -m "Oops, we didn't want this commit"
**03Сделайте коммит с новыми изменениями, отменяющими предыдущие**
git revert HEAD
**04Проверьте лог**
git log

## 15. Удаление коммитов из ветки

**01Команда reset**
**02Проверьте нашу историю**
git log
**03Для начала отметьте эту ветку**
git tag oops
**04Сброс к коммиту, предшествующему oops**
git reset --hard v1
git log
**05Ничего никогда не теряется**
git log --all
**06Опасность сброса**

## 16. Удаление тега oops

**01Удаление тега oops**
git tag -d oops
git log --all

## 17. Внесение изменений в коммиты

**01Измените страницу, а затем сделайте коммит**
git add hello.html
git commit -m "Added copyright statement"
git log
**02Ой... необходим email**
**03Измените предыдущий коммит**
git add hello.html
git commit --amend -m "Added copyright statement with email"

## 18. Создание ветки

**01Создайте ветку**
git switch -c style
git status

**02Добавьте файл стилей style.css**
touch style.css
git add style.css
git commit -m "Added css stylesheet"

**03 Измените hello.html, чтобы он использовал style.css.**
git add hello.html
git commit -m "Included stylesheet into hello.html"

## 19. Переключение веток

**01Переключение на ветку main**
git switch main
cat hello.html

**02Вернемся к ветке style**
git switch style
cat hello.html

## 19. Переключение веток

**01Переключение на ветку main**
git switch main
cat hello.html
**02Вернемся к ветке style**
git switch style
cat hello.html

## 20. Перемещение файлов

Научиться перемещать файлы в пределах репозитория.
**01Просмотр истории изменений в конкретном файле**
git log hello.html
git log style.css
**02Просмотр различий для конкретного файла**
git show v1
**03Переименуйте файл hello.html**
mv hello.html index.html
git status
git add .
git status
**04Переместите style.css безопасным способом**
mkdir css
git mv style.css css/style.css
git status
git commit -m "Renamed hello.html; moved style.css"
git log css/style.css
git log --follow css/style.css

## 21. Изменения в ветке main

Научиться работать с несколькими ветками с различными (и, возможно, конфликтующими) изменениями.
**01Создайте файл README**
**02Сделайте коммит файла README в ветку main**
git switch main
git add README
git commit -m "Added README"

## 22. Просмотр отличающихся веток

Научиться просматривать отличающиеся ветки в репозитории.
**01Просмотрите текущие ветки**
git log --all --graph

## 23. Слияние

Научиться сливать две отличающиеся ветки для переноса изменений обратно в одну ветку.
**01Слияние веток**
git switch style
git merge main
git log --all --graph

## 24. Создание конфликта

Создание конфликтующих изменений в ветке main.
**01Вернитесь в main и создайте конфликт**
git switch main
git add hello.html
git commit -m "Added meta title"
**02Просмотр веток**
git log --all --graph

## 25. Разрешение конфликтов

Научиться разрешать конфликты во время слияния.
**01Слияние main в ветку style**
git switch style
git merge main
git status
**02Отмена слияния**
git merge --abort
git status
**03Решение конфликта**
git merge main
примем оба изменения
**04Закоммитьте разрешенный конфликт**
git add index.html
git commit -m "Resolved merge conflict"
git status
git log --all --graph

## 26. rebase против merge

## 27. Сброс ветки style

Сбросить ветку style до точки перед первым слиянием.
**01Сбросьте ветку style**
git switch style
git log --graph
Нужен коммит:"стиль коммит_3 перемещение и переименование"
git reset --hard HEAD~2
**02Проверьте ветку**
В истории не должно быть коммитов слияния.
git log --graph

## 28. Перебазирование
Использовать команду rebase вместо команды merge.

**01Перебазируем ветку style на ветку main**
git switch style
git rebase main
git status
**02Разрешение конфликта**
git add .
git rebase --continue
git status
git log --all --graph

## 29. Слияние в ветку main

**01Слейте style в main**
git switch main
git merge style
**02Просмотрите логи**
git log --all --graph

## 30. Клонирование репозиториев

**01Перейдите в директорию repositories**
cd ..
pwd
ls
**02Создайте клон репозитория work**
git clone work home
ls

## 31. Просмотр клонированного репозитория

**01Посмотрите на клонированный репозиторий**
cd home
ls
**02Просмотрите историю репозитория**
git log --all

## 32. Что такое origin?
Узнать об именах удаленных репозиториев.
git remote
git remote show origin

## 33. Удаленные ветки

**00Список локальных веток**
git branch
**01Список удаленных веток**
git branch -a

## 34. Изменение оригинального репозитория

**01Внесите изменения в оригинальный репозиторий work**
cd ../work
Внесите следующие изменения в файл README
git add README
git commit -m "Changed README in original repo"

## 35. Подтягивание изменений

Научиться подтягивать изменения из удаленного репозитория.
cd ../home
git fetch
git log --all
**01Проверьте README**
cat README

## 36. Слияние подтянутых изменений

**01Слейте подтянутые изменения в локальную ветку main**
git merge origin/main
cat README
**03Команда pull (подтянуть)**
git pull
...эквивалентна следующим двум шагам:
git fetch
git merge origin/main

## 37. Добавление ветки наблюдения

Научиться добавлять локальную ветку, которая отслеживает изменения удаленной ветки.
**01Добавьте локальную ветку, которая отслеживает удаленную ветку**
git branch --track style origin/style
git branch -a
git log --max-count=2

## 38. Чистые репозитории

Научиться создавать чистые репозитории.
**01Создайте чистый репозиторий**
cd ..
git clone --bare work work.git
ls work.git

## 39. Добавление удаленного репозитория

Добавить чистый репозиторий в качестве удаленного репозитория к нашему оригинальному репозиторию.
cd work
git remote add shared ../work.git

## 40. Отправка изменений

Узнать, как передавать изменения в удаленный репозиторий.
git switch main
git add README
git commit -m "Added shared comment to readme"
Теперь отправьте изменения в общий репозиторий.
git push shared main

## 41. Подтягивание общих изменений

Научиться подтягивать изменения из общего репозитория.
git remote add shared ../work.git
git branch --track shared main
git pull shared main
cat README

## 42. Размещение ваших Git-репозиториев

Научиться настраивать Git-сервер для совместного использования репозиториев.
**01Запуск Git-сервера**
# (From the "repositories" directory)
git daemon --verbose --export-all --base-path=.
Теперь в отдельном окне терминала перейдите в вашу директорию repositories:
# (From the "repositories" directory)
git clone git://localhost/work.git network_work
cd network_work
ls
Вы увидите копию проекта work.
**02Отправка изменений в Git Daemon**
Если вы хотите разрешить отправку изменений (push) в репозиторий Git Daemon, добавьте метку --enable=receive-pack к команде git daemon. Будьте осторожны, этот сервер не производит аутентификацию, поэтому любой сможет отправлять изменения в ваш репозиторий.
