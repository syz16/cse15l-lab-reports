# Lab Report 1: Jan 16, 2024

## Part 1: `cd`

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

## Part 2: `ls`

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

## Part 3: `ls`

### 1. No arguments

### 2. Path to directory as argument

### 3. Path to file as argument
