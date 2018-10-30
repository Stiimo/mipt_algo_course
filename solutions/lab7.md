# Массивы
## Упражнение №1

```cpp
#include <fstream>

using namespace std;

int main() {
    int a[10] = {0};
    ofstream fout("out.txt");
    for (int i = 0; i < 10; i++) {
        fout << a[i] << ' ';
    }
    fout.close();
    return 0;
}
```
## Упражнение №2
Пример со статическим массивом, пример с динамическим будет в 3 упражнении.

```cpp
#include <fstream>

using namespace std;

int main() {
    int a[10][20] = {{0}};
    ofstream fout("out.txt");
    for (int i = 0; i < 10; i++) {
        for (int j = 0; j < 20; j++) {
            fout << a[i][i] << ' ';
        }
        fout << endl;
    }
    fout.close();
    return 0;
}
```

## Упражнение №3
При работе с динамической памятью не забывам ее освобождать!

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    int n = rand() % 9 + 2;
    int m = rand() % 9 + 2;
    int **a = new int*[n];
    for (int i = 0; i < n; i++) {
        a[i] = new int[m];
        for (int j = 0; j < m; j++) {
            a[i][j] = rand() % 11 - 5;
        }
    }
    ofstream fout("out.txt");
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            fout << a[i][j] << ' ';
        }
        fout << endl;
    }
    fout.close();
    for (int i = 0; i < n; i++) {
        delete[] a[i];
    }
    delete[] a;
    return 0;
}
```

## Упражнение №4

```cpp
#include <iostream>

using namespace std;

int f(int a) {
    int s = 0;
    int k = -1;
    while (s <= a) {
        k += 2;
        s += k * (k+1);
    }
    return k;
}

int main() {
    int a;
    cin >> a;
    cout << f(a) << endl;
    return 0;
}
```

## Упражнение №5

```cpp
#include <iostream>

using namespace std;

int digit_sum(int n) {
    int s = 0;
    while (n) {
        s += n % 10;
        n /= 10;
    }
    return s;
}

int main() {
    int n;
    cin >> n;
    cout << digit_sum(n) << endl;
    return 0;
}
```

## Упражнение №6

```cpp
#include <iostream>

using namespace std;

int count_1s(int n) {
    int s = 0;
    while (n) {
        s += n % 2;
        n /= 2;
    }
    return s;
}

int main() {
    int n;
    cin >> n;
    cout << count_1s(n) << endl;
    return 0;
}
```

## Упражнение №7

```cpp
#include <iostream>

using namespace std;

int f(int a) {
    int s = 0;
    int fact = 1;
    int k = 0;
    while (s <= a) {
        k++;
        fact *= k;
        s += fact;
    }
    return k;
}

int main() {
    int a;
    cin >> a;
    cout << f(a) << endl;
    return 0;
}
```

## Упражнение №8

```cpp
#include <iostream>

using namespace std;

int main() {
    int a;
    cin >> a;
    int *factor = new int[a];
    int count = 0;
    for (int i = 2; i <= a; i++) {
        while (a % i == 0) {
            factor[count++] = i;
            a /= i; 
        }
    }
    for (int i = 0; i < count; i++) {
        cout << factor[i] << ' ';
    }
    cout << endl;
    delete[] factor;
    return 0;
}
```

## Упражнение №10
Писал задачу, считывая сначала кол-во элементов, иначе сложно тестировать.

```cpp
#include <iostream>
#include <string>
#include <sstream>  // Необходимо для ostringstream 

using namespace std;

int main() {
    int n;
    cin >> n;
    int *a = new int[n];
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    int s = 0;
    for (int i = 0; i < n; i++) {
        ostringstream str_out;  // Аналогично stdout и ofstream, только для строк
        str_out << hex << a[i];  // std::hex подтягивается библиотеками iostream и sstream
        string str = str_out.str();
        if (str.length() == 3 && str[2] >= 'a' && str[2] <= 'f') {
            s += a[i];
        }
    }
    cout << s << endl;
    delete[] a;
    return 0;
}
```

## Упражнение №11

```cpp
#include <iostream>

using namespace std;

int main() {
    int n;
    cin >> n;
    int *a = new int[n];
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    int balance = 0;
    int min_even = 10000;
    int min_odd = 10000;
    for (int i = 0; i < n; i++) {
        if (a[i] % 2) {
            balance++;
            if (a[i] < min_odd) {
                min_odd = a[i];
            }
        } else {
            balance--;
            if (a[i] < min_even) {
                min_even = a[i];
            }
        }
    }
    if (balance < 0) {
        cout << min_odd << endl;
    } else {
        cout << min_even << endl;
    }
    delete[] a;
    return 0;
}
```

## Упражнение №12
Определение пары дано у упр. №13. Тогда для подсчета кол-ва пар посчитаем кол-во элементов, оканчивающихся на 3. Пусть их будет `m` штук. Искомое кол-во пар равно `K = (n - 1) + (n - 2) + ... + (n - m)`, которое можно посчитать через формулу суммы арифметической прогрессии.

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    int n = 1000 + rand() % 1001;
    ofstream fout("out.txt");
    int m = 0;
    for (int i = 0; i < n; i++) {
        int x = rand() % 1001;
        if (x % 10 == 3) {
            m++;
        }
    }
    fout << (m - 1) * m / 2 << endl;
    fout.close();
    return 0;
}
```

## Упражнение №13
Необходимые пары можно образовать двумя способами:
1. Одно из чисел должно быть кратно 26;
2. Одно из чисел должно быть кратно 13, другое 2.

Кол-во пар для 1 случая считается аналогично парам в упр. №12. Кол-во пар для 2 случая - произведение кол-ва чисел, кратных 13, на кол-во чисел, кратных 2.

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    int n = 1000 + rand() % 1001;
    ofstream fout("out.txt");
    int d_26 = 0;
    int d_13 = 0;
    int d_2 = 0;
    for (int i = 0; i < n; i++) {
        int x = rand() % 1001;
        if (x % 26 == 0) {
            d_26++;
        } else if (x % 13 == 0) {
            d_13++;
        } else if (x % 2 == 0) {
            d_2++;
        }
    }
    // Кол-во пар с числами, кратными 26
    int ans = (d_26 - 1) * d_26 / 2;

    // Прибавим кол-во пар м/у числами кратными 2 и 13
    ans += d_13 * d_2;

    fout << ans << endl;
    fout.close();
    return 0;
}
```

## Упражнение №14

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    ofstream fout("out.txt");
    int n = 0;
    int x = rand() % 1001;
    int sr_count = 0;
    int start;
    int prev;
    while (x) {
        n++;
        if (n > 1 && x < prev) {
            if (start < prev - start) {
                sr_count++;
            }
            start = x;
        } 
        prev = x;
        x = rand() % 1001;
    }
    if (start < prev - start) {
        sr_count++;
    }

    fout << "Получено чисел: " << n << endl;
    fout << "Значительных подъемов: " << sr_count << endl;
    fout.close();
    return 0;
}
```

## Упражнение №15
Задание с очень запутанным условием. Как я понял, из заданного множества чисел надо выбрать подмножество чисел, дающих максимальную нечетную сумму. ПОдмножество должно быть минимально. Для решения мы будем брать все четные числа, кроме 0. В итоге получим четную сумму. Для нечетности суммы надо нечетное кол-во нечетных чисел. В сумму мы будем добавлять нечетные числа, которые больше минимального. Если, дойдя до конца последовательности, мы добавили в сумму четное кол-во нечетных чисел, то добавляем минимальное.

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    int n = 3 + rand() % 1001;
    ofstream fout("out.txt");
    int min_odd = 1001;
    int odd_count = 0;
    for (int i = 0; i < n; i++) {
        int x = rand() % 1001;
        if (x == 0) {
            continue;
        }
        if (x % 2 == 0) {
            fout << x << ' ';
        } else if (x < min_odd) {
            if (odd_count > 0) {
                fout << min_odd << ' ';
            }
            min_odd = x;
            odd_count++;
        } else {
            fout << x << ' ';
        }
    }
    if (odd_count % 2) {
        fout << min_odd;
    }

    fout.close();
    return 0;
}
```

## Упражнение №16
Т.к. мы не можем обрабатывать положительные числа сразу, нам придется их где-нибудь хранить. В связи с тем, что их кол-во может быть большим, просто будем их выводить во временный файл. Потом просто оттуда перепечатаем в выходной. Отрицательные числа печатаем сразу. Т.к. про нули ничег оне сказано, я просто запоминал их кол-во и печатал м/у положительными и отрицательными.

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    int n = 1000 + rand() % 1001;
    ofstream fout("out.txt");
    ofstream tmp("tmp.txt");
    int m = 0;
    int z = 0;
    for (int i = 0; i < n; i++) {
        int x = rand() % 1001 - 500;
        if (x == 0) {
            z++;
        } else if (x > 0) {
            tmp << x << ' ';
            m++;
        } else {
            fout << x << ' ';
        }
    }
    tmp.close();
    for (int i = 0; i < z; i++) {
        fout << "0 ";
    }
    ifstream fin("tmp.txt");
    for (int i = 0; i < m; i++) {
        int x;
        fin >> x;
        fout << x << ' ';
    }
    fin.close();
    fout.close();
    return 0;
}
```

## Упражнение №17
Для решения задачи нам понадобится формула его площади: полупроизведение основания на высоту. Далее мы будем одновременно решать задачу поиска макс. треугольника для нижней и верхней полуплоскости отдельно. В каждой полуплоскости мы находим точку, максимально отдаленную от оси Oy. И находим две точки на оси Ox, лежащие на максимальном расстоянии друг от друга. Таким образом мы надем максимальные треугольники в каждой полуплоскости, удовлетворяющие условиям задачи. Для ответа необходимо выбрать наибольший из двух треугольников. 

```cpp
#include <iostream>
#include <cmath>

using namespace std;

int main() {
    int n;
    cin >> n;
    int pos_h = 0, pos_min = 0, pos_max = 0;
    int neg_h = 0, neg_min = 0, neg_max = 0;
    for (int i = 0; i < n; i++) {
        int x, y;
        cin >> x >> y;
        if (y == 0) {
            continue;
        }
        if (y > 0) {
            if (abs(x) > pos_h) {
                pos_h = abs(x);
            } else if (x == 0) {
                if (y < pos_min || pos_min == 0) {
                    pos_min = y;
                }
                if (y > pos_max || pos_max == 0) {
                    pos_max = y;
                }
            }
        } else {
            if (abs(x) > neg_h) {
                neg_h = abs(x);
            } else if (x == 0) {
                if (y < neg_min || neg_min == 0) {
                    neg_min = y;
                }
                if (y > neg_max || neg_max == 0) {
                    neg_max = y;
                }
            }
        }
    }
    cout << std::max(pos_h * (pos_max - pos_min) / 2.0, 
                     neg_h * (neg_max - neg_min) / 2.0) << endl;
    return 0;
}
```
