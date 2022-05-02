![Это лого git](gitlogo.png)
# Инструкция по работе с git 
## 1. Проверка наличия установленного Git.
В терминале выполнить команду `git version`.
Если git установлен, появится сообщение с информацией о версии файла. Иначе будет сообщение об ошибке.
## 2. Установка Git.
Загружаем последнюю версию Git с сайта https://git-scm.com/downloads
Устанавливаем с настройками по умолчанию

## 3. Настройка Git
При первом использовании необходимо представиться. Для этого в терминале ввести две команды:
```
git config --global user.name "Ваше имя"
git config --global user.email "Ваш email"
```
## 4. Инициализация репозитория. 
Получить репозиторий можно двумя способами:
1. Git init. 
2. Git clone
* В терминале переходим к папке, в которой хотим создать репозиторий.
Выполняем команду `git init` 
 исходной папке у нас появится скрытая папка *.git*, содержащая все необходимые файлы репозитория - структуру git репозитория.
* Клонировать существующий репозиторий Git из любого места.
Сделать это можно командой 

```
git clone <Адрес репозитория>
```
    Блок текстовый - отступом

*Два способа выделения - либо ```, либо отступом.*

## 5. Запись изменений в репозиторий
* Чтобы посмотреть состояние файлов в репозитории, необходимо выполнить команду:

    git status

    Также данной командой можно отследить расположение указателя HEAD


* Для того чтобы начать отслеживать новый фалй необходимо выполнить команду 

    git add <имя.расширение>

Данная команда добавляет изменения в индекс, подготавливает к коммиту.

## 6. Просмотр истории коммитов

Для просмотра истории коммитов используется команда 

    git log

Данная команда перечисляет коммиты с их хэш-кодами, именем и электронной почтой, датой создания и сообщением коммита.
По умолчанию последний коммит находится наверху.Для выхода из режима - нажать _**Q**_

## 7. Перемещение между коммитами 

    git checkout <хеш-код>

Пример использования команды `git checkout`

    git checkout 2f31c9e
Чтобы перейти к нужному коммиту необходимо использовать комманду __*git checkout*__

Такой переход можно использовать либо только для просмотра, либо для изменений, но тогда нужно создать ветку, иначе изменения потеряются.

*!!Обязательно **git checkout master** или **git switch -** для продолжения работы*

## 8. Игнорирование файлов
*.gitignore*
Данная команда используется для исключения файлов и папок из индекса. Файлы большого объема (к примеру изображения),при работе в комманде принято пушить чистый код, текст. Либо временные файлы, черновики.  

А это написано в GitHub и спуллено в VSC

## 9. Работа с ветками (branch)
Основные команды 
    
    git branch - выводит список веток
    git branch Branchname - создает ветку с именем <BranchName>
    git checkout BranchName - переходит на ветку <BranchName>
    git merge - слияние веток
    git branch -d BranchName - удаляет пустую ветку с именем <BranchName>
    git branch -D BranchName - удаляет ветку с именем <BranchName>, в которой присутствуют непроиндексированные данные

При  слиянии веток случаются конфликты.
Основная причина конфликтов - изменения в одной из веток части кода присутствующего в обеих ветках. VSC сигнализирует о конфликте и подсвечивает участок кода, в котором возник конфликт, а также предлагает пути решения путем выбора из набора вариантов:

* Принять код ветки a и удалить изменения кода ветки b
* Принять код ветки b b отменить изменения кода ветки b
* Принять и объединить версии кода обеих веток.

## 10. Работа с удаленными репозиториями. 
### На примере онлайн-сервиса-банка удаленных репозиториев GitHub

В случае работы разработчика над проектом с разных рабочих мест, либо в случае значительного количества разработчиков над проектом необходимо какое-то облачное решение, чем собственно и является GitHub. 

#### 10а. Работа в собственном удаленном репозитории на Github. 
* Создаем репозиторий в GitHub. 
    
    вариант a. В аккаунте переходим в пункт Repositories и нажимаем кнопку __*NEW*__.

    вариант b. Правом верхнем углу, возле логотипа аккаунту раскрываем список кнопки __*+*__
* Вводим наименование репозитория в поле __*Repository name*__ 
(при необходимости возможно добавить README c описанием проекта. Также можем выбрать из списка вариантов gitignore и применением лицензии можем задать ограничения на изменения кода другими пользователями).
* Жмем зеленую кнопку внизу __*Create repository*__

    *Из предложенных варантов:
1. Создание **нового** репозитория средствами коммандной строки. 
2. Пуш **существующего** репозитория средствами коммандной строки.
3. Импорт кода из другого репозитория.

    Выбираем второй вариант. Копируем и выполняем команды в VSC.

    Команда в VSC __*git push*__ отправляет изменения в GitHub


#### 10b. Работа с репозиторием другого пользователя GitHub

* Поиском на Github находим интересующий нас репозиторий 
* Кнопкой Fork делаем копию в свой аккаунт
* В своем аккаунте находим скопированный репозиторий, копируем его адрес кнопкой _Copy_
* Создаем папку с именем репозитория 
* В VSC выполняем команду __*git clone*__ со скопированной строкой, 
например, *git clone https://github.com/....*
* Проверяем правильность пути в созданную папку, при необходимости корректируем командой __*cd*__
* Создаем ветку в которой делаем всю работу. 
* По окончанию вносим изменения в свой репозиторий командой __*git push*__
* В gitHub создаем Pull Request с описанием проделанной работы.
