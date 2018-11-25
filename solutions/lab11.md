# Квадратичные сортировки
## Задача F
Для решения задачи необходимо отладить представленный код. Единственная проблема, что при считывании не учитывается, что начало отрезка может оказаться больше, чем конец. Поэтому после считывания проверяем, развернут ли отрезок. Если да, то просто меняем его концы местами.

## Задача G

```cpp
Rect* max(Rect *pa, Rect *pb) {
    if (pa->width * pa->height > pb->width * pb -> height) {
        return pa;
    }
    return pb;
}
```

## Задача H

```cpp
int cmp_int(const void * p1, const void * p2) {
    return *(int*)p1 - *(int*)p2;
}
```

##  Задача I

```cpp
int cmp_Point(const void * p1, const void * p2) {
    Point *p = (Point*)p1;
    Point *q = (Point*)p2;
    return (p->x * p->x + p->y * p->y) - (q->x * q->x + q->y * q->y);
}
```

## Задача J
При сравнении строк считается, что например строка "abcd" меньше строки "abcda".

```cpp
#include <iostream>
#include <string>

using namespace std;

struct Row {
    string name;
    int v;
};

int cmp_str(const Row *a, const Row *b) {
    return a->name.compare(b->name);
}

int cmp_int(const Row *a, const Row *b) {
    if (b->v == a->v) {
        return cmp_str(a, b);
    }
    return b->v - a->v;
}

int main() {
    int n;
    cin >> n;
    Row *a = new Row[n];
    for (int i = 0; i < n; i++) {
        cin >> a[i].name >> a[i].v;
    }
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (cmp_str(&a[j], &a[j+1]) > 0) {
                Row t;
                t.name = a[j].name;
                t.v = a[j].v;
                a[j].v = a[j+1].v;
                a[j].name = a[j+1].name;
                a[j+1].name = t.name;
                a[j+1].v = t.v;
            }
        }
    }
    for (int i = 0; i < n; i++) {
        cout << a[i].name << ' ' << a[i].v << endl;
    }
    cout << endl;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (cmp_int(&a[j], &a[j+1]) > 0) {
                Row t;
                t.name = a[j].name;
                t.v = a[j].v;
                a[j].v = a[j+1].v;
                a[j].name = a[j+1].name;
                a[j+1].name = t.name;
                a[j+1].v = t.v;
            }
        }
    }
    for (int i = 0; i < n; i++) {
        cout << a[i].name << ' ' << a[i].v << endl;
    }
    delete[] a;
    return 0;
}
```

## Задача K

```cpp
#include <iostream>
#include <string>

using namespace std;

bool cmp(const string &a, const string &b) {
    if (a.length() < b.length()) {
        if (b[a.length() - 1] == '+') {
            return true;
        }
        return false;
    }
    if (a[b.length() - 1] == '+') {
        return false;
    }
    return true;
}

int main() {
    int n;
    cin >> n;
    string *a = new string[n];
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (cmp(a[j], a[j+1])) {
                string t = a[j];
                a[j] = a[j+1];
                a[j+1] = t;
            }
        }
    }
    for (int i = 0; i < n; i++) {
        cout << a[i].length() << ' ';
    }
    delete[] a;
    return 0;
}
```

## Задача L
Для решения задачи просто сортируем атлетов по возрастанию: сначала массы, потом силы. Для сортировки используем встроенный qsort.

```cpp
#include <iostream>
#include <cstdlib>

using namespace std;

struct Athlete {
    int s, m;
};

int cmp_int(const void *a, const void *b) {
    Athlete *p = (Athlete*)a;
    Athlete *q = (Athlete*)b;
    if (p->m != q->m) {
        return p->m - q->m;
    }
    return p->s - q->s;
}

int main() {
    int n;
    cin >> n;
    Athlete *a = new Athlete[n];
    for (int i = 0; i < n; i++) {
        cin >> a[i].m >> a[i].s;
    }
    qsort(a, n, sizeof(Athlete), cmp_int);
    int c = 0;
    int h = 0;
    for (int i = 0; i < n; i++) {
        if (c <= a[i].s) {
            h++;
            c += a[i].m;
        }
    }
    cout << h << endl;
    delete[] a;
    return 0;
}
```
