# Анализ числовых последовательностей
## Упражнение №1
Данное упражнение не относится к теме лабы, но позволяет научиться работать с аргументами командной строки. Аргументы находятся в массиве argv в формате строк. Для коневертации строк в числа можно использовать ф-ии `int atoi(const char *str)` и `double atof(const char *str)`.

```cpp
#include <iostream>
#include <cstdlib>  // Необходимо для ф-ий atoi и atof

using namespace std;

int main(int argc, char **argv) {
    if (argc == 1) {
        cout << "No arguments\n";
    } else if (argc == 2) {
        cout << argv[1] << endl;
    } else if (argc == 3) {
        cout << (atoi(argv[1]) + atoi(argv[2])) / 2.0 << endl;
    } else {
        int ans = atof(argv[1]);
        for (int i = 2; i < argc; i++) {
            if (ans < atof(argv[i])) {
                ans = atof(argv[i]);
            }
        }
        cout << ans << endl;
    }
    return 0;
}
```

## Упражнение №2 
Среднее геометрическое - корень n-ой степени произведения n чисел. Для взятия такого корня понадобится функция `double pow(double base, double exponent)`, с помощью которой надо будет вовзвести число в степень 1/n. Часть упражнения с методом `is_open()` пропущена, т.к., на мой взгляд, она не несет в себе смысла.

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>
#include <cmath>  // Необходимо для ф-ии pow

using namespace std;

int main() {
    srand(time(NULL));

    ofstream fout("numbers.txt");
    int n = rand() % 20 + 20;
    for (int i = 0; i < n; i++) {
        fout << rand() % 100 + 1 << ' ';
    }
    fout.close();
    
    ifstream fin("numbers.txt");
    double prod = 1.0;
    for (int i = 0; i < n; i++) {
        int x;
        fin >> x;
        prod *= x;
    }
    fout.open("output.txt");
    fout << pow(prod, 1.0 / n);
    fout.close();
    return 0;
}
```

## Упражнение №3
В упражнении есть 6 отдельных заданий. Показан пример для 1 задания. Над остальными предлагается подумать самостоятельно.

```cpp
#include <fstream>
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));

    ofstream fout("stream.txt");
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) {
        fout << rand() % 1000 + 1 << ' ';
    }
    fout.close();
    
    ifstream fin("stream.txt");
    for (int i = 0; i < n; i++) {
        int x;
        fin >> x;
        if (x % 12 == 0) {
            cout << x << ' ';
        }
    }
    cout << endl;
    return 0;
}
```