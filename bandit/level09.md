# Bandit Level 9 → Level 10

In this level the passsword is stored in the file data.txt in one of the few human-readable strings, preceded by several `=` characters. So to find the password I am going to introduce you to a new command to find human readble strings and that is the `strings` command.  The `-e` flag is used to specify the character encoding. We are assuming the human readable line is ASCII text so we use `s` for the encoding type.

We also know that the line with the password starts with a few `=` characters. We can look for this pattern in the file using the grep command.

We can combine all these commands into an single line using the `|` (pipe) operator.

So the command is : 
```bash
   cat data.txt | strings -e s | grep ==
````

![level9 screenshot](images/Screenshot11.png)
