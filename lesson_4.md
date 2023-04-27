# [Working with HTTP](https://launchschool.com/lessons/0e67d1ce/assignments)

## [What to Focus on](https://launchschool.com/lessons/0e67d1ce/assignments/b9609f49)

- HTTP: This chapter uses Bash and other network utilities, but this is all to better understand HTTP an how it enables network connections between client and server.
-  HTTP and the structure of messages: HTTP can be seen as a set of rules for structuring messages exchanged between applications. Understand these rules and how to apply them.
-  HTTP is a request-response protocol: One of the fundamental aspects of HTTP is its request-response behaviour. Try to form a solid mental model aruond this.

## [Using Telnet to explore HTTP](https://launchschool.com/lessons/0e67d1ce/assignments/20d4226d)

- Telnet and netcat don't seem to be present on my AWS cloud9, so i'm coding along on VSCode with the inbuilt Netcat. 

<img width="1176" alt="Screenshot 2023-04-27 at 08 49 39" src="https://user-images.githubusercontent.com/78854926/234795741-347a194e-1518-4c48-baba-8bc4c1c3ee4f.png">

## [Speaking the same language](https://launchschool.com/lessons/0e67d1ce/assignments/ea90d10b)

### In AWS Cloud9

- I installed Netcat with `yum install nc`
- I then ran `nc --recv-only -v launchschool.com 80`
- But after that I can't seem to get it to repsond, so I switch to using Netcat in VSCode:

<img width="497" alt="Screenshot 2023-04-27 at 09 50 35" src="https://user-images.githubusercontent.com/78854926/234810875-43460fad-60f7-4d4f-a1f2-804db4c6f334.png">

### In VSCode

- LaunchSchool's homepage does not respond to `GET /` because I haven't specified the version of HTTP to use.

<img width="858" alt="Screenshot 2023-04-27 at 09 37 14" src="https://user-images.githubusercontent.com/78854926/234807364-f5a81b32-e295-41b1-b47a-15c256d7a4cd.png">

- Asking for the LaunchSchool Homepage in an outdated HMTL 0.9 returns a 400 error code:

  <img width="704" alt="Screenshot 2023-04-27 at 09 27 02" src="https://user-images.githubusercontent.com/78854926/234804706-d554d76c-892e-4562-a044-4bea4e47850b.png">

- So I try asking for the homepage in HTML 1.1, which also returns a 400 error code (as expected in LS material):

Seeking LS homepage:

<img width="691" alt="Screenshot 2023-04-27 at 09 38 55" src="https://user-images.githubusercontent.com/78854926/234807890-c3cae6a3-3a44-40ed-a3af-b6525624e406.png">

Although it does work with the Google homepage:

<img width="1152" alt="Screenshot 2023-04-27 at 09 31 33" src="https://user-images.githubusercontent.com/78854926/234805826-f4d2c1ca-d87a-4582-b1e6-0c5e47416ee6.png">

- Any response code that is in the 400s means there's a problem on the client-side. The 400 code specifically means there's a syntax error in the structure of the request. In other words the server is saying, "I don't understand what you just asked me".

- LS material says that specifying the HTTP version with `GET / HTTP/0.9` will get a 505 error:

  <img width="903" alt="Screenshot 2023-04-27 at 09 17 26" src="https://user-images.githubusercontent.com/78854926/234802347-6d033a93-39dc-4aa9-bcfa-1e891dd8d9ba.png">

- The response code in the 500s which means an error on the server side. This is because  the request was valid, but the server cannot communicate in that version of HTTP.

, but I am still getting the same 400 error (or it works fine - 200 OK - with google homepage):

  <img width="662" alt="Screenshot 2023-04-27 at 09 58 52" src="https://user-images.githubusercontent.com/78854926/234813101-27f06734-a06d-4fae-9681-6267300c0397.png">

- Apparently in HTTP 1.1 the client must specify the host name in the header, so:

<img width="842" alt="Screenshot 2023-04-27 at 10 16 55" src="https://user-images.githubusercontent.com/78854926/234817732-18720de0-925d-4b7b-880b-d2a1ff41d279.png">

- Error messages in the 300s relate to redirects. The client needs to take some additional action to complete the request. Here it's because the server is set up to redirect all http to https. The response includes a `Location` header which tells the client where it can now find the resource it requested. If the client were a browser it would automatically follow this redirect. Another interesting note is the TCP dfoesn't close the connection, but sets it to `keep-alive`. This is because it is expecting a follow-up request from the client.

## [Implementing your own HTTP server: Project overview](https://launchschool.com/lessons/0e67d1ce/assignments/be0e4401)

- HTTP is a set of rules for structuring a message between two points. It's up to the client and server to implement those rules, which result in how the message is interpreted.
- We will now implement our own basic server. It will only:
  - respond to GET requests
  - serve static text files.
- We will use netcat with some bash scripting. 

### Bash

- A command language for interacting with a system environment.

### Netcat

- A network utility which provides a variety of features. One feature is providing TCP connections between two network end-points.

### Installing Netcat

- already done? I'm doing a brew install anyway using `brew install netcat`

## [Bash Basics](https://launchschool.com/lessons/0e67d1ce/assignments/a0f37a79)

### Input and Output

<img width="320" alt="Screenshot 2023-04-27 at 10 43 52" src="https://user-images.githubusercontent.com/78854926/234825054-0f4930b1-65ff-4769-ba23-a24c2de287d3.png">

### Variables

- Like any other scripting language, Bash stores temporary data in variables, like this: `name='Sandy'` (no spaces) 
- Case sensitive:
  - `Cat='Maggy'` has to be called with `Cat`§
- Variable references must be prepended with $
  - `$Cat`
- We can pass bash variables as arguments to commands:
  - `echo $Cat`
- If you pass multiple varible names to `read` and then assign a multi-word string, it will divide the string at the spaces:

```
$ read first second third
Do you like apples?
$ echo $first # Do
$ echo $second # you
$ echo $third # like apples?
```

### Bash Files

- These bash commands are executable files.
- We can also create our own executables.
- By convention bash files are appended with `.sh`

Instructions:
- Create a directory called `bash_basics`
- In that directory create a file called `hello_world.sh`
- in that file write `echo "Hello World!"`
- in the command line write `bash hello_world.sh` and it will run the command in the `hello_world.sh` file.

Alternatively: 
- the `hello_world.sh` file can include `#!/bin/bash` at the beginning of the file. The `#!` character sequence is known as the 'shebang' and is followed by the path to the file or program that should be used to run the subsequent code in the bash file.
- Trying to run the file now: `./hello_world.sh` returns `Permission denied. So we need to grant the permission.
- `$ chmod +x hello_world.sh`
- Then it works.

### Conditional statements

- Bash provides a way to work through conditional logic with `if` statements.
- They are opened with `if` and closed with `fi`:

```
if [[ <condition> ]]
then
  <commands>
fi
```
- The condition is written between two square brackets, unless it is a boolean:

```
if true
then
  echo 'True'
fi
```

- The double square-brackets are in fact shorthand for running the `test` command. The test command, which provides operators for evaluating things. See below:

|Operator|Description|
| :--- | :---: |
|**Strings**|
|-n string|Length of string is greater than 0|
|-z string|Length of string is 0 (string is an empty string)|
|string_1 = string_2|	string_1 is equal to string_2|
|string_1 != string_2|	string_1 is not equal to string_2|
|**Integers**|
|integer_1 -eq integer_2|	integer_1 is equal to integer_2|
|integer_1 -ne integer_2|	integer_1 is not equal to integer_2|
|integer_1 -gt integer_2|	integer_1 is greater than integer_2|
|integer_1 -ge integer_2|	integer_1 is greater than or equal to integer_2|
|integer_1 -lt integer_2|	integer_1 is less than integer_2|
|integer_1 -le integer_2|	integer_1 is less than or equal to integer_2|
|**Files**|
|-e path/to/file|	file exists|
|-f path/to/file|	file exists and is a regular file (not a directory)|
|-d path/to/file|	file exists and is a directory|

- Example1: String longer than 0?

```
string='Hello'

if [[ -n $string ]]
then
  echo $string
fi
```

- Example 2: two integers are equal?

```
integer_1=10
integer_2=10

if [[ $integer_1 -eq $integer_2 ]]
then
  echo $integer_1 and $integer_2 are the same!
fi
```

- Example 3: Tests is file exists:

```
if [[ -e ./hello_world.sh ]]
then
  echo 'File exists'
fi
```

### Testing multiple conditions:

- We can:
  - Nest `if` statements
  - `else` and `elif`
  - Use boolean operators like `&&` and `||`

Example 1: Nested `if` statement:

```
integer=4

if [[ $integer -lt 10 ]]
then
  echo $integer is less than 10

  if [[ $integer -lt 5 ]]
  then
    echo $integer is also less than 5
  fi
fi
```

Example 2: two conditional branches with `if` and `else`

```
integer=15

if [[ $integer -lt 10 ]]
then
  echo $integer is less than 10
else
  echo $integer is not less than 10
fi
```

Example 3:

```
integer=15

if [[ $integer -lt 10 ]]
then
  echo $integer is less than 10
elif [[ $integer -gt 20 ]]
then
  echo $integer is greater than 20
else
  echo $integer is between 10 and 20
fi
```

Example 4:

```
integer=15

if [[ $integer -gt 10 ]] && [[ $integer -lt 20 ]]
then
  echo $integer is between 10 and 20
fi
```

Example 5:

```
integer=12

if [[ $integer -lt 5 ]] || [[ $integer -gt 10 ]]
then
  echo $integer is less than 5 or greater than 10.
fi
```

Example 6:

```
integer=8

if [[ ! ($integer -lt 5 || $integer -gt 10) ]]
then
  echo $integer is between 5 and 10.
fi
```

- In bash the `!` can be used in multiple different ways.

### Loops

- Bash has `for`, `until` and `while` loops. The second 2 are as you know them, but the `for` loop iterates through a list.
- while loops:

```
counter=0
max=10

while [[ $counter -le $max ]]
do
  echo $counter
  ((counter++))
done
```

### Funtions

- You can save multiple commands in a chunk of code called a 'function'
- Functions can take 0, 1 or more arguments.

Example 1:
```
greeting () {
  echo Hello $1
}

greeting 'Peter' # outputs 'Hello Peter'
```
- The variable is scoped to the function, which means we can access this variable within the function body but not outside it.
- Subsequent arguments would have 2, 3, 4 etc. assigned to them:

```
greeting () {
  echo "Hello $1"
  echo "Hello $2"
}
```
- Variables can be interpolated in double quoted strings.

greeting 'Peter' 'Paul' # outputs 'Hello Peter' 'Hello Paul' on separate lines

## [Working with Netcat](https://launchschool.com/lessons/0e67d1ce/assignments/7989eb3f)

- Netcat is a Network utility used for ereading and writing data accross network connections using TDP or UDP. (It's like Telnet from before).

```
$ netcat -v google.com 80
```
- The verbose flag means netcat will print messages when certain things happen, like a connection opening and closing.

- This is the command for installing netcat:

```
sudo yum -y install netcat
```

- As well as connecting to a domain and port, netcat also allows you to listen to that doman/port for incoming connections:

```
$ netcat -lv 2345 #              => Warning: Inverse name lookup failed for `0.0.9.41'
# LS said the message should be: => Listening on [0.0.0.0] (family 0, port 2345)
```
but it does work on AWS Cloud9:

<img width="431" alt="Screenshot 2023-04-27 at 16 30 57" src="https://user-images.githubusercontent.com/78854926/234911862-1ed46d66-85f6-4008-8e14-da5680ae7f90.png">

`netcat -v localhost 2345` does work `=> localhost [127.0.0.1] 2345 (dbm) open`

This will be our client instance.
You should now have two terminal windows.; One acting as a client, the other as a server. Typing text into either one will appear in the other as well. Congratulations, you have made A TCP connection.
- terminate the Netcat session with `command + C`

## [Implementing our own HTTP server: Basic Program Structure](https://launchschool.com/lessons/0e67d1ce/assignments/2e3c6bc3)

 - In the previous exercise we sent arbitrary messages. HTTP rquires a certain structure and now we will attempt to achieve that.

## [Implementing our own HTTP server: Sending a simple response]
## [Implementing our own HTTP server: Processing the request]
## [Implementing our own HTTP server: Serving HTML]
## [Implementing our own HTTP server: Working with the browser]
## [Implementing our own HTTP server: adding Hyperlinks]
## [Summary]

Overview:

|  | Once | Twice | Thrice | Comprehension | Retention
| :--- | :---: | :---: | :---: | :--- | :---
|1. What to Focus on|26th April|
|2. Using Telnet to explore HTTP|27th April|
|3. Speaking the same language|27th April|
|4. Implementing your own HTTP server: Project overview|27th April|
|5. Bash Basics|27th April|
|6. Working with Netcat
|7. Implementing our own HTTP server: Basic Program Structure
|8. Implementing our own HTTP server: Sending a simple response
|9. Implementing our own HTTP server: Processing the request
|10. Implementing our own HTTP server: Serving HTML
|11. Implementing our own HTTP server: Working with the browser
|12. Implementing our own HTTP server: adding Hyperlinks
|13. Summary
| + Read through Discussions |
