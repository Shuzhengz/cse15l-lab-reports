# Lab Report 2

## Part 1

Code for `StringServer`:

In `StringServer.java`

```java
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.lang.StringBuffer;

class Handler implements URLHandler {
    // The array list of strings stored
    ArrayList<String> values = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return formatToDisplay(values);
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    values.add(parameters[1]);
                    return formatToDisplay(values);
                }
            }
            return "404 Not Found!";
        }
    }

    private String formatToDisplay(ArrayList<String> value) {
        StringBuffer returnValue = new StringBuffer();
        for (int i = 0; i < value.size(); i++) {
            returnValue.append(Integer.toString(i + 1) + ". ").append(value.get(i)).append('\n');
        }
        return returnValue.toString();
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

### Example 1

![Example_Image_1](report2_images/Screenshot%20from%202023-10-22%2016-05-36.png)

Here the program called the `handleRequest()` method to run through the url
provided. It adds the string _hello_ the first time and then _hello_again_ the
second time (which is the url shown in the picture). The method then calls the
private method `formatToDisplay()` to format the values stored inside the 
string arraylist that I use to store values, an then returns them to be 
displayed on screen.

The relevant argument to the method would be the `?` character in the url, which
means that it wants to run a query; and the `s` character, which means the query
is in string. The last argument is the value itself, which in this case is
`hello_again`, as it is after the `=` character.

The value of the string `ArrayList` was changed, as the program stores the value
inside it.
