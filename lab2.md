# Lab Report 2: Jan 30, 2024

* [Part 1: ChatServer](#part-1)
* [Part 2: Logging in to `ieng6`](#part-2)
* [Part 3: What I learned](#part-3)

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

### Adding the first message:

<img src="/img/add-message-1.png" alt="Added a message using /add-message?s=Hello&user=jpolitz" width="600"/>

<img src="/img/chat-1.png" alt="Chat after adding message 1" width="500"/>

* The method `handleRequest` is called with the page's URL as the argument (`"https://0-0-[...].edusercontent.com/add-message?s=Hello&user=jpolitz"`)
* The field `chat` has an initial value of `""`, and the value gets changed to `"jpolitz: Hello\n"`.

### Adding the second message:

<img src="/img/add-message-2.png" alt="Added a message using /add-message?s=How are you&user=yash" width="600"/>

<img src="/img/chat-2.png" alt="Chat after adding message 2" width="500"/>

* The method `handleRequest` is called with the page's URL as the argument (`"https://0-0-[...].edusercontent.com/add-message?s=How are you&user=yash"`)
* The field `chat` has an initial value of `"jpolitz: Hello\n"`, and the value gets changed to `"jpolitz: Hello\nyash: How+are+you\n"`. The old message was concatenated with the new message.

## Part 2: Logging in to `ieng6` <a name="part-2"></a>

<img src="/img/ls-keys.png" alt="ssh key files are in .ssh directory" width="300"/>

* __Private__ key on my computer: /Users/sophiazhu/.ssh/id_rsa
* __Public__ key on `ieng6` remote server: /home/linux/ieng6/oce/8o/soz007/.ssh/authorized_keys

This screenshot shows that I can log in without entering my password:

<img src="/img/ieng6-login.png" alt="logging in to ieng6 through Terminal" width="800"/>

## Part 3: What I learned <a name="part-3"></a>

In week 2 lab, I learned that you can use Java to create web servers and handle URLs in various ways. In week 3 lab, I learned that you can use `ssh` keys to avoid having to enter your password each time you log into a remote server. 
