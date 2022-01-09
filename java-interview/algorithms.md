[Вопросы для собеседования](README.md)

# Алгоритмы
+ [Входит ли число в список(бинарный поиск)](algorithms.md#Входит-ли-число-в-список)
+ [Сортировка коллекции](algorithms.md#Сортировка-коллекции)  
+ [Числа Фибоначчи](algorithms.md#Числа-Фибоначчи)
+ [Факториал числа](algorithms.md#Факториал-числа)
+ [Вывести числа рекурсией](algorithms.md#Вывести-числа-рекурсией)
+ [Сколько гласных и согласных букв](algorithms.md#Сколько-гласных-и-согласных-букв)
+ [Палиндром](algorithms.md#Палиндром)
+ [Интегрированная шкала налогов](algorithms.md#Интегрированная-шкала-налогов)
+ [Удаляет дубли из массива заменяет их нулями](algorithms.md#Удаляет-дубли-из-массива-заменяет-их-нулями)
+ [Максимальное и минимальное значение в массиве](algorithms.md#Максимальное-и-минимальное-значение-в-массиве)
+ [Как найти все пары в массиве целых чисел сумма которых равна заданному числу](algorithms.md#Как-найти-все-пары-в-массиве-целых-чисел-сумма-которых-равна-заданному-числу)
+ [Выводит дубли букв](algorithms.md#Выводит-дубли-букв)
+ [Перевернуть строку](algorithms.md#Перевернуть-строку)
+ [Простая сортировка пузырьком](algorithms.md#Простая-сортировка-пузырьком)
+ [Вычисление квадрата минимального если не получается целое число](algorithms.md#Вычисление-квадрата-минимального-если-не-получается-целое-число)

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

## Сортировка коллекции
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

[к оглавлению](#Алгоритмы)

## Интегрированная шкала налогов
```java
/** 
 * 1 - 1000 -> 10%
 * 1000 - 3000 -> 15%
 * 3001 - ... -> 20%
 * 7000: 1000 * 0.10 + 2000 * 0.15 + 4000 * 0.20 = ...
 */
public class TaxTest {

    @Test
    public void taxTest() {
        var taxesConfiguration = List.of(new Tax(1000f, .1f),
                new Tax(2000f, .15f), new Tax(3000f, .2f));
        assertEquals(720.0f, getAmountToPay(taxesConfiguration, 800f));
        assertEquals(2005.0f, getAmountToPay(taxesConfiguration, 2300f));
        assertEquals(5800.0f, getAmountToPay(taxesConfiguration, 7000f));
    }

    private float getAmountToPay(List<Tax> taxesConfiguration, Float salary) {
        var salaryPercent = taxesConfiguration.stream().map(Tax::getSalaryPercent).collect(Collectors.toList());
        var percent = taxesConfiguration.stream().map(Tax::getPercent).collect(Collectors.toList());
        
        if (salary - salaryPercent.get(0) < 0) {
            return salary - (salary * percent.get(0));
        }

        if (salary - (salaryPercent.get(0) + salaryPercent.get(1)) < 0) {
            return salary - ((salaryPercent.get(0) * percent.get(0) + (salary - salaryPercent.get(0)) * percent.get(1)));
        }

        return salary - ((salaryPercent.get(0) * percent.get(0) + (salaryPercent.get(1) * percent.get(1)
                + ((salary - salaryPercent.get(0) - salaryPercent.get(1)) * percent.get(2)))));
    }
    
    class Tax {
        float salaryPercent;
        float percent;

        public Tax(float salary, float percent) {
            this.salaryPercent = salary;
            this.percent = percent;
        }

        public float getSalaryPercent() {
            return salaryPercent;
        }

        public float getPercent() {
            return percent;
        }
    }

}

/**
 * Вариант с HashMap
 * /** 
 * 1 - 1000 -> 10%
 * 1000 - 3000 -> 15%
 * 3001 - ... -> 20%
 * 7000: 1000 * 0.10 + 2000 * 0.15 + 4000 * 0.20 = ...
 */
 
public class IntegratedTaxTest {

    @Test
    public void integratesTaxTest() {
        final Map<Float, Float> taxManifest = new HashMap<>();
        taxManifest.put(10f, 1000f);
        taxManifest.put(15f, 2000f);
        taxManifest.put(20f, 1f);

        assertEquals(60.f, getIntegratedTax(taxManifest, 600f), 0.0f);
        assertEquals(100.f, getIntegratedTax(taxManifest, 1000f), 0.0f);
        assertEquals(175.f, getIntegratedTax(taxManifest, 1500f), 0.0f);
        assertEquals(220.f, getIntegratedTax(taxManifest, 1800f), 0.0f);
        assertEquals(250.f, getIntegratedTax(taxManifest, 2000f), 0.0f);
        assertEquals(340.f, getIntegratedTax(taxManifest, 2600f), 0.0f);
        assertEquals(400.f, getIntegratedTax(taxManifest, 3000f), 0.0f);
        assertEquals(800.f, getIntegratedTax(taxManifest, 5000f), 0.0f);
        assertEquals(1200.f, getIntegratedTax(taxManifest, 7000f), 0.0f);
        assertEquals(1800.f, getIntegratedTax(taxManifest, 10000f), 0.0f);
    }

    private Float getIntegratedTax(Map<Float, Float> taxManifest, Float salary) {
        float accumTax = 0f;
        float salarySum = 0f;
        float lastSalarySum = 0f;

        final List<Float> manifestKeys = new ArrayList<>(taxManifest.keySet());
        final List<Float> manifestValues = new ArrayList<>(taxManifest.values());

        for (int i = 0; i < manifestKeys.size(); i++) {
            salarySum += manifestValues.get(i);
            float salaryDif = salary - salarySum;

            if (salaryDif < 0 || i == manifestKeys.size() - 1) {
                accumTax += (salary - lastSalarySum) * (manifestKeys.get(i) / 100);
                return accumTax;
            }
            accumTax += manifestValues.get(i) * (manifestKeys.get(i) / 100);
            lastSalarySum = salarySum;
        }
        return -1f;
    }

}
```
[к оглавлению](#Алгоритмы)

## Удаляет дубли из массива заменяет их нулями
```java
 @Test // удаляет дубли из массива, заменяет их нулями
    public void removeDuplicatesTest() {
        int[] values1 = new int[]{1, 1, 2, 2, 3, 4, 5};
        System.out.println("removeDuplicates : " + Arrays.toString(removeDuplicates(values1)));
    }

    // удаляет дубли из массива, заменяет их нулями
    private int[] removeDuplicates(int[] numbersWithDuplicates) {
        // Sorting array to bring duplicates together
        Arrays.sort(numbersWithDuplicates);
        int[] result = new int[numbersWithDuplicates.length];
        int previous = numbersWithDuplicates[0];
        result[0] = previous;
        for (int i = 1; i < numbersWithDuplicates.length; i++) {
            int ch = numbersWithDuplicates[i];
            if (previous != ch) {
                result[i] = ch;
            }
            previous = ch;
        }
        return result;
    }
```
[к оглавлению](#Алгоритмы)

## Максимальное и минимальное значение в массиве
```java
    @Test //Максимальное и минимальное значение в массиве
    public void minMaxValueInArrays() {
        largestAndSmallest(new int[]{-20, 34, 21, -87, 92, Integer.MAX_VALUE});
        largestAndSmallest(new int[]{10, Integer.MIN_VALUE, -2});
        largestAndSmallest(new int[]{Integer.MAX_VALUE, 40, Integer.MAX_VALUE});
    }

    public void largestAndSmallest(int[] numbers) {
        int largest = Integer.MIN_VALUE;
        int smallest = Integer.MAX_VALUE;
        for (int number : numbers) {
            if (number > largest) {
                largest = number;
            } else if (number < smallest) {
                smallest = number;
            }
        }
        System.out.println("Given integer array : " + Arrays.toString(numbers));
        System.out.println("Largest number in array is : " + largest);
        System.out.println("Smallest number in array is : " + smallest);
    }
```
[к оглавлению](#Алгоритмы)

## Как найти все пары в массиве целых чисел сумма которых равна заданному числу
```java
    @Test //Как найти все пары в массиве целых чисел, сумма которых равна заданному числу
    public void pairsSumTest() {
        int[] numbers = {2, 4, 3, 5, 7, 8, 9};
        printPairs(numbers, 8);
    }

    public void printPairs(int[] array, int sum) {
        for (int i = 0; i < array.length; i++) {
            int first = array[i];
            for (int j = i + 1; j < array.length; j++) {
                int second = array[j];
                if ((first + second) == sum) {
                    System.out.printf("(%d, %d) %n", first, second);
                }
            }
        }
    }
```
[к оглавлению](#Алгоритмы)
## Выводит дубли букв
```java
    @Test //Выводит дубли букв
    public void findDuplicateCharacters() {
        printDuplicateCharacters("Programming");
        printDuplicateCharacters("Combination");
        printDuplicateCharacters("Java");
    }

    public static void printDuplicateCharacters(String word) {
        char[] characters = word.toCharArray();
        Map<Character, Integer> charMap = new HashMap<>();
        for (Character ch : characters) {
            if (charMap.containsKey(ch)) {
                charMap.put(ch, charMap.get(ch) + 1);
            } else {
                charMap.put(ch, 1);
            }
        }
        Set<Map.Entry<Character, Integer>> entrySet = charMap.entrySet();
        System.out.printf("List of duplicate characters in String '%s' %n", word);
        for (Map.Entry<Character, Integer> entry : entrySet) {
            if (entry.getValue() > 1) {
                System.out.printf("%s : %d %n", entry.getKey(), entry.getValue());
            }
        }
    }
```
[к оглавлению](#Алгоритмы)
## Перевернуть строку
```java
    @Test // перевернуть строку
    public void reversString() {
        System.out.println(reverse("123456"));
        System.out.println(reverseRecursively("123456789"));
    }

    public static String reverse(String str) {
        StringBuilder strBuilder = new StringBuilder();
        char[] strChars = str.toCharArray();
        for (int i = strChars.length - 1; i >= 0; i--) {
            strBuilder.append(strChars[i]);
        }
        return strBuilder.toString();
    }

    public static String reverseRecursively(String str) {
        if (str.length() < 2) {
            return str;
        }
        return reverseRecursively(str.substring(1)) + str.charAt(0);
    }
```
[к оглавлению](#Алгоритмы)

## Простая сортировка пузырьком
```java
    @Test // Простая сортировка пузырьком
    public void bubbleSortTest() {
        int[] numbers = {12, 3, -9, 5, 55, 8, 9};
        System.out.println(Arrays.toString(bubbleSort(numbers)));
    }

    private static int[] bubbleSort(int[] array) {
        boolean sorted = false;
        int temp;
        while (!sorted) {
            sorted = true;
            for (int i = 0; i < array.length - 1; i++) {
                if (array[i] > array[i + 1]) {
                    temp = array[i];
                    array[i] = array[i + 1];
                    array[i + 1] = temp;
                    sorted = false;
                }
            }
        }
        return array;
    }
```
[к оглавлению](#Алгоритмы)

## Вычисление квадрата минимального если не получается целое число
```java
    @Test // вычисление квадрата минимального если не получается целое число
    public void calculateSqrtTest(){
        System.out.println(calculateSqrt(9));
        System.out.println(calculateSqrt(16));
        System.out.println(calculateSqrt(20));
    }

    private int calculateSqrt(int input) {
        int low = 0;
        int high = input;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            int squMid = mid * mid;
            if (squMid == input) {
                return mid;
            }
            if (squMid > input) {
                high = mid - 1;
            }
            if (squMid < input) {
                low = mid + 1;
            }

        }
        return low - 1;
    }
```

[к оглавлению](#Алгоритмы)
