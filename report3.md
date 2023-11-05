# Lab Report 2

## Part 1

### For the bug in `reverseInPlace()` in `ArrayExamples`:

Code:

```java
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```

### Failed Junit Test with test input of array `[3, 4, 5, 6, 7]`:

```java
@Test
public void testReverseInPlaceTest() {
    int[] input1 = {3, 4, 5, 6, 7};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{7, 6, 5, 4, 3}, input1);
}
```

The test fails and outputs `[7, 6, 5, 6, 7]` instead  of the expected `[7, 6, 5, 4, 3]` with
output:

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
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invok
    (DirectMethodHandleAccessor.java:103)
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
	at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria
    java:8)
	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
	... 30 more


Process finished with exit code 255
```

### Junit test of input that does not induce a failure, an array of `[1]`:

```java
@Test
public void testReverseInPlaceTestNoError() {
    int[] input1 = {1};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{1}, input1);
}
```

With output:

```
Process finished with exit code 0
```

This is because the array has length of `1`, so there is no data to be lost.

### Fixed code vs original code:

```diff
static void reverseInPlace(int[] arr) {
+   final int[] tempArray = arr.clone();
    for (int i = 0; i < arr.length; i += 1) {
-       arr[i] = arr[arr.length - i - 1];
+       arr[i] = tempArray[arr.length - i - 1];
    }
}
```
### Explanation

The fix used a new temporary array that is a clone of the original array, and then assigned the
old array with the contents of the temp array in reverse. This fixed the bug that the original
code has, which is that it overrides itself for every operation it does in reverse, so it loses
half of the data that it had, resulting in only half of the array being reversed, which the other
half is unchanged. The fix works because it no longer loses data when rewriting the contents of 
the array, since the temp array is never being written to, and is declared as a constant.

## Part 2

I found the commands using the `man grep` and `grep --help` commands, and its
[offical documentation](https://www.gnu.org/software/grep/manual/) from GNU

### `grep -H` command

The `-H` flag is the same as `--with-filename`, which prints file names with output lines

For example, running the command for word _"observational"_ in all `.txt` files in 
`technical/plos` gives:

```
[zsz@fedora technical]$ grep -H "observational" plos/*.txt
plos/journal.pbio.0020420.txt:        observational, comparative, theoretical) and taxonomic systems.
plos/pmed.0020061.txt:        complete. Using observational studies to disentangle the adverse consequences of a single
plos/pmed.0020180.txt:        feel it is a reasonable approach to this dilemma until larger, prospective observational
plos/pmed.0020181.txt:        Randomized trials and observational studies have conclusively shown a marked improvement
plos/pmed.0020181.txt:        These results are closely consistent with observational data linking weight gain to
plos/pmed.0020195.txt:        are not negligible. Until larger prospective observational studies have been conducted,
plos/pmed.0020206.txt:        Working with several colleagues, I initiated an observational study to analyze the ways
plos/pmed.0020231.txt:        controlled trials, large observational studies (some prospective) suggest that this diet
```

We can also narrow the search down with the `\>` option at the end of the word, for example, 
running the command:

`grep -H "rvational\>" plos/*.txt` 

would give all `.txt` files in `plos/` that have words **ending** in _"rvational"_:

```
[zsz@fedora technical]$ grep -H "vational\>" plos/*.txt
plos/journal.pbio.0020404.txt:        motivational behavior, especially feeding behavior. It is lodged primarily in the lateral
plos/journal.pbio.0020420.txt:        observational, comparative, theoretical) and taxonomic systems.
plos/pmed.0010052.txt:        the same forces that have made millionaires out of motivational speakers and diet book
plos/pmed.0020061.txt:        complete. Using observational studies to disentangle the adverse consequences of a single
plos/pmed.0020180.txt:        feel it is a reasonable approach to this dilemma until larger, prospective observational
plos/pmed.0020181.txt:        Randomized trials and observational studies have conclusively shown a marked improvement
plos/pmed.0020181.txt:        These results are closely consistent with observational data linking weight gain to
plos/pmed.0020195.txt:        are not negligible. Until larger prospective observational studies have been conducted,
plos/pmed.0020206.txt:        Working with several colleagues, I initiated an observational study to analyze the ways
plos/pmed.0020231.txt:        controlled trials, large observational studies (some prospective) suggest that this diet
```

Words like _"motivational"_ are now also inlcuded in the search.

### `grep -C` command

The `-C` flag is the same as `--context=NUM`, which prints _NUM_ lines of output context

For example, to see 2 lines around the word _"observational"_ in `plos/pmed.0020061.txt`, we 
would run:

```
[zsz@fedora technical]$ grep -C 2 "observational" plos/pmed.0020061.txt
        standard” for detecting subtle effects of environmental toxins on humans. But
        epidemiological studies are expensive to mount, difficult to execute, and take years to
        complete. Using observational studies to disentangle the adverse consequences of a single
        toxin from other environmental influences and to promulgate regulations is a difficult and
        painfully slow process. There is also a financial disincentive for chemical registrants to
```

Which prints two lines of context above and below the word.

We can also run it when there are multiple matching word, in that case, the command would print 2 
extra linex above and below blocks of text that contains mutiple of the same word:

```
[zsz@fedora technical]$ grep -C 2 "this" plos/pmed.0020061.txt
        Council, the chemical manufacturer's trade association, to provide basic toxicity screening
        tests for the high-production-volume chemicals by 2005
        (http://www.epa.gov/chemrtk/volchall.htm), but this is voluntary.
        For new pesticides intended for use on food crops—one of the areas in which regulations
        are most stringent—regulations require only that DNT testing be evaluated for substances
--
        potential DNT prior to their registration and use [49]. For pesticides—which undergo more
        premarket testing than other chemicals—the EPA has relied on a tiered system of toxicity
        testing. The assumption underlying this system is that positive findings on earlier, more
        basic tests of neurotoxicity in adult animals will “trigger” the EPA to request more
        extensive testing by manufacturers, including tests in immature animals. Unfortunately,
        this tiered process has failed to result in appropriate DNT testing. In 1998, an internal
        EPA Toxicology Working Group concluded that these triggers may not be sufficient to
        identify all chemicals that have the potential to produce DNT [75]. Moreover, this tiered
        system discourages industry from conducting testing in immature animals because the
        findings could necessitate further costly testing and hinder a chemical from reaching the
```

This command is very useful in finding the context of the word being used

### `grep -L` command

The `-L` flag is the same as `--files-without-match`, which prints only names of FILEs with no 
selected line.
The command is very useful in finding files that are missing certain words

For example, running the `-L` flag on all `.txt` in `plos/` with the word _"this"_ gives all the 
files that do not contain the word:

```
[zsz@fedora technical]$ grep -L "this" plos/*.txt
plos/pmed.0010030.txt
plos/pmed.0010050.txt
plos/pmed.0020019.txt
plos/pmed.0020027.txt
plos/pmed.0020028.txt
plos/pmed.0020048.txt
plos/pmed.0020065.txt
plos/pmed.0020086.txt
plos/pmed.0020120.txt
plos/pmed.0020145.txt
plos/pmed.0020149.txt
plos/pmed.0020189.txt
plos/pmed.0020195.txt
plos/pmed.0020226.txt
```

The search however also includes parts of the word, so running:

```
[zsz@fedora technical]$ grep -L "x" plos/*.txt
plos/pmed.0020192.txt
plos/pmed.0020226.txt
plos/pmed.0020274.txt
```

would give all files that does not contain the character _"x"_. To narraow the search down to 
exact words, use the `-w` flag in front of the word to be searched

### `grep -l`

The `-l` flag is the same as `--files-with-match`, which is the opposite of "-L" command and 
prints only names of FILEs with selected line

For example, running the `-L` flag on all `.txt` in `plos/` with the word _"observation"_ gives 
all the files that contain the word:

```
[zsz@fedora technical]$ grep -l -w "observation" plos/*.txt
plos/journal.pbio.0020019.txt
plos/journal.pbio.0020046.txt
plos/journal.pbio.0020054.txt
plos/journal.pbio.0020125.txt
plos/journal.pbio.0020187.txt
plos/journal.pbio.0020206.txt
plos/journal.pbio.0020215.txt
plos/journal.pbio.0020241.txt
plos/journal.pbio.0020297.txt
plos/journal.pbio.0020302.txt
plos/journal.pbio.0020337.txt
plos/journal.pbio.0020346.txt
plos/journal.pbio.0020401.txt
plos/journal.pbio.0020439.txt
plos/pmed.0010066.txt
plos/pmed.0020018.txt
plos/pmed.0020045.txt
plos/pmed.0020067.txt
plos/pmed.0020103.txt
plos/pmed.0020123.txt
plos/pmed.0020150.txt
plos/pmed.0020246.txt
```

Note that I used the `-w` flag here that limits the search to only files that contain 
_"observation"_ as its own word, this is useful because sometimes only the exact word is wanted 
in a search

We can also run the same command but with `pmed.*.txt`

```
[zsz@fedora technical]$ grep -l -w "observation" plos/pmed.*.txt
plos/pmed.0010066.txt
plos/pmed.0020018.txt
plos/pmed.0020045.txt
plos/pmed.0020067.txt
plos/pmed.0020103.txt
plos/pmed.0020123.txt
plos/pmed.0020150.txt
plos/pmed.0020246.txt
```

It narrows the search down to only `pmed` files that are also `.txt` so that you don't have your 
screen flooded with unecessary files
