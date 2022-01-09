[Вопросы для собеседования](README.md)

# Алгоритмы
+ [Входит ли число в список(бинарный поиск)](algorithms.md#Входит-ли-число-в-список)
+ [Сортировка коллекции](algorithms.md#Сортировка-коллекции)  
+ [Числа Фибоначчи](algorithms.md#Числа-Фибоначчи)
+ [Факториал числа](algorithms.md#Факториал-числа)
+ [Вывести числа рекурсией](algorithms.md#Вывести-числа-рекурсией)
+ [Сколько гласных и согласных букв](Сколько-гласных-и-согласных-букв)
+ [Палиндром](algorithms.md#Палиндром)

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

    //работает только для отсортированного массива
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

## Сортировка-коллекции
```java
  @Test
    public void selectionsSortTest() {
        List<Integer> anyArray = new ArrayList<>(List.of(1, 2, Integer.MIN_VALUE, Integer.MAX_VALUE, 111, -222, 123, 8));
        assertFalse(Arrays.equals(anyArray.toArray(), getSelectionsSort(anyArray).toArray())); // коллекции не равны
        Collections.sort(anyArray); // сортировка коллекции классом Collections
        assertArrayEquals(anyArray.toArray(), getSelectionsSort(anyArray).toArray());
    }
    
    private List<Integer> getSelectionsSort(List<Integer> arr) {
        List<Integer> result = new ArrayList<>();
        int index = arr.size();
        for (int i = 0; i < index; i++) {
            Integer minItem = findSmallest(arr);
            result.add(minItem);
            arr.remove(minItem);
        }
        return result;
    }

    private int findSmallest(List<Integer> arr) {
        int smallest = arr.get(0);
        for (Integer i : arr) {
            if (smallest > i) {
                smallest = i;
            }
        }
        return smallest;
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

[к оглавлению](#Алгоритмы)

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

[к оглавлению](#Алгоритмы)

## Вывести числа рекурсией
```java
    @Test
    public void recursSimpleTest() {
        simpleRecurs(10);
    }

    private void simpleRecurs(int num) {
        if (num == 0) return;
        System.out.print(num-- + " ");
        simpleRecurs(num);
    }
```

[к оглавлению](#Алгоритмы)


## Сколько гласных и согласных букв
```java
    @Test
    public void stringTestArrays(){
        final var consonants = "bcdfghjklmnpqrstvwxyz";
        final var vowels = "aeiou";
        final var word = "Hello World";

        char[] arrayLatter = word.toCharArray();

        var countVowels = 0;
        var countConsonants = 0;
        var countWords = word.split(" ").length;

        for (int i = 0; i < arrayLatter.length; i++) {
            final String s = String.valueOf(arrayLatter[i]).toLowerCase();
            if (vowels.contains(s)) {
                countVowels++;
            }
            if (consonants.contains(s)) {
                countConsonants++;
            }
        }

        System.out.println("Слов - " + countWords);
        System.out.println("Гласных - " + countVowels);
        System.out.println("Согласных - " + countConsonants);
    }
```

[к оглавлению](#Алгоритмы)

## Палиндром
```java
 /**
     * Палиндром
     * Палиндром - слово, которое одинаково читается в обоих направлениях.
     * Например:
     * 123454321
     * madam i’m Adam
     * Olson in Oslo
     * Необходимо реализовать функцию:
     * на вход функция получает строку;
     * нужно вывести в консоль слово yes, если строка является палиндромом;
     * нужно вывести в консоль слово no, если строка не является палиндромом;
     * при определении палиндрома игнорировать все пробелы, знаки препинания и апостроф.
     */
    @Test
    public void palindromeTest() {
        String s1 = "123454321";
        String s2 = "madam i’m Adam";
        String s3 = "Olson in Oslo";
        
        checkPalindrom1(s1);
        checkPalindrom1(s2);
        checkPalindrom1(s3);
        
        checkPalindrom2(s1);
        checkPalindrom2(s2);
        checkPalindrom2(s3);
    }

    private void checkPalindrom1(String str) {
        str = str.toLowerCase().replaceAll("[^A-Za-zА-Яа-я0-9]", ""); // удалится все кроме букв и цифр и lowerCase
        String str1 = str.substring(0, str.length() / 2);
        String str2 = str.length() % 2 == 0 ? reverseString(str.substring((str.length() / 2)))
                : reverseString(str.substring((str.length() / 2) + 1));
        System.out.println(str1.equals(str2) ? "yes" : "no");
    }

    private String reverseString(String str) {
        return new StringBuilder(str).reverse().toString();
    }

    //TODO BestPractice
    void checkPalindrom2(String s) {
        String san = s.replaceAll("[^A-Za-z0-9]", "");
        System.out.println(new StringBuilder(san).reverse().toString().equalsIgnoreCase(san) ? "yes" : "no");
    }

```