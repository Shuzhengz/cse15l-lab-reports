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

![Example_Image_1](images/Screenshot%20from%202023-10-22%2016-05-36.png)

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


### Example 2

![Example_Image_2](images/Screenshot%20from%202023-10-22%2016-05-51.png)

Starting off from the last example, I used `/add-message` and added another value, 
`hello_again_again`, to the server, and then I entered the URL for the index 
page with no arguments. The method `handleRequest()` was called once again, and
with no argument, it proceeded with the default case of just outputting the 
stored values, which also uses the `formatToDisplay()` method.

No relevant arguments or values was passed in this time, and no values changed 
to this specific URL shown in picture. In the previous URL that I used to add 
the third value (`http://localhost:4000/add-message?s=hello_again_again`), the
process is the same with example 1.

## Part 2

### Path to private key:

![Private_Key](images/Screenshot%20from%202023-10-22%2016-31-18.png)

Contents of `home/zsz/.ssh/id_rsa.pub`: 

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCwLuDV+yWdA4Z1j+TbVUA/ecuucT1ikJWG7pEkQ
(..., shortened for security)UupVlx85kIxGWSKlQ/w3VIjjtFpn2jqbVTgzqIGIT1qp33Tt
6cjRi+X1k6k0k7Stc53NRwBApb4oPfC+wyFfsfPK7kMFk9FBisAP9NrODYmIDVuH0= zsz@fedora
```

### Path to public key:

![Public_Key](images/Screenshot%20from%202023-10-22%2016-31-46.png)

Contents of `~/.ssh/authorized_keys`:

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCwLuDV+yWdA4Z1j+TbVUA/ecuucT1ikJWG7pEkQ
(..., shortened for security)UupVlx85kIxGWSKlQ/w3VIjjtFpn2jqbVTgzqIGIT1qp33Tt
6cjRi+X1k6k0k7Stc53NRwBApb4oPfC+wyFfsfPK7kMFk9FBisAP9NrODYmIDVuH0= zsz@fedora
```

### Logging into `ieng6` with ssh:

![login](images/Screenshot%20from%202023-10-22%2016-32-12.png)

## Part 3

I did not know that the `ieng6` server was not compliant with the more modern
protocol that my system's `ssh` is running with. I use Fedora 36, and the `ssh`
on the system by default would not connect to the server, and I had to enable 
legacy features manually to add the ucsd server and fingerprint to the known 
host list, which I did not know how to do. But fortunately after a bit of 
digging around on Google, I managed to resolve the issue.
