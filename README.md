# JUnit3-vs-JUnit5-Benchmark

# Results:

## Test with configuration phase (100 iterations, 1 fork):
```
Benchmark                                     Mode  Cnt  Score   Error  Units
AppTest.junit3_empty_test_method              avgt  100  0,050 � 0,011  ms/op
AppTest.junit3_test_with_simple_assertEquals  avgt  100  0,082 � 0,009  ms/op
AppTest.junit3_test_with_simple_assertTrue    avgt  100  0,093 � 0,011  ms/op

Benchmark                                             Mode  Cnt  Score   Error  Units
AppTest.junit5_vintage_empty_test_method              avgt  100  0,272 � 0,041  ms/op
AppTest.junit5_vintage_test_with_simple_assertEquals  avgt  100  0,289 � 0,049  ms/op
AppTest.junit5_vintage_test_with_simple_assertTrue    avgt  100  0,277 � 0,040  ms/op

Benchmark                                     Mode  Cnt  Score   Error  Units
AppTest.junit5_empty_test_method              avgt  100  0,842 � 0,122  ms/op
AppTest.junit5_test_with_simple_assertEquals  avgt  100  1,179 � 0,190  ms/op
AppTest.junit5_test_with_simple_assertTrue    avgt  100  1,156 � 0,161  ms/op
```

## Summary
### TL;DR
**JUnit3 outperformed JUnit5 (Vintage + Jupiter) overall - But in my humble opinion: That's okay. Why?**

### Let me explain
I can realiably measure a difference of around 1ms/op for JUnit 5 Jupiter and around 0.2ms/op for JUnit 5 Vintage.
JUnit5 is slower overall, but that really doesn't affect small projects test execution times.

Caution: Normally, creating the test engine instance and running tests is not our job,
our IDE or any other tooling will do that for us in a (probably) faster, parallel and more reliable way.

To get a feeling about the measured numbers in a scale, let's talk about the worst case: We need 1ms more per operation (test).

| Number of tests | Execution time in seconds (est.) | Execution time in minutes (est.) |
|---|---|---|
| 100 tests | 0.5s |  ~0.001m |
| 1.000 tests | 5s | ~0.01m |
| 10.000 tests | 50s | ~1m |
| 100.000 tests | 500s | ~8m |

Until we find a project with around 10.000 tests, we probably won't even notice it, because it's less than a minute. And if we have such a big project, the other tests are probably taking way more time than the added 1m through the switch to JUnit 5 and we should question the way too big project itself. ;)

## Some references about JUnit 5 performance
- JUnit5 Jupiter vs. JUnit5 Vintage Assertions: https://github.com/junit-team/junit5/issues/1258 (Issue adressed and fixed in 2018)
* JUnit5 Jupiter 10x slower than JUnit4: https://github.com/junit-team/junit5/issues/880
- Complains of missing statistics (Reason for this repo): https://github.com/junit-team/junit5/issues/1273