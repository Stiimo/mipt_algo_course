# MIPT algo course
Добро пожаловать в репозиторий, посвященый курсу по алгоритмам и структурам данных. Здесь будут выкладываться разборы задач с контестов, текущий рейтинг группы и, если будет необходимо, ссылки на всякий полезный для понимания курса материал.<br>
К тому же напомню, что основное в нашем курсе - это изучение алгоритмов и структур данных. В перспективе вы можете перейти на другой язык программирования, который будет для Вас более удобным. Или это будут требования на работе. Сами алгоритмы от этого не изменятся, поэтому стоит не просто заучивать их код наизусть, а так же понять принцип их работы. Однако, это не означает, что на изучение языка стоит забить. Он является частью нашего курса, и Вы его будете использовать на протяжении как минимум года.<br>

## Подготовка к работе
Для работы Вам понадобится установить компилятор C++ на ваш компьютер. Для удобства написания кода, дебага и тд Вам понадобится удобная среда разработки. Во втором семестре курс проходит на языке Python3.

### Компиляторы С++
#### Linux
Установка через пакетный менеджер.<br>
`sudo apt install g++` - пример для ОС Debian и ее производных. 

#### Windows
[Компилятор MinGW](https://osdn.net/projects/mingw/releases/)<br>
[CygWin](https://cygwin.com/install.html) позволит вам использовать gcc(g++) в Windows. 

#### Mac OS
Возможно, родным компилятором на Mac OS является clang(clang++), но можно поставить gcc(g++).

### Интерпретатор Python
Чистый интрепретатор (без дополнительный модулей) можно скачать с [оф. сайта](https://www.python.org/). На UNIX подобных системах чистый интерпретатор устанавливается через пакетный менеджер. Например:
`sudo apt install python3`<br>
[Anaconda](https://www.anaconda.com/distribution/) - интерпретатор с предустановленным набором библиотек.

### IDE (среда разработки) для C++

[Visual Studio Code](https://code.visualstudio.com/#alt-downloads)<br>
[Xcode](https://developer.apple.com/xcode/) только для Mac OS, вроде платная.<br>
[Clion](https://www.jetbrains.com/clion/download/#section=linux) является платной IDE, но можно получить [студенческую лицензию](https://jetbrains.ru/students/classroom-licenses/free-classroom-licenses/) от JetBrains.<br> 
[CodeBlocks](http://www.codeblocks.org/downloads/binaries)

### IDE для Python
[Visual Studio Code](https://code.visualstudio.com/#alt-downloads)<br>
[PyCharm](https://www.jetbrains.com/pycharm/). Есть как платная (Professional), так и бесплатная (Community) версии. Для получения лицензии см. раздел про Clion выше.<br>
[Spyder](https://www.spyder-ide.org/)

### Решение 2-в-1
В личном кабинете на [mipt.ru](https://mipt.ru) есть инструкция о том, как получть лицензионное ПО от Microsoft. В его число входит Visual Studio со своим компилятором. [Visual Studio](https://visualstudio.microsoft.com/vs/) работает на Windows и Mac OS. Если не ошибаюсь, в VS можно установить поддержку Python. 

## Текущий рейтинг
Таблицу с текущими результатами контестов можно посмотреть тут:
+	[838](Results_838.ipynb)
+	[843](Results_843.ipynb)

## Оформление кода
[C++ code style](theory/cpp_code_style.md).<br>
[PEP8](https://www.python.org/dev/peps/pep-0008/) - общепринятый стандарт по написанию кода на языке Python. [Короткая версия](PEP8_short.pdf).

## Полезные ссылки и теория
1. [E-maxx](http://e-maxx.ru/algo/) - отличный онлайн сборник алгоритмов.
2. [Исчерпывающий список книг для знакомства с C++](https://tproger.ru/books/cpp-books-beginners/) - особенно обратил бы внимение на 1 книгу. Быстро пролистал, вроде норм, но на английском.
3. [Онлайн курс по Python](https://ru.coursera.org/learn/diving-in-python). Курс от Mail.ru и МФТИ. Доступ к просмотру видео, вроде, является бесплатным. В курсе довольно хорошо рассказываются основы языка + примеры. Для тех, кому интересно, дальше освещаются темы, которые в нашем курсе не затрагиваются.
4. [Документация по Python3](https://docs.python.org/3/) - тут есть вся информация о встроенных функциях и стандартных библиотеках. Кроме этого там можно найти хороший туториал.
5. [Теория по динамическому программированию](theory/dp.ipynb). Так же почитать можно [тут](https://neerc.ifmo.ru/wiki/index.php?title=Динамическое_программирование).
6. [Хеш и хеш-таблицы](theory/Hash.pdf).
​
## Разбор задач
1. [Основы языка C++](solutions/lab4.md)
2. [Анализ числовых последовательностей](solutions/lab5.md)
3. [Арифметика с плавающей запятой](solutions/lab6.ipynb)
4. [Массивы](solutions/lab7.md)
5. [Контрольная работа №1](solutions/cw1.md)
6. [Матрицы](solutions/lab9.md)
7. [Рекурсия](solutions/lab12.md)
8. [Работа со строками, Z-функция и КМП](solutions/lab20.ipynb)
9. [Словари и множества в Python](solutions/lab22.ipynb)

## Контакты со мной
Абрамов Максим Петрович<br>
+7(929)574-91-51<br>
<a href="mailto:maksim.abramov@phystech.edu">maksim.abramov@phystech.edu</a><br>
<a href="https://vk.com/stiimo">https://vk.com/stiimo</a>
