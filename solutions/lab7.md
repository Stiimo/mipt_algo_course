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

## Упражнение №9
## Упражнение №10
## Упражнение №11
## Упражнение №12
## Упражнение №13
## Упражнение №14
## Упражнение №15
## Упражнение №16
## Упражнение №17