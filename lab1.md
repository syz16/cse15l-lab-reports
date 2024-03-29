# Lab Report 1: Jan 16, 2024
In this lab, I ran 3 common terminal commands (`cd`, `ls`, and `cat`) with either no arguments, a path to a directory as an argument, or a path to a file as an argument. I ran these commands in an Edstem workspace where I had cloned the lecture1 repository. These are my observations. 

* [Part 1: `cd`](#cd)
* [Part 2: `ls`](#ls)
* [Part 3: `cat`](#cat)

## Part 1: `cd` <a name="cd"></a>

### 1. No arguments
* Working directory: `/home/lecture1`
```
$ cd
```
* The working directory was changed to `/home`. If there are no arguments given, `cd` simply changes the directory to the home directory.
* There is no output since `cd` simply changes the directory and there was no error.

### 2. Path to directory as argument
* Working directory: `/home/lecture1`
```
$ cd messages
```
* The working directory was changed to `/home/lecture1/messages`.
This happened because the current working directory (`/home/lecture1`) was combined with the relative file path (`messages`) to make the absolute file path of `/home/lecture1/messages`, 
and the current working directory was changed to that.
* There is no output since `cd` simply changes the directory and there was no error. 

### 3. Path to file as argument
* Working directory: `/home/lecture1/messages`
```
$ cd en-us.txt
bash: cd: en-us.txt: Not a directory
```
* The output is an error. The file path leads to the file at `/home/lecture1/messages/en-us.txt`. You can only `cd` to a directory, not a file.
So, there is an error saying that the file is not a directory.

---

## Part 2: `ls` <a name="ls"></a>

### 1. No arguments
* Working directory: `/home/lecture1`
```
$ ls
Hello.class  Hello.java  messages  README
```
* The `/home/lecture1` directory contains 3 files: `Hello.class`, `Hello.java`, and `README`. It also contains 1 directory, `nessages`. These were all printed out in the output because `ls` with no arguments lists the names of files and directories in the current working directory.
* This output was not an error. 

### 2. Path to directory as argument
* Working directory: `/home/lecture1`
```
$ ls messages
en-us.txt  es-mx.txt  sv.txt  zh-cn.txt
```
* `ls` prints out the names of files and directories in a given directory. Here, the directory was `/home/lecture1/messages`, which contains 4 files named `en-us.txt`, `es-mx.txt`, `sv.txt`, and `zh-cn.txt`.
* This output was not an error. 

### 3. Path to file as argument
* Working directory: `/home/lecture1`
```
$ ls Hello.java
Hello.java
```
* The only file located at `/home/lecture1/Hello.java` is the file itself. Thus, `Hello.java` is printed. 
* This output was not an error.

---

## Part 3: `cat` <a name="cat"></a>

### 1. No arguments
* Working directory: `/home/lecture1`
```
$ cat
some text
some text
```
* There was no output and it seemed like the terminal was waiting for the user to complete the prompt.
* Then, anything I entered got repeated as an output. 
* When there is no argument, it seems like `cat` simply takes the input and prints it as output.
* There was not an error.

### 2. Path to directory as argument
* Working directory: `/home/lecture1`
```
$ cat messages
cat: messages: Is a directory
```
* `messages` refers to the directory at `/home/lecture1/messages`.
* The output was an error message. Since `messages` is a directory, there is no text to concatenate. 

### 3. Path to file as argument
* Working directory: `/home/lecture1/messages`
```
$ cat en-us.txt 
Hello World!
```
* The text in `/home/lecture1/messages/en-us.txt` was printed. If there were multiple files as arguments, they would be concatenated and printed one after the other. But since there was just one file as an argument, the text in `en-us.txt` was simply outputted.
* There was no error.

Here is an example of multiple files being concatenated:
```
$ cat en-us.txt es-mx.txt 
Hello World!
¡Hola Mundo!
```
