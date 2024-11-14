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

Т.к. программа должна вывести сумму элементов массива и обработанные элементы массива, а числа Фибоначчи натуральные, то на выход мы получим натуральное число, строки, так как ищем двоичное представление числа, и целочисленный массив.

|                        | Тип         | min значение | max значение   |
|------------------------|-------------|--------------|----------------|
| Сумма чисел            | Целое число | 1            | 10<sup>9</sup> |
| Двоичное представление | Строка      | 1            | 10<sup>9</sup> |
| Сумма цифр             | Целое число | 1            | 10<sup>9</sup> |

### 3. Выбор структуры данных

Программа получает 2 вещественных числа, не превышающих по модулю 10<sup>9</sup> < 2<sup>30</sup>. Поэтому для их хранения
можно выделить 2 переменных (`x` и `y`) типа `double`.

|             | название переменной | Тип (в Java) | 
|-------------|---------------------|--------------|
| X (Число 1) | `x`                 | `double`     |
| Y (Число 2) | `y`                 | `double`     | 

Для вывода результата необязательно его хранить в отдельной переменной.

### 4. Алгоритм

#### Алгоритм выполнения программы:

1. **Ввод данных:**  
   Программа считывает два вещественных числа, обозначенные как `x` и `y`.

2. **Сравнение чисел:**  
   Программа сравнивает значения `x` и `y`. Если `x` больше или равно `y`, программа переходит к следующему шагу для
   работы с `x`. Если `y` больше, программа выполняет действия для работы с `y`.

3. **Проверка знака для выбранного числа:**
    - Если было выбрано число `x` (так как оно больше или равно `y`), проверяется, положительное оно или отрицательное.
      Если `x` положительное, оно выводится на экран. Если отрицательное, выводится его модуль (т.е. противоположное
      по знаку значение).
    - Если было выбрано число `y` (поскольку оно больше `x`), выполняется аналогичная проверка. Если `y` положительное,
      оно выводится на экран. Если отрицательное, выводится его модуль.

4. **Вывод результата:**  
   На экран выводится либо большее из чисел, либо его модуль, если это число отрицательное.

#### Блок-схема

```mermaid
graph TD
    A([Начало]) --> B[/Ввести: x, y/]
    B --> C{x >= y}
    C -- Нет --> D{y >= 0}
    D -- Нет --> E[/Вывод: -y/]
    D -- Да --> H[/Вывод: y/]
    C -- Да --> I{x >= 0}
    I -- Нет --> J[/Вывод: -x/]
    I -- Да --> K[/Вывод: x/]
    J --> Z
    K --> Z
    H --> Z
    E --> Z([Конец])

```

### 5. Программа

```java
import java.io.PrintStream;
import java.util.Scanner;

public class Main {
    // Объявляем объект класса Scanner для ввода данных
    public static Scanner in = new Scanner(System.in);
    // Объявляем объект класса PrintStream для вывода данных
    public static PrintStream out = System.out;

    public static void main(String[] args) {
        // Считывание двух вещественных чисел x и y из консоли
        double x = in.nextDouble();
        double y = in.nextDouble();

        // Определение максимального числа
        if (x >= y) {
            // Если x положительное, выводим x, иначе выводим -x,
            // чтобы на выходе было его абсолютное значение
            if (x >= 0) {
                out.println(x);
            } else {
                out.println(-x);
            }
        } else {
            // Если x положительное, выводим y, иначе выводим -y,
            // чтобы на выходе было его абсолютное значение
            if (y >= 0) {
                out.println(y);
            } else {
                out.println(-y);
            }
        }
    }
}
```

### 6. Анализ правильности решения

Программа работает корректно на всем множестве решений с учетом ограничений.

1. Тест на `X > Y > 0`:

    - **Input**:
        ```
        5 1.3
        ```

    - **Output**:
        ```
        5
        ```

2. Тест на `X < Y < 0`:

    - **Input**:
        ```
        -4 -2.2
        ```

    - **Output**:
        ```
        2.2
        ```

3. Тест на `X < 0 < Y`:

    - **Input**:
        ```
        -4 5
        ```

    - **Output**:
        ```
        5
        ```

4. Тест на `X = 0` или `Y = 0`:

    - **Input**:
        ```
        0 -3
        ```

    - **Output**:
        ```
        3
        ```

5. Тест на ограничение задачи:

    - **Input**:
        ```
        -1000000000 1000000000
        ```

    - **Output**:
        ```
        1000000000
        ```
