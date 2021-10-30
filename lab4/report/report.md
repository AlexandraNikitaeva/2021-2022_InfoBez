---
# Front matter
lang: ru-RU
title: "Отчёт по лабораторной работе №4"
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

Получение практических навыков работы в консоли с расширенными атрибутами файлов.

# Выполнение лабораторной работы

1. От имени пользователя guest определила расширенные атрибуты файла */home/guest/dir1/file1* командой `lsattr /home/guest/dir1/file1`. (рис. [-@fig:001])

2. Установила командой `chmod 600 file1` на файл file1 права, разрешающие чтение и запись для владельца файла. (рис. [-@fig:001])

3. Попробовала установить на файл */home/guest/dir1/file1* расширенный атрибут *a* от имени пользователя guest: `chattr +a /home/guest/dir1/file1`. В ответ 
получила отказ в выполнении операции. (рис. [-@fig:001])

![Установка *a* на file1 от имени guest](image/1.png){ #fig:001 width=70% }

4. Зашла на вторую консоль и повысила свои права с помощью команды su. Попробовала установить расширенный атрибут *a* на файл */home/guest/dir1/file1* от 
имени суперпользователя: `chattr +a /home/guest/dir1/file1`. (рис. [-@fig:002])

![Установка *a* на file1 от суперпользователя](image/2.png){ #fig:002 width=70% }

5. От пользователя guest проверила правильность установления атрибута: `lsattr /home/guest/dir1/file1`. (рис. [-@fig:003])

6. Выполнила дозапись в файл file1 слова «test» командой `echo "test" >> /home/guest/dir1/file1`. После этого выполнила чтение файла file1 командой 
`cat /home/guest/dir1/file1`. Убедилась, что слово test было успешно записано в file1. (рис. [-@fig:003])

7. Попробовала стереть имеющуюся в file1 информацию командой `echo "abcd" > /home/guest/dirl/file1`. Попробовала переименовать файл. (рис. [-@fig:003])

8. Попробовала с помощью команды `chmod 000 file1` установить на файл file1 права, запрещающие чтение и запись для владельца файла. (рис. [-@fig:003]) 
Указанные команды мне выполнить не удалось: операция была не позволена.

![Различные операции над file1 после установки *a*](image/3.png){ #fig:003 width=70% }

9. Сняла расширенный атрибут *a* с файла */home/guest/dirl/file1* от имени суперпользователя командой `chattr -a /home/guest/dir1/file1`. (рис. [-@fig:004]) 

![Снятие *a* на file1 от суперпользователя](image/4.png){ #fig:004 width=70% }

Повторила операции, которые мне ранее не удавалось выполнить. (рис. [-@fig:005]) Теперь все операции выполнены успешно.

![Различные операции над file1 после снятия *a*](image/5.png){ #fig:005 width=70% }

10. Повторила свои действия по шагам (рис. [-@fig:007]), заменив атрибут *a* атрибутом *i* (рис. [-@fig:006]). Теперь мне не удалось даже дозаписать 
информацию в файл. Все остальные операции так же, как и ранее, не удались.

![Установка *i* на file1 от суперпользователя](image/6.png){ #fig:006 width=70% }

![Различные операции над file1 после установки *i*](image/7.png){ #fig:007 width=70% }

# Выводы

Получила практические навыки работы в консоли с расширенными атрибутами файлов.

# Список литературы{.unnumbered}

1. Кулябов Д. С., Королькова А. В., Геворкян М. Н. Информационная безопасность компьютерных сетей. Лабораторная работа № 4. Дискреционное разграничение прав 
в Linux. Расширенные атрибуты.