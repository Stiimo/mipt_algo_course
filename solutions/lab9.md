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
