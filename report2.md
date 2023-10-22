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
