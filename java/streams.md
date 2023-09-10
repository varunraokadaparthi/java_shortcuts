# Print

### Print array
```
List<Integer> list;
Arrays.stream(nums).forEach(System.out::println);
```

### Print list
```
int[] nums;
list.forEach(System.out::println);
```

# Filter

### Filter Array
```
int[] nums;
int[] evenNums = Arrays.stream(nums)
    .filter(i -> i % 2 == 0)
    .toArray();
```

### Filter List
```
List<Integer> list = Arrays.asList(2, 4, 5, 3);
List<Integer> list evenNums = list.stream()
    .filter(i -> i % 2 == 0)
    .collect(Collectors.toList());
```

### Remove null values
```
List<String> list = Arrays.asList("hi", null, "hello");
List<String> nonNulllist = list.stream()
    .filter(i -> i != null)
    .collect(Collectors.toList());
```

# Sort
### Sort int array wrt indices
```
int[] test = {2, 3, 4, 1};
int[] sortedIndices = IntStream.range(0, test.length)
        .boxed().sorted(Comparator.comparingInt(i -> test[i]))
        .mapToInt(Integer::intValue)
        .toArray();
Arrays.stream(sortedIndices).forEach(System.out::println);
```

### Sort list wrt indices
```
List<Integer> test = Arrays.asList(2, 3, 4, 1);
int[] sortedIndices = IntStream.range(0, test.size())
            .boxed().sorted(Comparator.comparing(i -> test.get(i)))
            .mapToInt(Integer::intValue)
            .toArray();
```

## Sort by comparing 2 different quantities in a 2d array
```
int[][] arr = {{5, 4, 7}, {3, 5 , 6}, {8, 6, 5}, {10, 5, 4}};
Arrays.stream(arr)
        .sorted(Comparator.comparingInt((int[] row) -> row[0])
                .thenComparingInt((int[] row) -> row[1]))
        .forEach(row -> Arrays.stream(row).forEach(System.out::println));
```

# Map
### add to each element
```
List<Integer> list = Arrays.asList(2, 4, 5, 3);
List<Integer> list evenNums = list.stream()
    .map(i -> i + 10)
    .collect(Collectors.toList());
```

# Flatmap
### add 3 lists into a single list
```
List<Integer> list1 = Arrays.asList(1, 2);
List<Integer> list2 = Arrays.asList(3, 4);
List<Integer> list3 = Arrays.asList(5, 6);
List<List<Integer>> tList = Arrays.asList(list1, list2, list3);

List<Integer> flatMapList = tList.stream()
    .flatMap(x -> x.stream())
    .collect(Collectors.toList());

flatMapList.forEach(System.out::println);
```

### Convert 2d array to 1d array
```
int[][] arr = { {1, 2, 3}, {4, 5, 6}, {7, 8, 9} }
Arrays.stream(arr)
    .flatMapToInt(x -> Arrays.stream(x))
    .toArray();
```

### Flatmap along with map
```
int[][] arr = { {1, 2, 3}, {4, 5, 6}, {7, 8, 9} };
Arrays.stream(arr)
    .flatMapToInt(x -> Arrays.stream(x).map(y -> y + 10))
    .toArray();
```

# Character

### Convert 2d char array to list

```
char[][] board = { {'X','X','X','X'},{'X','O','O','X'},{'X','X','O','X'},{'X','O','X','X'} };
Arrays.stream(board)
    .map(x -> CharBuffer.wrap(x).chars()
        .mapToObj(ch -> (char)ch)
            .collect(Collectors.toList()))
    .collect(Collectors.toList());
```

# Map

### Access map
```
Map<List<List<Integer>>, Boolean> map = new HashMap<>();
map.entrySet()
        .stream()
        .filter(entrySet -> entrySet.getValue())
        .forEach(entrySet -> entrySet.getKey()
            .forEach(cList -> board[cList.get(0)][cList.get(1)] = 'X'));
```