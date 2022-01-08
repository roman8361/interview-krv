[Вопросы для собеседования](README.md)

# Алгоритмы
+ [Входит ли число в список(бинарный поиск)](algorithms.md#binarySearch)


## [sssss](binarySearch)

```java
    @Test
    public void binarySearch() {
        List<Integer> list = List.of(10, 22, 33, 46, 99);
        System.out.println(contains(list, 10));
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


