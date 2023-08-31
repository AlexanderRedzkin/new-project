### Работа с GIT 
📌Настройка Git

Работа с файлом настройки .gitconfig
Сейчас вы работаете в одиночку, но в дальнейшем вам может понадобиться использовать Git в команде. Чтобы участникам проекта было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя и адрес электронной почты.

Вы можете указать любую электронную почту и любое имя. Сделать это можно с помощью команды git config (от англ. configuration — «конфигурация», «настройка») с ключом --global (англ. «глобальный»). При этом не имеет значения, в какой директории вы находитесь прямо сейчас: вызов git config --global сработает везде.

В качестве значения user.name нужно указать своё имя или никнейм. Для настройки параметра user.email указывают электронную почту.

'''BASH
 $ git config --global user.name "User Namovich" 
%% имя или ник нужно написать латиницей и в кавычках

$ git config --global user.email username@yandex.ru
%%  здесь нужно указать свой настоящий email
'''

Все глобальные настройки Git хранит в файле .gitconfig в домашней директории. 
Команда запишет в этот файл указанные имя и почту. 

Чтобы убедиться в этом, можно вызвать команду для чтения файлов.
'''BASH
$ cat ~/.gitconfig  или $ git config --list 
'''

📌Шпаргалка. Базовые команды в консоли

Навигация

pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;

ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;

ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;

cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;

cd first-project/html — перейди в папку html, которая находится в папке first-project;

cd .. — перейди на уровень выше, в родительскую папку;

cd ~ — перейди в домашнюю директорию (/Users/Username);

cd / — перейди в корневую директорию.

Работа с файлами и папками.
Создание

touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;

touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;

mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.

Копирование и перемещение

cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;

mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.

Чтение

cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.

Удаление

rm about.html (от англ. remove, «удалить») — удали файл about.html;

rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;

rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.

📌Как инициализировать Git-репозиторий?

Сделать папку репозиторием — git init

Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать Git-репозиторием (от англ. repository — «хранилище»). Для этого следует переместиться в неё и ввести команду git init (от англ. initialize — «инициализировать»).
Например, создайте папку first-project и сделайте её Git-репозиторием: перейдите в неё с помощью команды cd и выполните git init.

'''BASH
$ cd ~/dev/first-project 
%% перешли в нужную папку

$ git init 
%% создали репозиторий
''' 
Вы можете создать папку в любом месте на компьютере. Но в этом случае не забывайте менять в наших примерах путь ~/dev/first-project на тот, который ведёт к вашей папке. Помните, что не рекомендуется создавать репозиторий Git внутри другого Git-репозитория. Это может вызывать проблемы с отслеживанием изменений.

В некоторых случаях при инициализации репозитория Git может показать объёмное сообщение, которое начинается со слов Using 'master' as the name…. Не пугайтесь: это не ошибка. Пока это сообщение не имеет большого значения.

Также git init выведет сообщение вида Initialized empty Git repository in <*ваша папка с проектом*>/.git/ (англ. «инициализирован пустой Git-репозиторий в <*ваша папка*>/.git/»). В подпапке .git Git будет хранить всю служебную информацию.

Команда git init — одна из редко применяемых, ведь репозиторий создаётся один раз, а пользоваться им можно сколько угодно долго.

«Разгитить» папку, если что-то пошло не так, — rm -rf .git
Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку .git.

'''BASH
$ cd <папка с репозиторием> 
%% перешли в папку

$ rm -rf .git 
%% удалили подпапку .git 
'''

📌Проверить состояние репозитория — git status

После инициализации репозитория first-project запустите команду git status (от англ. status — «статус», «состояние») — она показывает текущее состояние репозитория.

Команда git status выведет:
* название текущей ветки: On branch master или On branch main;
* сообщение о том, что в репозитории ещё нет коммитов: No commits yet;
* сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — nothing to commit (create/copy files * and use "git add" to track).
* Подробнее о том, что такое коммиты, мы расскажем в следующих уроках.

В отличие от git init, команду git status используют часто. В любой непонятной ситуации стоит посмотреть состояние (статус) репозитория, а потом решить, что делать дальше.

📌Добавляем файлы в репозиторий

Подготовить файлы к сохранению — git add. 
Добавим в репозиторий два файла. Например, файл todo.txt, в котором будет список дел, и readme.txt для информации о проекте.

'''BASH
$ touch todo.txt
$ touch readme.txt
%% создали файлы todo.txt и readme.txt

$ git status 
%% проверили статус
'''
'''BASH
$ git add --all 
%% подготовили к сохранению все файлы в репозитории
$ git status 
%% проверили статус 
'''

Добавлять файлы можно и по одному, без ключа --all.
'''BASH
$ git add todo.txt
$ git add readme.txt
$ git status
'''
Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены. Обратиться к текущей папке в Bash позволяет точка (.).
'''BASH
$ git add . %% добавить всю текущую папку
$ git status
'''

 дальше .... Чем отличается запоминание от сохранения?