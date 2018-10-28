# Арифметика с плавающей запятой
## Упражнение №1
Формула генерации случайного числа из отрезка [l, r]: $\frac{rand()}{RAND_MAX}(r-l) + l$. Напоминаю, что запись вида $Be+N$ эквивалентна $B*e^N$. 

```cpp
#include <fstream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL));
    ofstream fout("in.txt");
    fout << (double)rand() / (double)RAND_MAX * 10.0 + 0.1 << ' '
         << (double)rand() / (double)RAND_MAX * 1e+3 + 1e+6 << ' '
         << (double)rand() / (double)RAND_MAX * 1e+9 + 1e+12;
    fout.close();
    
    ifstream fin("in.txt");
    double a, b, c;
    fin >> a >> b >> c;
    fin.close();
    fout.open("out.txt");
    fout << a << endl << b << endl << c << endl
         << (a + b) + c << endl
         << (c + b) + a << endl
         << (c + a) + b << endl;
    fout.close();
    return 0;
}
```

## Упражнение №2 
```cpp
#define _USE_MATH_DEFINES  // Необходимо для использования констант
#include <iostream>
#include <cmath>

using namespace std;

int main() {
    double pi_arc = 1.0 + 5.0 / 3.0;  // 0-ой и 1-ый члены ряда
    double pi = 0.0;
    for (int i = 2; i <= 20; i++) {
        double x = 8.0 / ((2*i-3) * (2*i-1) * (2*i+1)); 
        if (i % 2) {
            pi_arc -= x;
        } else {
            pi_arc += x;
        }
    }
    for (int i = 0; i <= 20; i++) {
        if (i % 2) {
            pi -= 1.0 / (2.0 * i + 1.0);
        } else {
            pi += 1.0 / (2.0 * i + 1.0);
        }
    }
    pi *= 4.0;
    cout << "PI from arctan formula: " << pi_arc << endl;
    cout << "PI from pi formula: " << pi << endl;
    cout << "PI from cmath: " << M_PI << endl;
    return 0;
}
```

## Упражнение №3
Для вычисления корня необходимо посчитать сумму ряда $(1+x)^\alpha$, где $x=729, \alpha=\frac{1}{3}$. Вынесем 729 за скобки, получим $729^\frac{1}{3}*(1+\frac{1}{729})^\frac{1}{3}$. $(1+x)^\alpha=\sum_{n=0}^{\infin} {\alpha \choose n} x^n$, где ${\alpha \choose n}=\prod_{k=1}^{n} \frac{\alpha-k+1}{k}, |x|<1$.

```cpp
#include <iostream>

using namespace std;

int main() {
    double f = 0.0;  // Сумма ряда
    double delta = 1.0; 
    double i = 1.0;
    while (abs(delta) > 1e-6) {
        f += delta;
        delta *= (1.0 / 3.0 - i + 1) / i / 729.0;
        i += 1.0;
    }
    cout << 9.0*f << endl;
    return 0;
}
```

## Упраженение №4
В этом задании надо численно посчитать значение интеграла для какой-нибудь функции (я выбрал $f(x)=x^3$) двумя методами: Симпсона и Гаусса (не Эйлера!). С методами можно ознакомиться на Википедии.

```cpp
#include <fstream>
#include <cmath>

using namespace std;

double f(double x) {
    return x*x*x;
}

int main() {
    double acc_val = 1.0 / 4.0;
    double simpson_val = (1.0 + 4 * f(0.5)) / 6.0;
    double gauss_val = (f(0.5 - 0.5/sqrt(3.0)) + f(0.5 + 0.5/sqrt(3.0))) / 2.0;
    ofstream fout("out4.txt");
    fout << "Accurate value: " << acc_val << endl;
    fout << "2p simpson method: " << simpson_val <<  " Error: " << acc_val - simpson_val << endl;
    fout << "2p gauss method: " << gauss_val <<  " Error: " << acc_val - gauss_val << endl;
    
    // Разобьем отрезок на 100 отрезков и заного вычислим интеграл 
    simpson_val = 0.0;
    gauss_val = 0.0;
    for (double i = 0.0; i < 1.0; i += 0.01) {
        simpson_val += 0.01 * (f(i) + 4*f((2*i + 0.01)/2) + f(i+0.01)) / 6.0;
        gauss_val += 0.01 * (f((2*i + 0.1) / 2.0 - 0.005/sqrt(3.0)) + f((2*i + 0.1) / 2.0 + 0.005/sqrt(3.0))) / 2.0;
    }
    fout << "101p simpson method: " << simpson_val <<  " Error: " << acc_val - simpson_val << endl;
    fout << "101p gauss method: " << gauss_val <<  " Error: " << acc_val - gauss_val << endl;
    fout.close();
    return 0;
}
```