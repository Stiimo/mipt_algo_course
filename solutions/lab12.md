# Квадратичные сортировки
## Задача A
В этой задаче по факту решение можно вычислить с помощью формулы. Однако, по условию требуется использовать рекурсию. В решении я просто заменил рекурсивные вызов функции циклом. Для решения необходимо вычислить сумму `M-1` членов арифметической прогресии `K, K+1, K+2, ...`, умножить результат на 2 и прибавить `K+M-1`.

```cpp
#include <iostream>

using namespace std;

int main() {
    int k, m;
    cin >> k >> m;
    int ans = k + m - 1;
    for (int i = 0; i < m - 1; i++) {
        ans += (k + i) * 2; 
    }
    cout << ans << endl;
    return 0;
}
```

## Задача B
Основная сложность задачи в том, что две формулы выражаются друг через друга. Для того, чтобы написать такие функции и все компилировалось, просто надо написать сначала прототипы функций (строки 3 и 4).

```cpp
#include <iostream>

int F(int n);
int M(int n);

using namespace std;

int main() {
    int n;
    cin >> n;
    cout << F(n) << ' ' << M(n) << endl;
    return 0;
}

int F(int n) {
    if (n == 0) {
        return 1;
    }
    return n - M(F(n-1));
}

int M(int n) {
    if (n == 0) {
        return 0;
    }
    return n - F(M(n-1));
}

```

## Задача C

```cpp
#include <iostream>

using namespace std;

int main() {
    int n, k;
    cin >> n >> k;
    int *a = new int[n+1]();
    for (int i = 0; i < n; i++) {
        a[i] = i + 1;
    }
    int last = 0;
    while (n > 1) {
        last = (k % n + last - 1 + n) % n;
        n--;
        for (int i = last; i < n; i++) {
            a[i] = a[i+1];
        }
        last %= n;
    }
    cout << a[0] << endl;
    delete[] a;
    return 0;
}
```

##  Задача D
Наверное, самая сложная задача в этом контесте. Тут требуется использовать рекурсию с мемоизацией, иначе можно получить TL. Сложность заключается в реализации этой самой мемоизации. Удобне всего использовать std::vector, котором можно прочитать [тут](http://www.cplusplus.com/reference/vector/vector/).

```cpp
#include <iostream>
#include <sstream>
#include <string>
#include <vector>

using namespace std;

vector<string> f(int n, vector<string> *d, vector<string> *d_r);
vector<string> f_r(int n, vector<string> *d, vector<string> *d_r);

int main() {
    int n;
    cin >> n;
    vector<string> *d = new vector<string>[n]();
    vector<string> *d_r = new vector<string>[n]();
    f(n, d, d_r);
    for (int i = 0; i < d[n-1].size(); i++) {
        cout << d[n-1][i];
    }
    delete[] d;
    delete[] d_r;
    return 0;
}

vector<string> f(int n, vector<string> *d, vector<string> *d_r) {
    if (!d[n-1].empty()) {
        return d[n-1];
    }
    if (n == 1) {
        d[0].push_back("1 1 2\n");
        d[0].push_back("1 2 3\n");
        return d[0];
    }
    vector<string> r = f(n-1, d, d_r);
    d[n-1].insert(d[n-1].end(), r.begin(), r.end());
    ostringstream s;
    s << n;
    d[n-1].push_back(s.str() + " 1 2\n");
    r = f_r(n-1, d, d_r);
    d[n-1].insert(d[n-1].end(), r.begin(), r.end());
    d[n-1].push_back(s.str() + " 2 3\n");
    r = f(n-1, d, d_r);
    d[n-1].insert(d[n-1].end(), r.begin(), r.end());
    return d[n-1];
}

vector<string> f_r(int n, vector<string> *d, vector<string> *d_r) {
    if (!d_r[n-1].empty()) {
        return d_r[n-1];
    }
    if (n == 1) {
        d_r[0].push_back("1 3 2\n");
        d_r[0].push_back("1 2 1\n");
        return d_r[0];
    }
    vector<string> r = f_r(n-1, d, d_r);
    d_r[n-1].insert(d_r[n-1].end(), r.begin(), r.end());
    ostringstream s;
    s << n;
    d_r[n-1].push_back(s.str() + " 3 2\n");
    r = f(n-1, d, d_r);
    d_r[n-1].insert(d_r[n-1].end(), r.begin(), r.end());
    d_r[n-1].push_back(s.str() + " 2 1\n");
    r = f_r(n-1, d, d_r);
    d_r[n-1].insert(d_r[n-1].end(), r.begin(), r.end());
    return d_r[n-1];
}

```

## Задача E
Поиск определителя по [теореме Лапласа](https://ru.wikipedia.org/wiki/%D0%A2%D0%B5%D0%BE%D1%80%D0%B5%D0%BC%D0%B0_%D0%9B%D0%B0%D0%BF%D0%BB%D0%B0%D1%81%D0%B0).

```cpp
#include <iostream>

using namespace std;

long long det(int **a, int k, bool *c, int n) {
    if (k + 1 == n) {
        for (int i = 0; i < n; i++) {
            if (!c[i]) {
                return a[k][i];
            }
        }
    }
    long long res = 0;
    int sign = 1;
    for (int i = 0; i < n; i++) {
        if (!c[i]) {
            c[i] = true; 
            res += sign * a[k][i] * det(a, k+1, c, n);
            c[i] = false;
            sign *= -1; 
        }
    }
    return res;
}

int main() {
    int n;
    cin >> n;
    int **a = new int*[n];
    for (int i = 0; i < n; i++) {
        a[i] = new int[n];
        for (int j = 0; j < n; j++) {
            cin >> a[i][j];
        }
    }
    bool *cols = new bool[n]();
    cout << det(a, 0, cols, n) << endl;
    delete[] cols;
    for (int i = 0; i < n; i++) {
        delete[] a[i];
    }
    delete[] a;
    return 0;
}
```
