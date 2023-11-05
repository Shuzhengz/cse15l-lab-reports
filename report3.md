# Lab Report 2

## Part 1

For the bug in `reverseInPlace()` in `ArrayExamples`:

Code:

```java
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```

Junit Test with test input of array `{3, 4, 5, 6, 7}`:

```java
@Test
public void testReverseInPlaceTest() {
    int[] input1 = {3, 4, 5, 6, 7};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{7, 6, 5, 4, 3}, input1);
}
```

The test fails and outputs `[7, 6, 5, 6, 7]` instead with error:

```
arrays first differed at element [3]; 
Expected :4
Actual   :6
<Click to see difference>


	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
	at org.junit.Assert.internalArrayEquals(Assert.java:534)
	at org.junit.Assert.assertArrayEquals(Assert.java:418)
	at org.junit.Assert.assertArrayEquals(Assert.java:429)
	at ArrayTests.testReverseInPlaceTest(ArrayTests.java:24)
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:59)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:56)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.BlockJUnit4ClassRunner$1.evaluate(BlockJUnit4ClassRunner.java:100)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:366)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:103)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:63)
	at org.junit.runners.ParentRunner$4.run(ParentRunner.java:331)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:79)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:329)
	at org.junit.runners.ParentRunner.access$100(ParentRunner.java:66)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:293)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:413)
	at org.junit.runner.JUnitCore.run(JUnitCore.java:137)
	at com.intellij.junit4.JUnit4IdeaTestRunner.startRunnerWithArgs(JUnit4IdeaTestRunner.java:69)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater$1.execute(IdeaTestRunner.java:38)
	at com.intellij.rt.execution.junit.TestsRepeater.repeat(TestsRepeater.java:11)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:35)
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:232)
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:55)
Caused by: java.lang.AssertionError: expected:<4> but was:<6>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:120)
	at org.junit.Assert.assertEquals(Assert.java:146)
	at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
	... 30 more


Process finished with exit code 255
```
