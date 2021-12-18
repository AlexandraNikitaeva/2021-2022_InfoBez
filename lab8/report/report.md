---
# Front matter
lang: ru-RU
title: "Отчёт по лабораторной работе №8"
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

Освоить на практике применение режима однократного гаммирования на примере кодирования различных исходных текстов одним ключом.

# Выполнение лабораторной работы

1. Объявила нужные библиотеки. Задала исходные данные -- телеграммы Центра. 

```python
import numpy as np
import operator as op
import sys

P1 = "GimmeGimmeGimmeA"
P2 = "ManAfterMidnight"
```

Также вывела длины телеграмм, чтобы показать, что они равны (рис. [-@fig:001]).

```python
print("Длина первой телеграммы {} символов, а второй -- {}".format(len(P1), len(P2)))
```

![Вывод на экран длин телеграмм](image/1.png){ #fig:001 width=90% }

2. Написала функцию, кодирующую исходные тексты в режиме однократного гаммирования.

```python
def shifrovka(p1, p2):
    print("Исходная телеграмма 1: ", p1)
    print("Исходная телеграмма 2: ", p2)
    
    p1_16 = []
    p2_16 = []
    for i in p1:
        p1_16.append(i.encode("cp1251").hex())
    for i in p2:
        p2_16.append(i.encode("cp1251").hex())
    print("Телеграмма 1 в 16-ой форме: ", p1_16)
    print("Телеграмма 2 в 16-ой форме: ", p2_16)
    
    K = []
    for i in np.random.randint(0, 255, len(p1)):
        K.append(hex(i)[2:])
    print("Ключ длиной {} байт: {}".format(len(p1), K))
    
    c1_16 = []
    c2_16 = []
    for i in range(len(p1_16)):
        c1_16.append("{:02x}".format(int(K[i], 16) ^ int(p1_16[i], 16)))
    for i in range(len(p2_16)):
        c2_16.append("{:02x}".format(int(K[i], 16) ^ int(p2_16[i], 16)))
    print("Зашифрованная телеграмма 1 в 16-ой форме: ", c1_16)
    print("Зашифрованная телеграмма 2 в 16-ой форме: ", c2_16)
    
    c1 = bytearray.fromhex("".join(c1_16)).decode("cp1251")
    c2 = bytearray.fromhex("".join(c2_16)).decode("cp1251")
    print("Зашифрованная телеграмма 1: ", c1)
    print("Зашифрованная телеграмма 2: ", c2)
    return c1, c2
```

3. Закодировала исходные тексты (рис. [-@fig:002]).

```python
C1, C2 = shifrovka(P1, P2)
```

![Шифрование исходных телеграмм](image/2.png){ #fig:002 width=90% }

4. Написала функцию, читающую (дешифрующую) оба текста, не зная ключа и не стремясь его определить, но получая на вход шаблон.

```python
def rasshifrovka(c1, c2, p):
    print("Зашифрованная телеграмма 1: ", c1)
    print("Зашифрованная телеграмма 2: ", c2)
    
    c1_16 = []
    c2_16 = []
    for i in c1:
        c1_16.append(i.encode("cp1251").hex())
    for i in c2:
        c2_16.append(i.encode("cp1251").hex())
    print("Зашифрованная телеграмма 1 в 16-ой форме: ", c1_16)
    print("Зашифрованная телеграмма 2 в 16-ой форме: ", c2_16)
    
    print("Шаблон: ", p)
    
    p_16 = []
    for i in p:
        p_16.append(i.encode("cp1251").hex())
    print("Шаблон в 16-ой форме: ", p_16)
    
    tmp = []
    pp_16 = []
    for i in range(len(p)):
        tmp.append("{:02x}".format(int(c1_16[i], 16) ^ int(c2_16[i], 16)))
        pp_16.append("{:02x}".format(int(tmp[i], 16) ^ int(p_16[i], 16)))
    print("Вторая телеграмма в 16-ой форме: ", pp_16)
    
    pp = bytearray.fromhex("".join(pp_16)).decode("cp1251")
    print("Вторая телеграмма: ", pp)
    return pp
```

5. Прочитала оба текста, используя шаблон 1-ой телеграммы (рис. [-@fig:003]).

```python
P2_dec = rasshifrovka(C1, C2, P1)
```

![Чтение телеграмм по 1-ой](image/3.png){ #fig:003 width=90% }

6. Прочитала оба текста, используя шаблон 2-ой телеграммы (рис. [-@fig:004]).

```python
P1_dec = rasshifrovka(C1, C2, P2)
```

![Чтение телеграмм по 2-ой](image/4.png){ #fig:004 width=90% }

# Выводы

Освоила на практике применение режима однократного гаммирования на примере кодирования различных исходных текстов одним ключом.

# Ответы на контрольные вопросы

1. Как, зная один из текстов (P1 или P2), определить другой, не зная при этом ключа?

По формуле (рис. [-@fig:005]):

![Определение другого текста](image/5.png){ #fig:005 width=60% }

2. Что будет при повторном использовании ключа при шифровании текста?

Ничего не изменится -- получится исходный текст.

3. Как реализуется режим шифрования однократного гаммирования одним ключом двух открытых текстов?

По формуле (рис. [-@fig:006]):

![Реализация однократного гаммирования](image/6.png){ #fig:006 width=60% }

4. Перечислите недостатки шифрования одним ключом двух открытых текстов.

Злоумышленнику достаточно знать формат хотя бы одного текста и иметь на руках оба шифротекста, чтобы дешифровать послание.

5. Перечислите преимущества шифрования одним ключом двух открытых текстов.

Режим однократного гаммирования помогает упростить процессы шифровки и дешифровки.

# Список литературы{.unnumbered}

1. Кулябов Д. С., Королькова А. В., Геворкян М. Н. Информационная безопасность компьютерных сетей. Лабораторная работа № 8. Элементы криптографии. Шифрование 
(кодирование) различных исходных текстов одним ключом