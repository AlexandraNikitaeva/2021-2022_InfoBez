---
# Front matter
lang: ru-RU
title: "Отчёт по лабораторной работе №1"
subtitle: "дисциплина: Информационная безопасность"
author: "Никитаева Александра Семеновна, НПИбд-02-18"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Задание

Лабораторная работа подразумевает установку на виртуальную машину VirtualBox операционной системы Linux, дистрибутив Centos.

# Выполнение лабораторной работы

1. Загрузила на своем компьютере операционную систему Windows. Осуществила вход в систему.

2. Перешла в каталог, предназначенный для данного предмета.

3. Создала каталог с именем пользователя asnikitaeva.

4. Перешла в каталог "Загрузки", где размещён образ виртуальной машины.

5. Скопировала образ виртуальной машины в созданный на предыдущем шаге каталог (рис. [-@fig:001]).

![Перемещение образа виртуальной машины в каталог asnikitaeva](image/1.png){ #fig:001 width=70% }

6. Запустила виртуальную машину (рис. [-@fig:002]).

![Запуск виртуальной машины](image/2.png){ #fig:002 width=70% }

7. Проверила в свойствах VirtualBox месторасположение каталога для виртуальных машин. Для этого в VirtualBox выбрала "Файл" -> "Свойства", вкладка "Общие". 
В поле "Папка для машин" (рис. [-@fig:003]) должен стоять каталог asnikitaeva, расположенный в папке ИБ.

![Исправление каталога для виртуальных машин](image/3.png){ #fig:003 width=70% }

8. Создала новую виртуальную машину. Для этого в VirtualBox выбрала "Машина" -> "Создать". Указала имя виртуальной машины — Base, тип операционной системы — 
Linux, RedHat. Указала размер основной памяти виртуальной машины — 1024 МБ. Также создала новый виртуальный жесткий диск. (рис. [-@fig:004])

![Создание виртуальной машины](image/4.png){ #fig:004 width=70% }

9. Задать конфигурацию жесткого диска — загрузочный, VDI (VirtualBox Disk Image), динамический виртуальный диск. Задала размер диска — 40 ГБ и его 
расположение. (рис. [-@fig:005])

![Конфигурация жесткого диска](image/5.png){ #fig:005 width=70% }

10. В VirtualBox появилась новая виртуальная машина (рис. [-@fig:006]).

![Новая виртуальная машина](image/6.png){ #fig:006 width=70% }

11. Выделила в окне менеджера VirtualBox виртуальную машину Base и открыла окно "Свойства". Проверила, что папка для снимков виртуальной машины Base имеет 
путь <Моя папка>/Base/Snapshots. Для этого выбрала в VirtualBox "Свойства" виртуальной машины Base -> "Общие", вкладка "Дополнительно" (рис. [-@fig:007]).

![Настройка папки для снимков виртуальной машины](image/7.png){ #fig:007 width=70% }

12. Выбрала в VirtualBox "Свойства" -> "Носители" виртуальной машины Base. Добавила новый привод оптических дисков и выбрала нужный образ (рис. [-@fig:008] 
и [-@fig:009]).

![Выбор образа оптического диска](image/8.png){ #fig:008 width=70% }

![Окно "Носители" виртуальной машины](image/9.png){ #fig:009 width=70% }

13. Запустила виртуальную машину Base, выбрала установку системы (рис. [-@fig:010]).

![Запуск установки системы](image/10.png){ #fig:010 width=70% }

14. Установила английский язык для процесса установки, т. к. при установке русского языка у меня обрезалось окно установки (рис. [-@fig:011]).

![Выбор языка для процесса установки](image/11.png){ #fig:011 width=70% } 

15. Добавила русский язык для раскладки клавиатуры (рис. [-@fig:012]) и в качестве еще одного поддерживаемого языка (рис. [-@fig:013]).

![Выбор языка для раскладки клавиатуры](image/12.png){ #fig:012 width=70% }

![Выбор языка в качестве еще одного поддерживаемого](image/13.png){ #fig:013 width=70% }

16. В качестве имени машины указала «asnikitaeva.localdomain» (рис. [-@fig:014]).

![Указание сетевого имени виртуальной машины](image/14.png){ #fig:014 width=70% }

17. Указала часовой пояс «Москва» (рис. [-@fig:015]).

![Настройка часового пояса](image/15.png){ #fig:015 width=70% }

18. Установила пароль для root (рис. [-@fig:016]).

![Установка пароля для root](image/16.png){ #fig:016 width=70% }

19. Создала пользователя asnikitaeva (рис. [-@fig:018]).

![Создание пользователя asnikitaeva](image/18.png){ #fig:018 width=70% }

20. Проверила все пункты и начала установку (рис. [-@fig:019]).

![Предустановочное состояние](image/19.png){ #fig:019 width=70% }

21. Завершила установку операционной системы и перезагрузила её (рис. [-@fig:020]).

![Завершение установки](image/20.png){ #fig:020 width=70% }

22. В VirtualBox оптический диск отключился автоматически (рис. [-@fig:021]).

![Отключенный оптический диск](image/21.png){ #fig:021 width=70% }

23. Запустила виртуальную машину. Приняла лицензию (рис. [-@fig:022]).

![Принятие лицензии](image/22.png){ #fig:022 width=70% }

24. Подключилась к виртуальной машине с помощью созданной учётной записи (рис. [-@fig:023]).

![Подключение к виртуальной машине](image/23.png){ #fig:023 width=70% }

25. Настроила все, что требовалось.

26. На виртуальной машине Base запустила терминал, перешла под учетную запись root с помощью команды su. С помощью команды yum update 
обновила системные файлы. (рис. [-@fig:024])

![Окончание обновления системных файлов](image/24.png){ #fig:024 width=70% }

27. Установила необходимые программы (mc) (рис. [-@fig:025]).

![Окончание установки mc](image/25.png){ #fig:025 width=70% }

28. После установки необходимых программ завершила работу виртуальной машины.

29. Для того чтобы другие виртуальные машины могли использовать машину Base и её конфигурацию как базовую, произвела следующие действия. В VirtualBox в меню 
выбрала "Файл" -> "Менеджер виртуальных носителей" -> "Жёсткие диски" и, выделив «Base.dvi», указала "Отключить". (рис. [-@fig:026] и [-@fig:027])

![Освобождение жесткого диска](image/26.png){ #fig:026 width=70% }

![Изменение свойств жесткого диска](image/27.png){ #fig:027 width=70% }

30. На основе виртуальной машины Base создала машину Host2, выбрав в VirtualBox "Машина" -> "Создать" и в "Мастере создания новой виртуальной машины" указав 
в качестве имени машины Host2, в качестве типа операционной системы — Linux, версия RedHat, а при конфигурации виртуального жёсткого диска выбрав 
"Использовать существующий жёсткий диск" Base.vdi. (рис. [-@fig:028] и [-@fig:029])

![Создание виртуальной машины Host2](image/28.png){ #fig:028 width=70% }

![Созданная новая виртуальная машина](image/29.png){ #fig:029 width=70% }

# Выводы

Приобрела практические навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Список литературы{.unnumbered}

1. Кулябов Д. С., Королькова А. В., Геворкян М. Н. Информационная безопасность компьютерных сетей. Лабораторная работа № 1. Установка и конфигурация 
операционной системы на виртуальную машину