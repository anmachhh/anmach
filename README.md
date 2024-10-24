## Отчет по лабораторной работе № 1

#### № группы: `ПМ-2403`

#### Выполнила: `Мачульская Анастасия Андреевна`

#### Вариант: `18`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Входные и выходные данные](#2-входные-и-выходные-данные)
- [Выбор структуры данных](#3-выбор-структуры-данных)
- [Алгоритм](#4-алгоритм)
- [Программа](#5-программа)
- [Анализ правильности решения](#6-анализ-правильности-решения)

### 1. Постановка задачи

> В парке есть 4 дорожки длиной A, B, C, D метров. Ваша цель -
прогуляться по всем дорожкам, начиная с самой длинной. Но у вас есть
ограничение по времени - вы можете прогуляться не более чем X метров.
Какое количество дорожек вы сможете пройти? На вход программы подаются
натуральные числа X, A, B, C, D.

Для начала программе нужно будет создать список дорожек и отсортировать его, а затем, пройтись по отсортированному списку, уменьшая оставшийся лимит на длину каждой дорожки.


### 2. Входные и выходные данные

#### Данные на вход

На вход программа должна получить 5 чисел - сначала длину пути, по которому можно прогуляться, а затем - длину всех дорожек. Эти значения могут быть только натуральными.

#### Данные на выход

На выходе программа должна вывести число дорожек, которое получилось пройти.

### 3. Выбор структуры данных

В коде используются примитивные типы данных (int).

|             | название переменной | Тип (в Java) | 
|-------------|---------------------|--------------|
| X (Число 1) | `X`                 | `Int`        |
| A (Число 2) | `A`                 | `Int`        | 
| B (Число 3) | `B`                 | `Int`        |
| C (Число 4) | `C`                 | `Int`        | 
| D (Число 5) | `D`                 | `Int`        |
|totalDistance| `totalDistance`     | `Int`        | 
|count        | `count`             | `Int`        | 
|lengths      | `lengths`           | `Int`        | 

### 4. Алгоритм

#### Алгоритм выполнения программы:

1. Прочитать значения X, A, B, C, D.

2. Создать список дорожек и отсортировать его по убыванию.

3. Инициализировать счетчик пройденных дорожек и переменную для оставшегося лимита.

4. Пройтись по отсортированному списку дорожек, уменьшая оставшийся лимит на длину каждой дорожки, если это возможно.
  
5. Вывести количество пройденных дорожек.

   
7. #### Блок-схема

```mermaid
graph TD
A[Начало] --> B[Ввод X, A, B, C, D]
    B --> C[Создать массив lengths]
    C --> D[Сортировать массив lengths по возрастанию]
    D --> E[Инициализировать totalDistance = 0]
    E --> F[Инициализировать count = 0]
    F --> G[Для каждой длины в массиве lengths]
    G --> H{totalDistance + длина <= X}
    H -- Да --> I[totalDistance += длина]
    I --> J[count += 1]
    J --> G
    H -- Нет --> K[Выход из цикла]
    K --> L[Вывод count]
    L --> M[Конец]
 ```

### 5. Программа

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Scanner;

public class ParkWalk {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Чтение входных данных
        System.out.print("Введите X (максимальная длина): ");
        int X = scanner.nextInt();
        
        System.out.print("Введите длины дорожек A, B, C, D: ");
        Integer[] lengths = new Integer[4];
        for (int i = 0; i < 4; i++) {
            lengths[i] = scanner.nextInt();
        }

        // Сортировка дорожек по убыванию 

        int totalDistance = 0;
        int count = 0;

        // Проход по дорожкам
        for (int length : lengths) {
            if (totalDistance + length <= X) {
                totalDistance += length;
                count++;
            } else {
                break; // Прекращаем, если превышаем лимит
            }
        }

        // Вывод результата
        System.out.println("Количество дорожек, которые вы сможете пройти: " + count);
 scanner.close();
    }
}
 ```

### 6. Анализ правильности решения

Программа работает корректно на всем множестве решений с учетом ограничений.

1. Тест X > A > B > C > D

- Input:
    ```
    100
    40
    30
    20
    10
    ```

- Output:
    ```
    4
    ```

    1. Тест X > A > B > C < D

- Input:
    ```
    50
    40
    30
    5
    8
    ```

- Output:
    ```
    1
    ```
   
