# Shell Scripting Basics

## Learning goals

- Understand the basics of shell scripting
- Learn how to mark a shell script as executable and run it
- Learn what shell variables are and how to use them

## Introduction

*Shell scripting* is an extremely powerful tool for automating tasks and processing data. It's an essential skill for most developers, unquestionably so for sysadmins and devops engineers.

**Shell scripts** are essentially a series of commands that are executed in a shell, like the ones we have been using in the previous chapters. These commands are then saved to a text file, which can be executed by the shell. They can both receive input and return output.

These scripts have the advantage of being portable, meaning that you can run them in any shell on any computer (granted you don't try executing commands or programs that don't exist on the host computer).

## Writing a shell script

Like we touched on earlier, shell scripts are simply text files. So in order to write one, all we need to do is create a new text file. The only consideration is that the file should have a `.sh` extension; for example, `script.sh`. 

Let's start by dissecting an example of a simple shell script:

```bash
#!/bin/bash
greeting="Hello world!"

# Print the value of the "greeting" variable
echo $greeting
```

> Note: You should try re-typing the example in `vim` or `nano`! e.g. `vim script.sh`.

Let's break apart each of the lines:

```bash
#!/bin/bash
```
- This line specifies what shell interpreter should be used to run the script. In this case, we're using `bash`, but in some cases other shells could be used. For the most part, however, you will see `bash` or `sh` in this line.

```bash
greeting="Hello world!"
```
- This line sets a *variable* called `greeting` and sets its value to `Hello world!`. A **variable** is simply a way of storing a value or set of values. You assign it a name, in this case `greeting`, and then assign it a value with `=`. 

```bash
# Print the value of the "greeting" variable
```
- This line is what is known as a *comment*. A **comment** is a line of code ignored by the *interpreter*; in other words, it won't be executed. It starts with a `#`, and whatever follows it is part of the comment. The point of comments is to let us (or other programmers) know information. For example, explain what a certain complicated section is doing, or explain *why* something is being done in a certain part of the code.

```bash
echo $greeting
```
- This line prints the `greeting` variable we made. `echo` is the name of a shell command that simply prints what follows it. The `$` sign is prepended to our variable name when we are trying to read from it.

Keep in mind that shell scripts are *whitespace-sensitive*. This means that your script might have issues if it's indented incorrectly. Indentation simply refers to the amount of spaces after the line begins. We'll go more over that later; for now, just keep it in mind.

## Variables

As we briefly touched on above, variables are a way of temporarily storing data. We can give them any name in order to make it easy to remember what is stored in that location. In practice, variables names are usually descriptive of their contents. For instance, if we would like to store the value of the number five in a variable:

```bash
number=5
```

This stores a variable in memory with the name `number` and a value of `5`. Variables can store many types of data such as numbers, strings of text, and boolean values (true or false).

```bash
isReady=false
string="This is a string (of text); notice the double quotes"
```

Variable names are case-sensitive and cannot start with a numerical digit, meaning these statements would create two different variables:

```bash
number=6
NUMBER=7
```

To access the value we stored, we would call the name of the variable preceded by a dollar sign:

```bash
echo "The value stored is $number"
```

Variables can be of much use to us in scripts, particularly because they can also store the output of a bash command. Say we want our shell script to return the current date and time, we may approach it this way:

```bash
current_date=$(date)
echo "Today is $current_date"
```

In the first line above, `date` is a bash command that returns the date and time at runtime and looks something like this:

```bash
Wed Mar 3 14:15:09 EST 2021
```

This value is what gets stored in our `current_date` variable and summoned by the echo following it. What gets printed for the user on the screen should be:

```bash
Today is Wed Mar 3 14:15:09 EST 2021
```

In shell scripting, variables are named using alphanumeric characters, underscores, and numbers (but cannot start with a number). Conventionally, we use uppercase letters for the shell environment variables, and lowercase letters for variables that only live for the duration of our script.

## Arithmetic

Just like in the standard shell, you can perform basic arithmetic in your shell scripts using the `expr` command.

Here's an example:

```bash
add_result=$(expr 5 + 3)          # stores 8
sub_result=$(expr 200 - 150)      # stores 50
mult_result=$(expr 4 * 2)         # stores 8
div_result=$(expr 15 / 3)         # stores 5
mod_result=$(expr 7 % 3)          # stores 1
```

Most of that should be self-explanatory, although you might be unfamiliar with *modulo*, which uses the `%` operator.

While it may sound technical, all **modulo** means is simply the remainder of a division. So for instance, in the example above, `7 % 3` returns `1` because `3` only goes into `7` twice, leaving a `1` remaining.

While it may seem relatively useless at first glance, modulo is actually very useful for checking if something is divisible by something else since you can just evaluate if the remainder is 0. We'll see an example of this later on in a lab.

## Running shell scripts

Before executing a shell script, you nee dto ensure that it has the right permissions.

File permissions can be changed using the `chmod` command, for example:

```bash
$ chmod +x /path/to/script.sh
# or if you're in the folder already
$ chmod +x script.sh
```

The `+x` argument is what gives the file the `execute` permission; in other words, allows the shell script to be run.

Once it has permission, running it is extremely simple:

```bash
$ /path/to/script.sh
# or again, if you're in the folder already
$ ./script.sh
```

After inputting the command, the script will run line-by-line as if you had typed each one into the terminal.

## Conclusion

Well done making it through this lesson! While daunting at first, you will find that it doesn't take too long to become acquainted with the basics of shell scripting. In the next lesson we'll take a look at how to handle user input and control flow, after which you'll be ready to go!
