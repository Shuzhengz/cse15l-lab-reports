# Lab Report 5

## Part 1

### 1. Student post:

My code runs with the expected output for the first input that I put, but the code stops after
and errors out. It says that there is an exception that the index is out of bounds, but it is
in the bounds of string 2 that I inputed.

![stacktrace](images/Screenshot%202023-12-03%20183534.png)

I think that the function that is checking the second string didn't pick up my input, but I'm
not sure why because the input I had was inside the second string.

My input is:

```java
String a = "hellothere";
String b = "thereisnospacehere";
String c = "is";
```

### 2. Response:

It seems like that your input did run correctly, there is a `th` on the top of the stacktrace that
you sent, which seems to be the correct output. Are there any other inputs that you have in the
code that may cause this exception?

Also, make sure to check every condition for the inputs, compiling and running your program in
`jdb` may give you some helpful messages.

### 3. Trying the suggestion

![jdb](images/Screenshot%202023-12-03%20185609.png)

It seems like that the error is caused by checking the index from something to something, which is
what it is doing on the first string instead of the second. The input `sp` does actually look like
that it is not valid, because the first string does not have the words this long. Catching this 
throwable in the code would fix the issue as the `jdb` output suggested.

Running this seems to have solved the problem

![after](images/Screenshot%202023-12-03%20190553.png)

It also ran the third test case this time, which was not ran because the program errored out before
reaching there.

### 4. Files

File structure:

```
│
└───src
        Main.class
        Main.java
        run.sh
        debug.sh
```

`Main.java` before fixing:

```java
public class Main {

    /**
     * Finds the first occurrence of c in b, and returns the corresponding substring in a with the
     * same start and end indexes.
     *
     * @param a String a, to be modified and returned based on the indexes
     * @param b String b, to find the index number of the substring
     * @param c String c, the substring to find the index numbers from b, must be contained in b
     * @return Modified String a based on the indexes from the occurrence of String c in String b
     */
    public static String substringIndex(String a, String b, String c) {

        String result;
        int indexNum = b.indexOf(c);
        result = a.substring(indexNum, indexNum + c.length());

        return result;
    }

    public static void main(String[] args) {
        String a = "hellothere";
        String b = "thereisnospacehere";
        String c = "is";
        System.out.println(substringIndex(a, b, c));

        String d = "sp";
        System.out.println(substringIndex(a, b, d));

        String e = "xy";
        System.out.println(substringIndex(a, b, e));
    }

}
```

`run.sh`:

```bash
javac *.java
java Main
```

`debug.sh`:

```bash
javac -g *.java
jdb Main
```

Commands to trigger the bug:

```
bash run.sh
```

`Main.java` after fixing:

```java
public class Main {

    /**
     * Finds the first occurrence of c in b, and returns the corresponding substring in a with the
     * same start and end indexes.
     *
     * @param a String a, to be modified and returned based on the indexes
     * @param b String b, to find the index number of the substring
     * @param c String c, the substring to find the index numbers from b, must be contained in b
     * @return Modified String a based on the indexes from the occurrence of String c in String b
     */
    public static String substringIndex(String a, String b, String c) {

        String result;

        try {
            int indexNum = b.indexOf(c);
            result = a.substring(indexNum, indexNum + c.length());
        } catch(Exception nonOccurrence) {
            result = "Cannot find c in b, or not valid in a";
        }

        return result;
    }

    public static void main(String[] args) {
        String a = "hellothere";
        String b = "thereisnospacehere";
        String c = "is";
        System.out.println(substringIndex(a, b, c));

        String d = "sp";
        System.out.println(substringIndex(a, b, d));

        String e = "xy";
        System.out.println(substringIndex(a, b, e));
    }

}
```

Description:

Adding the exception handing solves the issue, because if the indexes of string 3 that is in string
2 does not exist in string 1, then the program would catch this exception and throw it, outputing
an error message, and then keeps running as usual.

It also fixes the third input case that is not tested becuase the program never reached there, that
string 3 does not exist in string 2, and will also handle it properly.

## Part 2

I didn't know that you can use plugins to make `nvim` look very good with a tiling windows manager
before.

I was searching for `vim` in my package manager when I saw `Neovim` as an option. Out of curiocity
I searched it up, and it seems to be a more customizable version of `vim`, which was pretty cool,
so I installed it. It turns out that most of the features for `nvim` can be achieved by adding
things in its `.config` file, and it is possible to customize the looks and function of the editor
to make it more like an IDE. So I followed resources and instructions online like 
[this one](https://github.com/crivotz/nv-ide) to customize it:

![example](https://raw.githubusercontent.com/crivotz/nv-ide/master/screenshots/nv-ide_screenshot_1.png)

(This screenshot is from the GitHub repo I linked, I'm still working on setting it up on my machine)
