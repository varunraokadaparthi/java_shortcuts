#Streams
### Sort by indices
int[] test = {2, 3, 4, 1};
    int[] sortedIndices = IntStream.range(0, test.length)
            .boxed().sorted(Comparator.comparingInt(i -> test[i]))
            .mapToInt(Integer::intValue)
            .toArray();
    Arrays.stream(sortedIndices).forEach(System.out::println);