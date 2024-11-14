## Отчет по лабораторной работе № 2

#### № группы: `ПМ-2401`

#### Выполнил: `Ядыкин Максим Михайлович`

#### Вариант: `31`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные и выходные данные](#2-входные-и-выходные-данные)
- [Выбор структуры данных](#3-выбор-структуры-данных)
- [Алгоритм](#4-алгоритм)
- [Программа](#5-программа)
- [Анализ правильности решения](#6-анализ-правильности-решения)

### 1. Постановка задачи

> Напишите программу на Java, которая выполняет следующие действия
> с одномерным массивом чисел Фибоначчи:
> 1. Считывает с консоли число N и генерирует массив первых N чисел
Фибоначчи.
> 2. Сортирует массив в порядке возрастания количества цифр в числе.
Если количества цифр равны, сортирует в порядке убывания числа.
> 3. Находит и выводит сумму всех нечётных чисел в массиве
> 4. Выводит элементы массива, заменяя каждое число на его двоичное
представление.
> 5. Заменяет каждое число в массиве на сумму его цифр и выводит
полученный массив.

Данная задача имеет 5 подзадач:
1. Пользователь вводит число N, которое будет задавать длинну массива. Потом при помощи формулы заполняется массив первыми числами последовательности Фибоначчи.
2. Сортировка массива таким образом, что в начале идут однозначные числа по убыванию, потом двузначные по убыванию и т.д. Например: `6, 2, 1, 65, 43, 29, 355, 212...`
3. Находится сумма всех нечетных чисел и выводится на экран.
4. Каждое число переводится в двоичную систему представления и выводится на экран.
5. Находится сумма цифр числа, которая записывается в массив вместо него. Выводится получившийся массив.

### 2. Входные и выходные данные

#### Данные на вход

На вход программа должна получать 1 число, так как это будет длиная массива, то число должно быть натуральным. Вверхняя граница не данна, тогда пусть ей будет 10<sup>9</sup>.

|   | Тип         | min значение    | max значение   |
|---|-------------|-----------------|----------------|
| N | Целое число | 1               | 10<sup>9</sup> |

#### Данные на выход

Т.к. программа должна вывести сумму элементов массива и обработанные элементы массива, а числа Фибоначчи натуральные, то на выход мы получим натуральное число, строка, так как ищем двоичное представление числа, и целочисленный массив.

|                        | Тип                  | min значение | max значение   |
|------------------------|----------------------|--------------|----------------|
| Сумма чисел            | Целое число          | 1            | 10<sup>9</sup> |
| Двоичное представление | Строка               | 1            | 10<sup>9</sup> |
| Массив                 | Целочисленный массив | 1            | 10<sup>9</sup> |

### 3. Выбор структуры данных

Программа получает 1 натуральное число, не меньше 1 и не превышающего 10<sup>9</sup>. Поэтому для его хранения
можно выделить 1 переменную (`n`) типа `int`. Нам нужно сгенерировать последовательность Фибоначчи, числа которой натуральные, значит нужно создать целочисленный массив. 
Создаем еще один целочисленный массив для сортировки. Чтобы получить двоичное представление чисел, выделяем переменну (`y`) типа `String` и выделяем еще одну переменную (`r`) типа `String`, чтобы развернуть строку.

|              | название переменной | Тип (в Java) | 
|--------------|---------------------|--------------|
| N (Число 1)  | `n`                 | `int`        |
| A (Массив 1) | `a`                 | `int`        |
| B (Массив 2) | `b`                 | `int`        |
| Y (Строка 1) | `y`                 | `String`     | 
| R (Строка 1) | `r`                 | `String`     |

### 4. Алгоритм

#### Алгоритм выполнения программы:

1. **Ввод данных:**  
   Программа считывает одно целое число, обозначенное как `n`.

2. **Генерация последовательности:**  
   Программа создает целочисленнй массив `a` длины `n`, в который записывает первые числа Фибоначчи. Первый и второй элемент присваеваются "вручную", остальные генерируются при помощи цикла со счетчиком и реккурентной формулы.

3. **Сортировка массива:**
    - Создается целочисленный массив `b`, куда записывается количество цифр чисел Фибоначчи. Чтобы посчитать количество цифр в числе, нужно задать счетчик и считать сколько раз можно поделить число нацело на 10, пока не останется 0.
    - Перебираем элементы двух массивов, и если количество цифр текущего и следующего числа совпадаю, а текущее число меньше следующего, то меняем их местами. 

4. **Сумма нечетных чисел:**  
   Программа создает переменную `s` и присваевывает ей значение 0. Перебираются элементы последовательности, и если остаток от деления не равен 0, то прибавляем значение к `s`.

5. **Двоичное представление чисел:**  
   Программа перебирает элементы массива, записывает в строку `y` остаток от деления на 2 и делит нацелов на 2, пока не останется 0. Создается пустая строка `r`, в которую по символьно записываются символы из строки `y`. Выводится строка `r`.

6. **Сумма цифр числа:**  
   Программа перебирает элементы массива. Запоминается значение элемента. Элемент массива обнуляется. Остатки числа при деление на 10 суммируются со значением элемента массива. Выводим получившийся массив

### 5. Программа

```java
import java.io.PrintStream;
import java.util.Scanner;
public class Main {
    public static Scanner in = new Scanner(System.in);
    public static PrintStream out = System.out;
    public static void main(String[] args) {
        //1. Считывает с консоли число N и генерирует массив первых N чисел
        //Фибоначчи.
        out.print("Введите длину последовательности: ");
        int n = in.nextInt();//считываем с консоли длину массива
        if (n==1) {//обработка исключающего случая
            out.println("Сумма всех нечетных чисел: "+1);
            out.println("Двоичное представление чисел: "+1);
            out.println("Сумма цифр каждого числа: "+1);
        }
        else {
            int [] a = new int[n];//создаем массив для нашей последовательности
            a[0] = 1;//первый элемент последовательности Фибоначчи
            a[1] = 1;//второй элемент последовательности Фибоначчи
            for (int i = 2; i < a.length; i++)//цикл для генерации массива
                a[i] = a[i-1]+a[i-2];//генерируем остальные элементы последовательности Фибоначчи по реккурентной формуле
            //2. Сортирует массив в порядке возрастания количества цифр в числе.
            //Если количества цифр равны, сортирует в порядке убывания числа.
            int [] b = new int[n];//создаем массив, где значение каждого элемента - это количество цифр числа Фибоначчи
            for (int i = 0; i < a.length; i++) {//цикл для генерации массива
                int k = 0, x = a[i];//переменная k считает количество цифр, переменная x копирует элемент изначального массива, чтобы не изменить его
                while (x > 0) { //цикл для счета количества цифр в числе
                    k++;//счетчик
                    x /= 10;//постепено избавляемя от каждой цифры в числе
                }
                b[i] = k;//записываем количество цифр в массив
            }

            for (int j = 1, z; j<n; j++)//цикл для сортикровки через совметную сортировку двух массивов
                for (int i = 0; i<n-j; i++) {
                    if(b[i]==b[i+1]&&a[i]<a[i+1]) {//если количество цифр одинаково и значение элемента меньше следующего
                        z = a[i];//то нужно поменять их местами через третью переменную
                        a[i] = a[i+1];
                        a[i+1] = z;
                    }
                }
            //3. Находит и выводит сумму всех нечётных чисел в массиве.
            int s = 0;//изначально сумма равна 0
            for (int i = 0; i < a.length; i++) {//цикл для перебора элементов последовательности
                if (a[i]%2!=0)//отбираем нечетные числа
                    s += a[i];//складываем их
            }
            out.println("Сумма всех нечетных чисел: "+s);//выводим сумму
            //4. Выводит элементы массива, заменяя каждое число на его двоичное
            //представление.
            out.print("Двоичное представление чисел: ");
            for (int i = 0, x; i < a.length; i++) {//цикл для перебора элементов последовательности
                String y = "";//создаем строку, в которую будем записывать двоичное представление чисел
                x = a[i];//создаем переменную x, чтобы не трогать элементы нашего массива
                while (x>0) {//цикл представления числа в двоичной системе счисления
                    y += x%2;//записываем каждый разряд в строку
                    x /= 2;//делим число на 2
                }
                String r = "";//создаем строку, чтобы развернуть, ведь у нас получилось двоичное число задом наперед
                for (int j = 0; j < y.length(); j++) {//цикл для перебора символов строки
                    r = y.charAt(j) + r;//записываем символы изначальной строки в обратном порядке
                }
                out.print(r+" ");//выводим двоичный вид чисел последовательности
            }
            out.println();//переходим на новую строку
            //5. Заменяет каждое число в массиве на сумму его цифр и выводит
            //полученный массив.
            for (int i = 0, x; i < a.length; i++) {//цикл для перебора элементов последовательности
                x = a[i];//запоминаем значение элемента
                a[i] = 0;//обнуляем значение элемента
                while (x>0) {//цикл для перебора цифр числа
                    a[i] += x%10;//отделяем цифру от числа и прибавляем в элемент
                    x /= 10;//делим число на 10
                }
            }
            out.print("Сумма цифр каждого числа: ");
            for (int i = 0; i < a.length; i++)//цикл для вывода элементов массива
                out.print(a[i]+" ");//выводим элементы массива
        }
    }
}
```

### 6. Анализ правильности решения

Программа работает корректно на всем множестве решений с учетом ограничений.

1. Тест на `N=1`:

    - **Input**:
        ```
        1
        ```

    - **Output**:
        ```
        Сумма всех нечетных чисел: 1
        Двоичное представление чисел: 1
        Сумма цифр каждого числа: 1
        ```

2. Тест на `N=10`:

    - **Input**:
        ```
        10
        ```

    - **Output**:
        ```
        Сумма всех нечетных чисел: 99
        Двоичное представление чисел: 1000 101 11 10 1 1 110111 100010 10101 1101
        Сумма цифр каждого числа: 8 5 3 2 1 1 10 7 3 4 
        ```
