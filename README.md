# JUnit3-vs-JUnit5-Benchmark

# Results:

## Without configuration phase (100 iterations, 1 fork):
```
Benchmark                                     Mode  Cnt  Score   Error  Units
AppTest.junit3_empty_test_method              avgt  100  0,065 � 0,041  ms/op
AppTest.junit3_test_with_simple_assertEquals  avgt  100  0,066 � 0,008  ms/op
AppTest.junit3_test_with_simple_assertTrue    avgt  100  0,095 � 0,013  ms/op

Benchmark                                     Mode  Cnt  Score   Error  Units
AppTest.junit5_empty_test_method              avgt  100  0,450 � 0,091  ms/op
AppTest.junit5_test_with_simple_assertEquals  avgt  100  0,477 � 0,097  ms/op
AppTest.junit5_test_with_simple_assertTrue    avgt  100  0,468 � 0,093  ms/op
```

## With configuration phase (100 iterations, 1 fork):
```
Benchmark                                     Mode  Cnt  Score   Error  Units
AppTest.junit3_empty_test_method              avgt  100  0,061 � 0,006  ms/op
AppTest.junit3_test_with_simple_assertEquals  avgt  100  0,076 � 0,013  ms/op
AppTest.junit3_test_with_simple_assertTrue    avgt  100  0,066 � 0,010  ms/op

Benchmark                                     Mode  Cnt  Score   Error  Units
AppTest.junit5_empty_test_method              avgt  100  0,918 � 0,110  ms/op
AppTest.junit5_test_with_simple_assertEquals  avgt  100  1,244 � 0,325  ms/op
AppTest.junit5_test_with_simple_assertTrue    avgt  100  1,019 � 0,165  ms/op
```

## Summary
JUnit3's TestRunner was faster in my benchmark, I couldn't find any other reference data to compare mine with.
There is only one issue under the junit5 repository which also comes to this conclusion.

BUT to point that out: We are talking about 1 millisecond in difference for 100 iterations of a test.
It's slower but still incredibly fast and doesn't really affect small projects test execution times.
