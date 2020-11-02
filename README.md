# MIPT algo course
Добро пожаловать в репозиторий, посвященый курсу по алгоритмам и структурам данных.
Здесь будут выкладываться ссылки на всякий полезный для понимания курса материал.<br>
К тому же напомню, что основное в нашем курсе - это изучение алгоритмов и структур данных.
В перспективе вы можете перейти на другой язык программирования, который будет для Вас более удобным.
Или это будут требования на работе.
Сами алгоритмы от этого не изменятся, поэтому стоит не просто заучивать их код наизусть, а так же понять принцип их
работы. Однако, это не означает, что на изучение языка стоит забить.
Он является частью нашего курса, и Вы его будете использовать на протяжении как минимум года.

## Подготовка к работе
Для работы вам понадобится установить интерпретатор Python 3 на ваш компьютер.
Для удобства написания кода, дебага и тд вам понадобится удобная среда разработки.

### Интерпретатор Python
Чистый интрепретатор (без дополнительный модулей) можно скачать с [оф. сайта](https://www.python.org/).
На UNIX подобных системах чистый интерпретатор устанавливается через пакетный менеджер. Например для Ubuntu и его
производных: `sudo apt install python3`<br>
[Anaconda](https://www.anaconda.com/distribution/) - интерпретатор с предустановленным набором библиотек.

### IDE (среда разработки)
[Visual Studio Code](https://code.visualstudio.com/#alt-downloads)<br>
[PyCharm](https://www.jetbrains.com/pycharm/). Есть как платная (Professional), так и бесплатная (Community) версии.
Можно получить [студенческую лицензию](https://jetbrains.ru/students/classroom-licenses/free-classroom-licenses/) от
JetBrains.<br>
[Spyder](https://www.spyder-ide.org/)<br>
[Visual Studio](https://visualstudio.microsoft.com/vs/).
В личном кабинете на [mipt.ru](https://mipt.ru) есть инструкция о том, как получить лицензионное ПО от Microsoft.
Обычно VS используется для программирования на C++ и C#, но он поддерживает и Python (возможно потребуется установка
дополнительных модулей).

## Полезные ссылки
1. [E-maxx](http://e-maxx.ru/algo/) - отличный онлайн сборник алгоритмов.
2. [Онлайн курс по Python](https://ru.coursera.org/learn/diving-in-python). Курс от Mail.ru и МФТИ. Доступ к просмотру
видео, вроде, является бесплатным. В курсе довольно хорошо рассказываются основы языка + примеры. Для тех, кому
интересно, дальше освещаются темы, которые в нашем курсе не затрагиваются.
3. [Документация по Python3](https://docs.python.org/3/) - тут есть вся информация о встроенных функциях и стандартных
библиотеках. Кроме этого там можно найти хороший туториал.
4. [PEP8](https://www.python.org/dev/peps/pep-0008/) - общепринятый стандарт по написанию кода на языке Python.
[Короткая версия](PEP8_short.pdf).
5. [Дискретная оптимизация](discrete_optimization.pdf) - неплохой учебник, в котором часть темы по временной сложности
и около того. Кроме этого, там есть материалы по теории графов и не только.
6. [Викиконспекты](https://neerc.ifmo.ru/wiki) - материалы программированию и алгоритмам университета ИТМО.

## Теория по алгоритмам
Большая часть теории основана на материалах E-maxx, Викиконспектов, которые в свою очередь основываются на материалах
книги авторства Томаса Кормена и др. Алгоритмы: Построение и анализ.

0. [Временная сложность](theory/complexity.pdf) (пока только на англ., материал на русском смотрите в учебнике по
дискретной оптимизации)
1. Теория чисел
    1. [Алгоритм Евклида](theory/euclidean_algorithm.pdf)
    2. [Решето Эратосфена](theory/sieve_of_eratosthenes.pdf)
    3. Расширенный алгоритм Евклида
2. Сортировки и поиск
    1. [Квадратичные сортировки](theory/quadratic_sortings.pdf)
    2. [Сортировки с квазилинейной сложностью](theory/quasilinear_sortings.pdf)
    3. [Сортировки для особых случаев](theory/spec_case_sortings.pdf)
    4. [Поиск элементов в массиве](theory/searches.pdf)
3. Алгоритмы на строки
    1. [Префикс-функция](https://e-maxx.ru/algo/prefix_function)
    2. [Z-функция](https://e-maxx.ru/algo/z_function)
    3. Разбор выражений
4. [Динамическое программирование](theory/dp.ipynb). Так же почитать можно [тут](https://neerc.ifmo.ru/wiki/index.php?title=Динамическое_программирование).
5. [Хеширование](theory/hashing_ru.pdf)
6. Графы
    1. [Хранение графов](theory/graph_storage_ru.pdf)
    2. [Обходы](theory/graph_traverse_ru.pdf)
    3. [Пути минимального веса](theory/graph_shortest_ru.pdf)
    4. [Остовные деревья](theory/mst_ru.pdf)
    5. Асимптотически сложные задачи
7. Теория игр
8. Структуры данных
    1. [Связные списки](theory/ll_ru.pdf)
    2. [Куча](theory/heap_ru.pdf)
    3. [Система непересекающихся множеств](https://e-maxx.ru/algo/dsu)
    4. Двоичные деревья поиска

## Algorithms theory
Theese articles mostly based on E-maxx, neerc.ifmo.ru, which are based on Thomas Korman's book Introduction to
ALgorithms.

0. [Time complexity](theory/complexity.pdf)
1. Number theory
    1. Euclidean algorithm
    2. Sieve of Eratosthenes
    3. Extended Euclidean algorithm
2. Sortings and searches
    1. Quadratic
    2. Quasilinear
    3. Sortings for special cases
    4. Elements search in array
3. String algorithms
    1. Prefix function
    2. Z function
    3. Tokenization
4. Dynamic programming
5. [Hashing](theory/hashing_en.pdf)
6. Graphs theory
    1. Storage in memory
    2. Traverse
    3. Shortest paths
    4. Minimum spanning trees
    5. Асимптотически сложные задачи
7. Game theory
8. Data structures
    1. [Linked lists](theory/ll_en.pdf)
    2. Heap
    3. Disjoint set union
    4. Binary search trees

## Контакты со мной
Абрамов Максим Петрович<br>
+7(929)574-91-51<br>
Telegram: @stiimo<br>
<a href="mailto:maksim.abramov@phystech.edu">maksim.abramov@phystech.edu</a><br>
<a href="https://vk.com/stiimo">https://vk.com/stiimo</a><br>
