# Инструкция по работе с Git

## Что такое гит?
***Git*** - самая популярная реализация распределённой системы контроля версий(версионность поддерживается и на сервере, и у каждого клиента). Самой распространнённой реализацией ***Git*** является (GitHub)[https://github.com]

## Подготовка репозитория
Для создания репозитория используется команда *git init*. Для этого необходимо открыть в терминале папку с будущем репозиторием и написать *git init*

## Создание коммитов

### Добавление файлов к коммиту
Для добавления файла к новому коммиту используется команда *git add*. Используется она следующим образом: в терминале с папкой-репозиторием пишем *git add <название файла>*.

### Создание коммита
Для создание новой фиксации(коммита) используется команда *git commit*. Для этого в терминале с папкой-репозиторием пишем *git commit -m "<сообщение к коммиту>*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО!!!***

## Журнал изменений
Для просмотра истории изменений используется команда *git log*. Для этого в терминале с папкой-репозиторием необходимо написать *git log*

## Перемещение между коммитами
Для перемещения на другую фиксацию(коммит) используется команда *git checkout*. Для этого необходимо, как показано в прошлом пункте, в журнале изменений найти необходимый коммит и его хеш(номер), после чего в терминале с папкой-репозиторием надо написать *git checkout <хеш коммита>*. После выполнения этой команды мы попадаем в состояние **detached head**, в котором никакие следующие коммиты сохраняться не будут. Для выхода из этого состояния необходимо написать *git checkout master*.

## Ветки в гит
### Создание веток в гит
Для создание новой ветки используется команда *git branch*. Для этого в терминале с папкой-репозиторием необходимо написать *git branch <название ветки>*.
### Просмотр списка веток
Для просмотра списка веток используется команда *git branch*. Для этого в терминале с папкой-репозиторием необходимо написать *git branch*. Выделенная зелёным со звёздочкой ветка - это ветка, в данный момент на которой мы находимся.

### Перемещение между ветками
Для перехода на другую ветку используется команда *git checkout*. Для этого в терминале с папкой-репозиторием необходимо написать *git checkout <название ветки>*. Такая ветка должна **существовать**.

## Слияние веток и разрешение конфликтов
Ветвление позволяет разделять рабочий процесс, оптимизировать тестирование и написание нового кода. Однако после того, как разработчик убедился, что написанный им кусок кода готов и его можно отправить к остальной части итоговой версии, удобно переместить его в основную ветку. Такой подход дает возможность получить к концу разработки проекта целый продукт в одном месте.
Для этого в Git предусмотрено слияние — перенос изменений с одной ветки на другую. Однако сливаемая ветка (под этим определением мы подразумеваем ветку, у которой берем изменения для «вливания» их в другую ветвь) никак не меняется и остается в прежнем состоянии. Такие преобразования мы получаем, применив git merge

     *git merge <name of merged branch>*

Операция может привести к появлению конфликтов при попытке слить ветки. Это вызвано тем, что изменения удаляют или переписывают информацию в существующих файлах. При попытке некорректного слияния Git останавливает выполнение команды, чтобы вы могли разрешить конфликт.
Также стоит упомянуть о существовании ключей, предназначенных специально для работы с конфликтами:

 * abort — прерывает слияние и возвращает все к началу
 * continue — продолжает слияние после разрешения конфликта
Решить конфликт можно двумя способами:

Вручную разрешить файловый конфликт. Для этого нужно самим изменить файлы, с которыми возникли проблемы. Мы получим файлы такими, какими и представляли их при попытке слияния.
Выбрать более подходящий файл, а от второго отказаться.

## Удаление веток

Для корректного удаления нужно помнить несколько правил:

 * Нельзя удалить ветку, в которой вы находитесь. Git выкинет ошибку и не произведет удаление. Следовательно, нужно перейти на другую ветку.

 * Git не позволит удалить ветку, у которой есть несохраненные изменения. Так мы избегаем ситуации, когда часть написанного кода будет безвозвратно утеряна. Если же мы уверены, что изменения в этой версии не нужны и их можно смело удалять, то вместо флага -d используем -D:

        git branch -D <name of branch>

Соблюдая все условия, нам удастся удалить указанную ветвь.

## Работа с удаленными репозиториями 
### Удаленный репозитоий 
Удаленный репозиторий – полноценный репозиторий, ничем не отличающийся от локального. У удаленного репозитория есть собственные ветки, собственный указатель HEAD, своя история коммитов и так далее.
## Просмотр удалённых репозиториев
Для того, чтобы просмотреть список настроенных удалённых репозиториев запускаем команду *git remote*. Она выведет названия доступных удалённых репозиториев. Если вы клонировали репозиторий, то увидите как минимум origin – имя по умолчанию, которое Git даёт серверу, с которого производилось клонирование.
## Добавление удалённых репозиториев
Для того, чтобы добавить удалённый репозиторий и присвоить ему имя (shortname), просто задайте команду 

      *git remote add <shortname> <url>*
## git push
Команда *git push* используется для установления связи с удалённым репозиторием, вычисления локальных изменений отсутствующих в нём, и собственно их передачи в вышеупомянутый репозиторий. Этой команде нужно право на запись в репозиторий, поэтому она использует аутентификацию.
## git remote
Команда *git remote* служит для управления списком удалённых репозиториев. Она позволяет сохранять длинные URL репозиториев в виде понятных коротких строк, например «origin», так что вам не придётся забивать голову всякой ерундой и набирать её каждый раз для связи с сервером. Вы можете использовать несколько удалённых репозиториев для работы и git remote поможет добавлять, изменять и удалять их.

## Вывод
таким образом мы расммотрели следующие пункты работы в Git:
что такое гит, подготовка репозитория, создание коммитов, журнал изменений, перемещения, ветки их слияние и разрешение конфликтов, удаление веток и работу с удаленными репозиториями.

