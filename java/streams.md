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
List<Integer> list;
List<Integer> list evenNums = list.filter(i -> i % 2 == 0)
    .toArray();
```

### Sort int array by indices
```
int[] test = {2, 3, 4, 1};
int[] sortedIndices = IntStream.range(0, test.length)
        .boxed().sorted(Comparator.comparingInt(i -> test[i]))
        .mapToInt(Integer::intValue)
        .toArray();
Arrays.stream(sortedIndices).forEach(System.out::println);
```