# Инструкция для работы с Git и удалёнными репозиториями


## Что такое Git? <a name="1"></a>
![что такое Git?](1.jpeg)

Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.

## Подготовка репозитория

Репозиторий — каталог файловой системы, в котором могут находиться файлы журналов конфигураций и операций, выполняемых над репозиторием, а также сами контролируемые файлы. [Подробнее смотри здесь](https://wiki.miem.hse.ru/docs/miem-digital/git/basic-concepts)

### просмотр состояния репозитория 

>__git status__

Для создание репозитория необходимо выполнить команду *git init*  в папке с репозиторием и у Вас создаться репозиторий (появится скрытая папка .git)

## Создание коммитов

### Git add
Для добавления измений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите *git add <имя файла>*

### Просмотр состояния репозитория
Для того, чтобы посмотреть состояние репозитория используется команда *git status*. Для этого необходимо в папке с репозиторием написать *git status*, и Вы увидите были ли измения в файлах, или их не было.

### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду *git commit*. Выполняется она так: *git commit -m "<сообщение к коммиту>*. Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

[Подробнее здесь](https://ru.stackoverflow.com/tags/git-commit/info)

## Перемещение между сохранениями
Для того, чтобы перемещаться между коммитами, используется команда *git checkout*. Используется она в папке с репозиторием следующим образом: *git checkout <номер коммита>*

## Журнал изменений
Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда *git log*. Для этого достаточно выполнить команду *git log* в папке с репозиторием

## Ветки в Git <a name="4"></a>

![Ветки в Git](2.jpg)

### Создание ветки

Для того, чтобы создать ветку, используется команда *git branch*. Делается это следующим образом в папке с репозиторием: *git branch <название новой ветки>*

### Переключиться на ветку можно следующей командой:

git checkout <имя ветки>

## Слияние веток

Для того чтобы дабавить ветку в текущую ветку используется команда *git merge <name branch>*

## Удаление веток
Для удаления ветки ввести команду "git branch -d 'name branch'"

[Подробнее о работе с ветками в Git](https://habr.com/ru/post/342116/?ysclid=l872ijg8rw170965301)

## Работа с удаленными репозиториями 

>**Репозиторий — каталог файловой системы, в котором могут находиться файлы журналов конфигураций и операций, выполняемых над репозиторием, а также сами контролируемые файлы.**

Помимо локальных репозиториев, в Git могут применяться и удаленные. 

## Работа с удалёнными репозиториями


Чтобы иметь возможность совместной работы над каким-либо Git-проектом, необходимо знать, как управлять удалёнными репозиториями. Удалённые репозитории — это модификации проекта, которые хранятся в интернете или ещё где-то в сети. Их может быть несколько, каждый из которых, как правило, доступен для вас либо только на чтение, либо на чтение и запись. Совместная работа включает в себя управление удалёнными репозиториями и помещение **(push)** и получение **(pull)** данных в и из них тогда, когда нужно обменяться результатами работы.

### Отображение удалённых репозиториев
Чтобы просмотреть, какие удалённые серверы у вас уже настроены, следует выполнить команду **git remote**. Она перечисляет список имён-сокращений для всех уже указанных удалённых дескрипторов. 

### Разница между fetch и pull.

Fetch и Pull

Как вы только что узнали, для получения данных из удалённых проектов, следует выполнить:

**git fetch [имя удал. сервера]**

Данная команда связывается с указанным удалённым проектом и забирает все те данные проекта, которых у вас ещё нет. После того как вы выполнили команду, у вас должны появиться ссылки на все ветки из этого удалённого проекта. Теперь эти ветки в любой момент могут быть просмотрены или слиты (объединены).

Когда вы клонируете репозиторий, команда **clone** автоматически добавляет этот удалённый репозиторий под именем **origin**. Таким образом, **git fetch origin** извлекает все наработки, отправленные (**push**) на этот сервер после того, как вы склонировали его (или получили изменения с помощью **fetch**). Важно отметить, что команда **fetch** забирает данные в ваш локальный репозиторий, но не сливает (не объединяет) их с какими-либо вашими наработками и не модифицирует то, над чем вы работаете в данный момент. Вам необходимо вручную слить эти данные с вашими, когда вы будете готовы.

Если у вас есть ветка, настроенная на отслеживание удалённой ветки, то вы можете использовать команду **git pull**. Она автоматически извлекает и затем сливает (объединяет) данные из удалённой ветки в вашу текущую ветку. Этот способ может для вас оказаться более простым или более удобным. К тому же по умолчанию команда **git clone** автоматически настраивает вашу локальную ветку *master* на отслеживание удалённой ветки *master* на сервере, с которого вы клонировали (подразумевается, что на удалённом сервере есть ветка *master*). Выполнение **git pull**, как правило, извлекает (**fetch**) данные с сервера, с которого вы изначально склонировали, и автоматически пытается слить (объеденить) (**merge**) их с кодом, над которым вы в данный момент работаете.

## **Push**

Когда вы хотите поделиться своими наработками, вам необходимо отправить (**push**) их в главный репозиторий. Команда для этого действия простая: **git push [удал. сервер] [ветка]**. Чтобы отправить вашу ветку master на сервер **origin**(повторимся, что клонирование, как правило, настраивает оба этих имени автоматически), вы можете выполнить следующую команду для отправки наработок на сервер:

**git push origin master**

Эта команда срабатывает только в случае, если вы клонировали с сервера, на котором у вас есть права на запись, и если никто другой с тех пор не выполнял команду **push**. Если вы и кто-то ещё одновременно клонируете, затем он выполняет команду push, а затем команду push выполняете вы, то ваш push точно будет отклонён. Вам придётся сначала вытянуть (**pull**) их изменения и объединить с вашими. Только после этого вам будет позволено выполнить **push**.
