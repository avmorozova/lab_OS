---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе №11"
subtitle: "Дисциплина: Операционные системы"
author: "Морозова Анастасия Владимировна"

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

Изучить основы программирования в оболочке ОС UNIX/Linux. Научиться писать небольшие командные файлы.

# Выполнение лабораторной работы

1. Изучила команды архивации (команды manzip, manbzip2, mantar)(рис. -@fig:001)
 - Синтаксис команды zip для архивации файла: zip[опции] [имя файла.zip][файлы или папки, которые будем архивировать]
 - Синтаксис команды zip для разархивации/распаковки файла: unzip[опции][файл_архива.zip][файлы] -x [исключить] -d [папка] (рис. -@fig:002)
 - Синтаксис команды bzip2 для архивации файла:bzip2 [опции] [имена файлов]
 - Синтаксис команды bzip2 для разархивации/распаковки файла: bunzip2[опции] [архивы.bz2] (рис. -@fig:003)
 - Синтаксис команды tar для архивации файла:tar[опции][архив.tar][файлы_для_архивации]
 - Синтаксис команды tarдля разархивации/распаковки файла:tar[опции][архив.tar] (рис. -@fig:004)
 
  ![Команды архивации](image11/1.png){ #fig:001 width=70% }

  ![Команды zip](image11/2.png){ #fig:002 width=70% }
 
  ![Команды bzip2](image11/3.png){ #fig:003 width=70% }
  
  ![Команды tar](image11/4.png){ #fig:004 width=70% }
  
2. Создаю файл, в котором будуписать первый скрипт, и открыла его в редакторе emacs, используя клавиши «Ctrl-x» и «Ctrl-f» (команды touch backup.sh и emacs &) (рис. -@fig:005)
 
  ![Открытие файла](image11/5.png){ #fig:005 width=70% }
  
Написала скрипт, который при запуске будет делать резервную копию самого себя (то есть файла, в котором содержится его исходный код) в другую  директорию backup в домашнем каталоге. При этом файл должен архивироваться одним из архиваторов на выбор zip, bzip2 или tar. При  написании  скрипта  использовала архиватор bzip2 (рис. -@fig:006)
  
  ![Написание скрипта](image11/6.png){ #fig:006 width=70% }
  
Проверила работу скрипта (команда ./backup.sh), предварительно добавив  для него право на выполнение (команда chmod +x*.sh). Проверила, появился ли каталог backup/, перейдя в него(команда cd backup/), посмотрела его  содержимое  (команда ls) и  просмотрела содержимое архива (команда bunzip2 -c backup.sh.bz2).Скрипт работает корректно.(рис. -@fig:007)(рис. -@fig:008)
  
  ![Проверка работы скрипта](image11/7.png){ #fig:007 width=70% }

  ![Проверка работы скрипта](image11/8.png){ #fig:008 width=70% }
  
3. Создала файл, в котором буду писать второй скрипт, и открыла его в редакторе emacs, используя клавиши «Ctrl-x» и «Ctrl-f» (команды touch ex2.sh и emacs &)(рис. -@fig:009)
 
  ![Второй скрипт](image11/9.png){ #fig:009 width=70% }
  
Написала пример командного файла, обрабатывающего любое произвольное  число аргументов командной строки, в том числе превышающее десять. Например, скрипт может последовательно распечатывать значения всех переданных аргументов (рис. -@fig:010)

  ![Обработка произвольного числа аргументов](image11/10.png){ #fig:010 width=70% }

Проверила работу написанного скрипта (команды ./prog2.sh0 1 2 3 4 и ./ex2.sh 0 1 2 3 45 6 7 8 9 10 11), предварительно добавив для него право на выполнение (команда chmod +x*.sh). Вводила аргументы, количество которых меньше 10 и больше 10.Скрипт работает корректно. (рис. -@fig:011)

  ![Проверка скрипта](image11/11.png){ #fig:011 width=70% }
 
4. Создала файл, в котором буду писать третий скрипт, и открыла его в редакторе emacs, используя клавиши «Ctrl-x» и «Ctrl-f» (команды touch progls.sh и emacs &)(рис. -@fig:012)

  ![Третий скрипт](image11/12.png){ #fig:012 width=70% }
 
Написала командный файл − аналог команды ls(без использования самой этой команды и команды dir). Он должен выдавать информацию 
о нужном каталоге и выводить информацию о возможностях доступа к файлам этого каталога (рис. -@fig:013)(рис. -@fig:014)
  
  ![Аналог команды ls](image11/13.png){ #fig:013 width=70% }
  
  ![Аналог команды ls](image11/14.png){ #fig:014 width=70% }
  
Далее проверила работу скрипта (команда ./progls.sh~), предварительно  добавив для него право на выполнение (команда chmod +x*.sh) (рис. -@fig:015)

  ![Проверка скрипта](image11/15.png){ #fig:015 width=70% }

5. Создала файл для четвертого скрипта (команда touch format.sh)и открыла его в редакторе emacs, используя клавиши «Ctrl-x» и «Ctrl-f» (команда emacs &). Переместила курсор в конец строки клавишей «Ctrl-e»(рис. -@fig:016)
 
  ![Четвертый скрипт](image11/16.png){ #fig:016 width=70% }
  
Написала командный файл, который получает в качестве аргумента командной строки формат файла (.txt, .doc, .jpg, .pdfи т.д.) и вычисляет количество таких файлов в указанной директории. Путь к директории также передаётся в виде аргумента командной строки (рис. -@fig:017)

  ![Вычисление кол-ва необходимых файлов](image11/17.png){ #fig:017 width=70% }
  
Проверила работу написанного скрипта (команда ./format.sh~ pdf sh txt doc), предварительно добавив для него право на выполнение (команда chmod +x*.sh), а также создав дополнительные файлы с разными расширениями (команда touch file.pdf file1.doc file2.doc»)(рис. -@fig:018)

  ![Проверка скрипта](image11/18.png){ #fig:018 width=70% }
  
6. Контрольные вопросы:

  1) Командный процессор (командная оболочка, интерпретатор команд shell) - это программа, позволяющая пользователю взаимодействовать с операционной системой компьютера. В операционных системах типа UNIX/Linux наиболее  часто  используются  следующие  реализации командных оболочек:
  - оболочка Борна (Bourneshellили sh) − стандартная командная оболочка UNIX/Linux, содержащая базовый, но при этом полный набор функций;
  - С-оболочка  (или csh) − надстройка над оболочкой Борна, использующая  С-подобный синтаксис команд с возможностью сохранения истории выполнения команд;
  - оболочка Корна (или ksh) − напоминает оболочку С, но операторы управления программой совместимы с операторами оболочки Борна;
  - BASH − сокращение от Bourne Again Shell (опять оболочка Борна), в  основе своей совмещает свойства оболочек С и Корна (разработка компании Free Software Foundation)
  
  2) POSIX (Portable Operating System Interface for Computer Environments) − набор стандартов описания интерфейсов взаимодействия операционной системы и прикладных программ. Стандарты POSIX разработаны комитетом IEEE (Institute of Electrical and Electronics Engineers) для обеспечения совместимости различных UNIX/Linuxподобных операционных систем и переносимости прикладных программ на уровне исходного кода. POSIX-совместимые оболочки разработаны на базе оболочки Корна.
  
  3) Командный процессор bashобеспечивает возможность использования переменных  типа  строка  символов.  Имена  переменных  могут  быть выбраны пользователем. Пользователь имеет возможность присвоить переменной значение некоторой строки символов. Например, команда 
«mark=/usr/andy/bin» присваивает значение строки символов /usr/andy/binпеременной markтипа строка символов. Значение, присвоенное   некоторой переменной, может быть впоследствии использовано. Для этого в соответствующем месте командной строкиn должно быть употреблено  имя  этой переменной, которому предшествует метасимвол $. Например,  команда «mv afile${mark}» переместит файл afile из текущего каталога в каталог с абсолютным полным именем /usr/andy/bin.
Оболочка bashпозволяет работать с массивами. Для создания массива используется команда setс  флагом -A. За флагом следует имя переменной,  а затем список значений, разделённых пробелами. Например, «set -A states Delaware Michigan "NewJersey"». Далее можно сделать добавление в массив, например, states[49]=Alaska. Индексация массивов начинается с нулевого элемента.

  4) Оболочка bash поддерживает встроенные арифметические функции. Команда let является показателем того, что последующие аргументы представляют собой выражение, подлежащее вычислению. Простейшее выражение − это единичный терм (term), обычно целочисленный. Команда let берет два операнда и присваивает их переменной. Команда readпозволяет читать значения переменных со стандартного ввода: 
  - «echo "Please enter Month and Day of Birth ?"»
  - «read monday trash»
  В переменные mon и day будут считаны соответствующие значения, введённые с клавиатуры, а переменная trash нужна для того, чтобы отобрать всю избыточно введённую информацию и игнорировать её.
  
  5) В языке программирования bash можно применять такие арифметические операции как сложение (+), вычитание (-), умножение (*), целочисленное деление (/) и целочисленный остаток от деления (%).

  6) В (( )) можно записывать условия оболочки bash, а также внутри двойных скобок можно вычислять арифметические выражения и возвращать результат.
  
  7) Стандартные переменные:
  - PATH: значением данной переменной является список каталогов, в которых командный процессор осуществляет поиск программы или команды, указанной в командной строке, в том случае, если указанное имя программы или команды не содержит ни одного символа /. Если имя команды содержит хотя бы один символ /, то последовательность поиска, предписываемая значением переменной PATH, нарушается. В этом случае в зависимости от того,  является имя команды абсолютным  или  относительным, поиск начинается  соответственно от корневогоили текущего каталога
  - PS1  и PS2: эти  переменные  предназначены  для  отображения промптера командного процессора. PS1 − это промптер командного  процессора, по умолчанию его значение равно символу  $  или  #. Если какая-то интерактивная  программа, запущенная командным  процессором, требует   ввода, то используется  промптер PS2. Он по умолчанию имеет значение символа >.
  - HOME: имя домашнего каталога пользователя. Если команда cdвводится  без аргументов, то происходит переход в каталог,указанный в этой переменной
  - IFS: последовательность символов, являющихся разделителями в командной строке, например, пробел, табуляция и перевод строки (newline).
  - MAIL: командный процессор каждый раз перед выводом на экран промптера проверяет содержимое файла, имя которого указано в этой переменной, и если содержимое этого файла изменилось с момента последнего ввода из него, то перед тем как вывести на терминал промптер, командный процессор выводит на терминал сообщение You have mail(у Вас есть почта).
  - TERM: тип используемого терминала.
  - LOGNAME: содержит регистрационное имя пользователя, которое устанавливается автоматически при входе в систему.
  
  8) Такие символы, как ' < > * ? | \" &, являются метасимволами и имеют для командного процессора специальный смысл.
  
  9) Снятие специального смысла с метасимвола называется экранированием   метасимвола. Экранирование может быть осуществлено с помощью предшествующего метасимволу символа \, который, в свою очередь, является метасимволом. Для экранирования группы  метасимволов нужно заключить её в одинарные кавычки. Строка, заключённая в двойные кавычки, экранирует все метасимволы, кроме $, ' , \, ". Например, 
  - –echo\* выведет на экран символ *,
  - –echoab’*\|*’cdвыведет на экран строку ab*\|*cd.
  
  10) Последовательность команд может быть помещена в текстовый файл. Такой файл называется командным. Далее этот файл можно выполнить по команде: bash командный _ файл [аргументы].Чтобы не вводить каждый раз  последовательности символов bash, необходимо изменить код защиты этого командного файла, обеспечив доступ к этому файлу по выполнению. Это может быть сделано с помощью команды chmod +x имя_файла. Теперь можно вызывать свой командный файл на выполнение, просто вводя его имя с терминала так, как будто он является выполняемой программой. Командный процессор распознает, что в Вашем файле на самом деле хранится не выполняемая программа, а программа, написанная на языке программирования оболочки, и осуществит её интерпретацию.
  
  11) Группу команд можно объединить в функцию. Для этого существует ключевое слово function, после которого следует имя функции и список команд, заключённых в фигурные скобки. Удалить функцию можно с помощью команды unset c флагом -f.
  
  12)Чтобы выяснить, является ли файл каталогом или обычным файлом, необходимо воспользоваться командами «test-f [путь до файла]» (для проверки, является ли обычным файлом) и «test -d[путь до файла]» (для проверки, является ли каталогом).
  
  13) Команду set можно использовать для вывода списка переменных окружения. В системах Ubuntu и Debian команда set также выведет список функций командной оболочки после списка переменных командной оболочки. Поэтому для ознакомления со всеми элементами списка переменных  окружения  при работе с данными системами рекомендуется использовать команду set| more. Команда type set предназначена для наложения ограничений на переменные. Команду unset следует использовать для удаления переменной из окружения командной оболочки.
  
  14)При вызове командного файла на выполнение параметры ему могут быть переданы точно таким же образом, как и выполняемой программе. С точки  зрения командного файла эти параметры являются позиционными. Символ  $  является метасимволом командного процессора. Он используется, в частности, для ссылки на параметры, точнее, для получения их значений в командном файле. В командный файл можно передать до девяти параметров. При использовании где-либо в командном файле комбинации символов $i, где 0 < i< 10, вместо неё будет осуществлена подстановка значения параметра с порядковым номером i, т.е. аргумента командного файла с порядковым номером i. Использование  комбинации  символов  $0  приводит  к  подстановке вместо неё имени данного командного файла.
  
  15) Специальные переменные:
  - $* − отображается вся командная строка или параметры оболочки;
  - $? − код завершения последней выполненной команды;
  - $$ − уникальный  идентификатор  процесса,  в  рамках  которого выполняется командный процессор;
  - $! − номер процесса, в рамках которого выполняется последняя вызванная на выполнение в командном режиме команда;
  - $- − значение флагов командного процессора;
  - ${#* } − возвращает целое число количество слов, которые были результатом $*;
  - ${#name} − возвращает целое значение длины строки в переменной name;
  - ${name[n]} − обращение к n-му элементу массива;
  - ${name[*]} − перечисляет все элементы массива, разделённые пробелом;
  - ${name[@]} − то же самое, но позволяет учитывать символы пробелы в самих переменных;
  - ${name:-value} − если значение переменной name не определено, то оно будет заменено на указанное value;
  - ${name:value} − проверяется факт существования переменной;
  - ${name=value} − если name не определено, то ему присваивается значение value;
  - ${name?value} − останавливает выполнение, если имя переменной не  определено, и выводит value как сообщение об ошибке;
  - ${name+value} − это выражение работает противоположно ${name-value}. Если переменная определена, то подставляется value;
  - ${name#pattern} − представляет  значение  переменной name с удалённым самым коротким левым образцом (pattern);
  - ${#name[*]} и ${#name[@]} − эти  выражения  возвращают количество элементов в массиве name.
  
# Выводы

В ходе выполнения лабораторной работы я изучила основы программирования в оболочке ОС UNIX/Linux. Научилась писать небольшие командные файлы.
 
