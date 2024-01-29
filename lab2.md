# Lab Report 2: Jan 30, 2024

* [Part 1: ChatServer](#part-1)
* [Part 2](#ls)
* [Part 3: What I learned](#cat)

## Part 1: ChatServer <a name="part-1"></a>
My home directory on EdStem has one subdirectory, `wavelet`. These are the files inside `wavelet`:
```
ChatServer.class  ChatServer.java  Handler.class  README.md  Server.class  ServerHttpHandler.class  Server.java  URLHandler.class
```

Here is the code inside `ChatServer.java`:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String chat = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return chat;
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] queries = url.getQuery().split("&");
                if (queries.length == 2){
                    String[] stringParams = queries[0].split("=");
                    String[] userParams = queries[1].split("=");
                    if (stringParams[0].equals("s") && userParams[0].equals("user")) {
                        chat += userParams[1] + ": " + stringParams[1] + "\n";
                        return "Message added!";
                    }
                }
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
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


