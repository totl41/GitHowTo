# GitHowTo
Изучаю GIT

https://githowto.com/ru/

Git How To — это интерактивный тур, который познакомит вас с основами Git. Тур создан с пониманием того, что лучшим способом научиться чему-нибудь — сделать это своими руками. Кстати, если вы знаете английский и Ruby, вам может быть удобней пройти курс на Git Immersion

## 1. Финальные приготовления

**Установка имени и электронной почты**<br>
git config --global user.name "Your Name"<br>
git config --global user.email "your_email@whatever.com"<br>
**Имя ветки по умолчанию**<br>
git config --global init.defaultBranch main<br>
**Корректная обработка окончаний строк**<br>
Для пользователей Unix/Mac:<br>
git config --global core.autocrlf input<br>
git config --global core.safecrlf warn<br>
Для пользователей Windows:<br>
git config --global core.autocrlf true<br>
git config --global core.safecrlf warn<br>

## 2. Создание проекта

mkdir work<br>
cd work<br>
touch hello.html<br>
git init<br>
git add hello.html<br>
git commit -m "Initial Commit"<br>

## 3. Проверка состояния

**Проверьте состояние репозитория**<br>
git status<br>
git branch -m master main<br>

## 4. Внесение изменений

git status<br>

## 5. Индексация изменений

git add hello.html<br>
git status<br>

## 6. Индексация и коммит

git add a.html<br>
git add b.html<br>
git commit -m "Changes for a and b"<br>

git add c.html<br>
git commit -m "Unrelated change to c"<br>

## 7. Коммит изменений

**Сделайте коммит сейчас и проверьте состояние.**<br>
git commit<br>
**Проверьте состояние**<br>
git status<br>

## 8. Изменения, а не файлы

**Первое изменение: Добавьте стандартные теги страницы**<br>
**Добавьте это изменение**<br>
git add hello.html<br>
**Проверьте текущий статус**<br>
git status<br>
**Коммит**<br>
git commit -m "Added standard HTML page tags"<br>
git status<br>
**Добавьте второе изменение**<br>
git add .<br>
git status<br>
**Сделайте коммит второго изменения**<br>
git commit -m "Added HTML header"<br>

## 9. История

git log<br>
**01Однострочная история**<br>
git log --pretty=oneline<br>
**02Контроль отображения записей**<br>
git log --oneline --max-count=2<br>
git log --oneline --since="5 minutes ago"<br>
git log --oneline --until="5 minutes ago"<br>
git log --oneline --author="Your Name"<br>
git log --oneline --all<br>
**03Изощряемся**<br>
git log --all --pretty=format:"%h %cd %s (%an)" --since="7 days ago"<br>
**04Конечный формат лога**<br>
git log --pretty=format:"%h %ad | %s%d [%an]" --date=short<br>
git config --global format.pretty '%h %ad | %s%d [%an]'<br>
git config --global log.date short<br>

## 10. Получение старых версий

Научиться возвращать рабочую директорию к любому предыдущему состоянию.<br>
**01Получите хеши предыдущих коммитов**<br>
git log<br>
git checkout <hash><br>
cat hello.html<br>
**02Вернитесь к последней версии в ветке main**<br>
git switch main<br>
cat hello.html<br>

## 11. Создание тегов версий

**01Создайте тег первой версии**<br>
git tag v1<br>
git log<br>
**02Теги для предыдущих версий**<br>
git checkout v1^<br>
cat hello.html<br>
git tag v1-beta<br>
git log<br>
**03Переключение по имени тега**<br>
git checkout v1<br>
git checkout v1-beta<br>
**04Просмотр тегов с помощью команды tag**<br>
git tag<br>
**05Просмотр Тегов в логах**<br>
git log main --all<br>

## 12. Отмена локальных изменений (до индексации)

**01Переключитесь на ветку main**<br>
git switch main<br>
**02Измените hello.html**<br>
**03Проверьте состояние**<br>
git status<br>
**04Отмена изменений в рабочем каталоге**<br>
git restore hello.html<br>
git status<br>
cat hello.html<br>

## 13. Отмена проиндексированных изменений (перед коммитом)

**01Измените файл и проиндексируйте изменения**<br>
git add hello.html<br>
**02Проверьте состояние**<br>
git status<br>
**03Восстановление индекса**<br>
git restore --staged hello.html<br>
**04Восстановление рабочего каталога**<br>
git restore hello.html<br>
git status<br>

## 14. Отмена коммитов

**01Отмена коммитов**<br>
Иногда вы понимаете, что новые коммиты являются неверными, и хотите их отменить. Есть несколько способов решения этого вопроса, здесь мы будем использовать самый безопасный.<br>
Мы отменим коммит путем создания нового коммита, отменяющего нежелательные изменения.<br>
**02Измените файл и сделайте коммит**<br>
git add hello.html<br>
git commit -m "Oops, we didn't want this commit"<br>
**03Сделайте коммит с новыми изменениями, отменяющими предыдущие**<br>
git revert HEAD<br>
**04Проверьте лог**<br>
git log<br>

## 15. Удаление коммитов из ветки

**01Команда reset**<br>
**02Проверьте нашу историю**<br>
git log<br>
**03Для начала отметьте эту ветку**<br>
git tag oops<br>
**04Сброс к коммиту, предшествующему oops**<br>
git reset --hard v1<br>
git log<br>
**05Ничего никогда не теряется**<br>
git log --all<br>
**06Опасность сброса**<br>

## 16. Удаление тега oops

**01Удаление тега oops**<br>
git tag -d oops<br>
git log --all<br>

## 17. Внесение изменений в коммиты

**01Измените страницу, а затем сделайте коммит**<br>
git add hello.html<br>
git commit -m "Added copyright statement"<br>
git log<br>
**02Ой... необходим email**<br>
**03Измените предыдущий коммит**<br>
git add hello.html<br>
git commit --amend -m "Added copyright statement with email"<br>

## 18. Создание ветки

**01Создайте ветку**<br>
git switch -c style<br>
git status<br>

**02Добавьте файл стилей style.css**
touch style.css<br>
git add style.css<br>
git commit -m "Added css stylesheet"<br>

**03 Измените hello.html, чтобы он использовал style.css.**
git add hello.html<br>
git commit -m "Included stylesheet into hello.html"<br>

## 19. Переключение веток

**01Переключение на ветку main**<br>
git switch main<br>
cat hello.html<br>

**02Вернемся к ветке style**
git switch style<br>
cat hello.html<br>

## 19. Переключение веток

**01Переключение на ветку main**<br>
git switch main<br>
cat hello.html<br>
**02Вернемся к ветке style**<br>
git switch style<br>
cat hello.html<br>

## 20. Перемещение файлов

Научиться перемещать файлы в пределах репозитория.<br>
**01Просмотр истории изменений в конкретном файле**<br>
git log hello.html<br>
git log style.css<br>
**02Просмотр различий для конкретного файла**<br>
git show v1<br>
**03Переименуйте файл hello.html**<br>
mv hello.html index.html<br>
git status<br>
git add .<br>
git status<br>
**04Переместите style.css безопасным способом**<br>
mkdir css<br>
git mv style.css css/style.css<br>
git status<br>
git commit -m "Renamed hello.html; moved style.css"<br>
git log css/style.css<br>
git log --follow css/style.css<br>

## 21. Изменения в ветке main

Научиться работать с несколькими ветками с различными (и, возможно, конфликтующими) изменениями.<br>
**01Создайте файл README**<br>
**02Сделайте коммит файла README в ветку main**<br>
git switch main<br>
git add README<br>
git commit -m "Added README"<br>

## 22. Просмотр отличающихся веток

Научиться просматривать отличающиеся ветки в репозитории.<br>
**01Просмотрите текущие ветки**<br>
git log --all --graph<br>

## 23. Слияние

Научиться сливать две отличающиеся ветки для переноса изменений обратно в одну ветку.<br>
**01Слияние веток**<br>
git switch style<br>
git merge main<br>
git log --all --graph<br>

## 24. Создание конфликта

Создание конфликтующих изменений в ветке main.<br>
**01Вернитесь в main и создайте конфликт**<br>
git switch main<br>
git add hello.html<br>
git commit -m "Added meta title"<br>
**02Просмотр веток**<br>
git log --all --graph<br>

## 25. Разрешение конфликтов

Научиться разрешать конфликты во время слияния.<br>
**01Слияние main в ветку style**<br>
git switch style<br>
git merge main<br>
git status<br>
**02Отмена слияния**<br>
git merge --abort<br>
git status<br>
**03Решение конфликта**<br>
git merge main<br>
примем оба изменения<br>
**04Закоммитьте разрешенный конфликт**<br>
git add index.html<br>
git commit -m "Resolved merge conflict"<br>
git status<br>
git log --all --graphм

## 26. rebase против merge

## 27. Сброс ветки style

Сбросить ветку style до точки перед первым слиянием.<br>
**01Сбросьте ветку style**<br>
git switch style<br>
git log --graph<br>
Нужен коммит:"стиль коммит_3 перемещение и переименование"<br>
git reset --hard HEAD~2<br>
**02Проверьте ветку**<br>
В истории не должно быть коммитов слияния.<br>
git log --graph<br>

## 28. Перебазирование

Использовать команду rebase вместо команды merge.<br>
**01Перебазируем ветку style на ветку main**<br>
git switch style<br>
git rebase main<br>
git status<br>
**02Разрешение конфликта**<br>
git add .<br>
git rebase --continue<br>
git status<br>
git log --all --graph<br>

## 29. Слияние в ветку main

**01Слейте style в main**<br>
git switch main<br>
git merge style<br>
**02Просмотрите логи**<br>
git log --all --graph<br>

## 30. Клонирование репозиториев

**01Перейдите в директорию repositories**<br>
cd ..<br>
pwd<br>
ls<br>
**02Создайте клон репозитория work**<br>
git clone work home<br>
ls<br>

## 31. Просмотр клонированного репозитория

**01Посмотрите на клонированный репозиторий**<br>
cd home<br>
ls<br>
**02Просмотрите историю репозитория**<br>
git log --all<br>

## 32. Что такое origin?
Узнать об именах удаленных репозиториев.<br>
git remote<br>
git remote show origin<br>

## 33. Удаленные ветки

**00Список локальных веток**<br>
git branch<br>
**01Список удаленных веток**<br>
git branch -a<br>

## 34. Изменение оригинального репозитория

**01Внесите изменения в оригинальный репозиторий work**<br>
cd ../work<br>
Внесите следующие изменения в файл README<br>
git add README<br>
git commit -m "Changed README in original repo"<br>

## 35. Подтягивание изменений

Научиться подтягивать изменения из удаленного репозитория.<br>
cd ../home<br>
git fetch<br>
git log --all<br>
**01Проверьте README**<br>
cat README<br>

## 36. Слияние подтянутых изменений

**01Слейте подтянутые изменения в локальную ветку main**<br>
git merge origin/main<br>
cat README<br>
**03Команда pull (подтянуть)**<br>
git pull<br>
...эквивалентна следующим двум шагам:<br>
git fetch<br>
git merge origin/main<br>

## 37. Добавление ветки наблюдения

Научиться добавлять локальную ветку, которая отслеживает изменения удаленной ветки.<br>
**01Добавьте локальную ветку, которая отслеживает удаленную ветку**<br>
git branch --track style origin/style<br>
git branch -a<br>
git log --max-count=2<br>

## 38. Чистые репозитории

Научиться создавать чистые репозитории.<br>
**01Создайте чистый репозиторий**<br>
cd ..<br>
git clone --bare work work.git<br>
ls work.git<br>

## 39. Добавление удаленного репозитория

Добавить чистый репозиторий в качестве удаленного репозитория к нашему оригинальному репозиторию.<br>
cd work<br>
git remote add shared ../work.git<br>

## 40. Отправка изменений

Узнать, как передавать изменения в удаленный репозиторий.<br>
git switch main<br>
git add README<br>
git commit -m "Added shared comment to readme"<br>
Теперь отправьте изменения в общий репозиторий.<br>
git push shared main<br>

## 41. Подтягивание общих изменений

Научиться подтягивать изменения из общего репозитория.<br>
git remote add shared ../work.git<br>
git branch --track shared main<br>
git pull shared main<br>
cat README<br>

## 42. Размещение ваших Git-репозиториев

Научиться настраивать Git-сервер для совместного использования репозиториев.<br>
**01Запуск Git-сервера**<br>
# (From the "repositories" directory)<br>
git daemon --verbose --export-all --base-path=.<br>
Теперь в отдельном окне терминала перейдите в вашу директорию repositories:<br>
# (From the "repositories" directory)<br>
git clone git://localhost/work.git network_work<br>
cd network_work<br>
ls<br>
Вы увидите копию проекта work.<br>
**02Отправка изменений в Git Daemon**<br>
Если вы хотите разрешить отправку изменений (push) в репозиторий Git Daemon, добавьте метку --enable=receive-pack к команде git daemon. Будьте осторожны, этот сервер не производит аутентификацию, поэтому любой сможет отправлять изменения в ваш репозиторий.<br>
