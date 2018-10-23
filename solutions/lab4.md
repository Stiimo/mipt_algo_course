# Основы языка C++
## Упражнение №5
Для решения достаточно 6 раз вывести результат оператора sizeof, который показывает размр типа в байтах.

```cpp
#include <iostream>

using namespace std;

int main() {
    cout << "Size of char is " << sizeof(char) << endl;
    cout << "Size of bool is " << sizeof(bool) << endl;
    cout << "Size of short is " << sizeof(short) << endl;
    cout << "Size of int is " << sizeof(int) << endl;
    cout << "Size of long is " << sizeof(long) << endl;
    cout << "Size of long long is " << sizeof(long long) << endl;
    return 0;
}
```

## Упражнение №6 
В упражнении необходимо сгенерировать 2 последовательности случайных чисел. Напоминаю, что rand() генерирует числа от 0 до RAND_MAX (константа, определенная в cstdlib).

```cpp
#include <iostream>
#include <cstdlib>  // Необходимо для функций srand и rand
#include <ctime.h>  // Необходимо для функции time

using namespace std;

int main() {
    // Инициализация генератора случайных чисел `случайным` числом
    /* Функция time возвращает количество секунд с момента 00:00 UTC 1 января 1970
       https://en.wikipedia.org/wiki/Unix_time */
    srand(time(NULL));
    // First part
    for (int i = 0; i < 10; i++) {
        cout << rand() % 6 + 1 << ' ';
    }
    cout << endl;

    // Second part
    for (int i = 0; i < 10; i++) {
        cout << (double)rand() / (double)RAND_MAX * 2.0 + 1.0 << ' ';
    }
    cout << endl;
    return 0;
}
```

## Упражнение №7
Тут необходимо было выводить числа в файл. Для этого используется std::ofstream из библиотеки fstream. Выходной файл создается автоматически, если его нет. Если он есть, то, по умолчанию, полностью перезаписывается. После работы с файлом его **необходимо** закрыть!

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    // First part
    int a = rand() % 101;
    int d = rand() % 101;
    int n = rand() % 101;
    ofstream fout("out1.txt");
    fout << a << ' ' << d << ' ' << n << endl;
    for (int i = 0; i < n; i++) {
        fout << a << ' ';
        a += d;
    }
    fout.close();

    // Second pat
    double b = (double)rand() / (double)RAND_MAX * 4.0 + 1.0;
    double q = (double)rand() / (double)RAND_MAX * 4.0 + 1.0;
    fout = ofstream("out2.txt");
    fout << b << ' ' << q << endl;
    for (int i = 0; i < 10; i++) {
        fout << b << ' ';
        b /= q;
    }
    fout.close();
    return 0;
}
```