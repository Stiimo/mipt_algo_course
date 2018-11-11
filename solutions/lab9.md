# Матрицы
## Упражнение №1
Код функции main будет аналогичен предложенному в упражнении №2.

## Упражнение №2

```cpp
void good_incrementor(int *x) {
    (*x)++;
}
```

## Упражнение №3

```cpp
void mul(double **a, int **b, double **c, int m, int n, int k) {
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < k; j++) {
            for (int h = 0; h < n; h++) {
                c[i][j] += a[i][h] * b[h][j];
            }
        }
    }
}

void mul(double **a, double **b, double **c, int m, int n, int k) {
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < k; j++) {
            for (int h = 0; h < n; h++) {
                c[i][j] += a[i][h] * b[h][j];
            }
        }
    }
}

void f(int m, int n, int k) {
    // #1
    double **c = new double*[m];
    for (int i = 0; i < m; i++) {
        c[i] = new double[k]();
    }

    // #2
    double **a = new double*[m];
    for (int i = 0; i < m; i++) {
        a[i] = new double[n];
        for (int j = 0; j < n; j++) {
            a[i][j] = i + j;
        }
    }

    // #3
    int **b = new int*[n];
    for (int i = 0; i < n; i++) {
        b[i] = new int[k];
        for (int j = 0; j < k; j++) {
            b[i][j] = (int)(i == j);
        }
    }

    cout.precision(2);
    cout.setf(ios::fixed);
    // #4
    mul(a, b, c, m, n, k);
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < k; j++) {
            cout << c[i][j] << ' ';
        }
        cout << endl;
    }

    // #5
    double **t = new double*[k];
    for (int i = 0; i < k; i++) {
        t[i] = new double[m]();
    }

    for (int i = 0; i < m; i++) {
        for (int j = 0; j < k; j++) {
            t[j][i] = c[i][j];
        }
        delete[] c[i];
    }
    delete[] c;
    c = t;

    for (int i = 0; i < k; i++) {
        for (int j = 0; j < m; j++) {
            cout << c[i][j] << ' ';
        }
        cout << endl;
    }

    // #6
    if (m == k) {
        int x;
        cin >> x;
        t = new double*[m];
        for (int i = 0; i < m; i++) {
            t[i] = new double[m]();
            for (int j = 0; j < m; j++) {
                t[i][j] = c[i][j];
            }
        }
        for (int iter = 0; iter < x; iter++) {
            double **q = new double*[m];
            for (int i = 0; i < m; i++) {
                q[i] = new double[m]();
            }
            mul(c, t, q, m, m, m);
            for (int i = 0; i < m; i++) {
                delete[] t[i];
            }
            delete[] t;
            t = q;
        }

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < k; j++) {
                cout << t[i][j] << ' ';
            }
            cout << endl;
        }   
        for (int i = 0; i < m; i++) {
            delete[] t[i];
        }
        delete[] t;
    }

    // #7
    for (int i = 0; i < m; i++) {
        delete[] a[i];
    }
    delete[] a;
    for (int i = 0; i < n; i++) {
        delete[] b[i];
    }
    delete[] b;
    for (int i = 0; i < k; i++) {
        delete[] c[i];
    }
    delete[] c;
}
```

## Упражнение №5
К упраженениям №№5-8 код расписывать не буду, т.к. он получается путем необльших модификация кода из лабы.


## Упражнение №6
Для вычисления определителя достаточно привести матрицу к единичной. Когда мы очередную строку делим на число, чтобы получить на диагонали `1`, мы запоминаем это число. Тогда определитль равен произведению этих чисел. Только стоит заметить, что некоторые строки и столбцы могуть быть полностью заполнены `0`, тогда определитель равен `0`. Ранг матрицы - кол-во ненулевых элементов в нашей диагональной матрице. Для получения обратной матрицы создаем единичную матрицу. Далее начинаем приводить нашу матрицу в единичной, применяя такие же операции к единичной. В результате получим обратную матрицу.

## Упражнение №7
Система будет несовместной в случае, если нулевой строке матрицы будет соответствовать ненулевой элемент в векторе-столбце свободных коэффициентов.

## Упражнение №8
Если нулевой строке матрицы будет соответствовать нулевой элемент в векторе-столбце свободных коэффициентов, то мы получаем бесконечное множество решений


## Упражнение №9

```cpp
#include <cmath>

using namespace std;

double dot(double *u, double *v, int n) {
    double ans = 0.0;
    for (int i = 0; i < n; i++) {
        ans += u[i] * v[i];
    }
    return ans;
}

double* cross(double *u, double *v) {
    double *t = new double[3];
    t[0] = u[1] * v[2] - u[2] * v[1];
    t[1] = u[2] * v[0] - u[0] * v[2];
    t[2] = u[0] * v[1] - u[1] * v[0];
    return t;
}

double project(double *u, double *v, int n) {
    double len = 0;
    for (int i = 0; i < n; i++) {
        len += v[i] * v[i];
    }
    len = sqrt(len);
    return dot(u, v, n) / len;
}

double* add(double *u, double *v, int n) {
    double *t = new double[n];
    for (int i = 0; i < n; i++) {
        t[i] = u[i] + v[i];
    }
    return t;
}
```

## Упражнение №10
Для решения пунктов 5-8 необходимо воспользоваться знаниями из аналитической геометрии и некоторыми написанными ранее функциями.

```cpp
#include <cmath>

// p - точка на прямой
// v - направляющий вектор
// q - точка, от которой необходимо найти расстояние до прямой
double distance2line(double *p, double *v, double *q) {
    double len = sqrt(v[0] * v[0] + v[1] * v[1]);
    return (v[1] * q[0] - v[0] * q[1] + v[0] * p[1] - v[1] * p[0]) / len;
}

// p - точка на плоскости
// v - нормаль к плоскости
// q - точка, от которой необходимо найти расстояние до плоскости
double distance2plane(double *p, double *v, double *q) {
    double len = sqrt(v[0] * v[0] + v[1] * v[1] + v[2] * v[2]);
    return (v[0] * q[0] + v[1] * q[1] + v[2] * q[2] - (v[0] * p[0] + v[1] * p[1] + v[2] * p [2])) / len;
}

// p, q, r - точки на плоскости
// Функция cross из упражнения №9. 
double* plane_normal(double *p, double *q, double *r) {
    double *u = new double[3];
    u[0] = q[0] - p[0];
    u[1] = q[1] - p[1];
    u[2] = q[2] - p[2];

    double *v = new double[3];
    v[0] = r[0] - p[0];
    v[1] = r[1] - p[1];
    v[2] = r[2] - p[2];

    double *t = cross(u, v);
    delete[] u;
    delete[] v;
    double len = sqrt(t[0] * t[0] + t[1] * t[1] + t[2] * t[2]);
    t[0] /= len;
    t[1] /= len;
    t[2] /= len;
    return t;
}

// u, v - направляющие векторы
// Функция dot из упражнения №9.
double angle_btw_lines(double *u, double *v) {
    double len_u = sqrt(u[0] * u[0] + u[1] * u[1]);
    double len_v = sqrt(v[0] * v[0] + v[1] * v[1]);
    return acos(dot(u, v, 2) / len_u / len_v);
}

// u - направляющий вектор прямой
// v - нормаль к плоскости
double angle_btw_line_and_plane(double *u, double *v) {
    double len_u = sqrt(u[0] * u[0] + u[1] * u[1]);
    double len_v = sqrt(v[0] * v[0] + v[1] * v[1]);
    return asin(dot(u, v, 2) / len_u / len_v);
}

// u, v - нормали к плоскостям
double angle_btw_planes(double *u, double *v) {
    double len_u = sqrt(u[0] * u[0] + u[1] * u[1]);
    double len_v = sqrt(v[0] * v[0] + v[1] * v[1]);
    return acos(dot(u, v, 2) / len_u / len_v);
}
```

## Упражнение №11
Для решения просто необходимо запрограммировать те действия, которые вы бы выполняли для вычисления результата преобразования.
