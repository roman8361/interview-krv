[Вопросы для собеседования](README.md)

# Алгоритмы
+ [Входит ли число в список(бинарный поиск)](algorithms.md#Входит-ли-число-в-список)
+ [Числа Фибоначчи](algorithms.md#Числа-Фибоначчи)
+ [Факториал числа](algorithms.md#Факториал-числа)

## Входит ли число в список

```java
    @Test
    public void binarySearch() {
        List<Integer> list = List.of(10, 22, 33, 46, 99);
        assertEquals(Boolean.TRUE, contains(list, 10));
        assertEquals(Boolean.TRUE, contains(list, 46));
        assertEquals(Boolean.FALSE, contains(list, 0));
        assertEquals(Boolean.FALSE, contains(list, 12));
    }

    private Boolean contains(List<Integer> list, Integer item) {
        int low = 0;
        int high = list.size() - 1;
        while (low <= high) {
            int mid = (low + high) / 2;
            int guess = list.get(mid);
            if (guess == item) {
                return Boolean.TRUE;
            }
            if (guess > item) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return Boolean.FALSE;
    }
```
[к оглавлению](#Алгоритмы)

## Числа Фибоначчи

```java
 /**
     * Числа Фибоначчи
     * Это числовой ряд, который выглядит следующим образом:
     * 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...
     * A0 = 0
     * A1 = 1
     * An+1 = An + An-1
     * Необходимо реализовать функцию:
     * на вход функция получает целое число n;
     * необходимо вывести в консоль значение числа Фибоначчи под номером n;
     * не рекомендуется использовать рекурсию.
     */
    @Test
    public void fibonacciTest() {
        assertEquals(5L, getFibonacciNumber(4L));
        assertEquals(13L, getFibonacciNumber(6L));
        assertEquals(144L, getFibonacciNumber(11L));
        
        assertEquals(5L, getFibonacciNumberRecurse(4L));
        assertEquals(13L, getFibonacciNumberRecurse(6L));
        assertEquals(144L, getFibonacciNumberRecurse(11L));
    }

    private long getFibonacciNumber(long num) {
        long firstNum = 0;
        long secondNum = 1;
        long fibonacci = 0;
        for (long i = 0; i < num; i++) {
            fibonacci = firstNum + secondNum;
            firstNum = secondNum;
            secondNum = fibonacci;
        }
        return fibonacci;
    }

    private long getFibonacciNumberRecurse(long num) {
        if (num == 1) return 1;
        if (num == 2) return 2;
        return getFibonacciNumberRecurse(num - 1) + getFibonacciNumberRecurse(num - 2);
    }

```

## Факториал числа
```java
 /**
     * Факториал числа n — это значение произведения (умножения) всех натуральных чисел от 1 до n, которое обозначается как n!
     * 1! =  1
     * 2! =  1 * 2 = 2
     * 3! =  1 * 2 * 3 = 6
     * 4! =  1 * 2 * 3 * 4 = 24
     * 5! =  1 * 2 * 3 * 4 * 5  = 120
     */

    @Test
    public void factorialTest(){
        assertEquals(6L, getFactorial(3));
        assertEquals(120L, getFactorial(5));
        assertEquals(720L, getFactorial(6));
        assertEquals(3628800L, getFactorial(10));

        assertEquals(6L, getFactorialRecurse(3));
        assertEquals(120L, getFactorialRecurse(5));
        assertEquals(720L, getFactorialRecurse(6));
        assertEquals(3628800L, getFactorialRecurse(10));

        assertEquals(6L, getFactorialStream(3));
        assertEquals(120L, getFactorialStream(5));
        assertEquals(720L, getFactorialStream(6));
        assertEquals(3628800L, getFactorialStream(10));
    }

    public long getFactorial(int f) {
        long result = 1;
        for (int i = 1; i <= f; i++) {
            result = result * i;
        }
        return result;
    }

    public long getFactorialRecurse(int f) {
        if (f <= 1) {
            return 1;
        }
        else {
            return f * getFactorialRecurse(f - 1);
        }
    }

    public long getFactorialStream(int f) {
        if (f <= 1) {
            return 1;
        }
        else {
            return IntStream.rangeClosed(2, f).reduce((x, y) -> x * y).getAsInt();
            }
        }

```