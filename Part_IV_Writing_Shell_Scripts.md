## 24. Writing Your First Script

### Hints
- The \#\! (called 'shebang') is used to specify the interpreter that should be used to execute the script that follows. Every shell script should include this as its first line (e.g. '#!/bin/bash').
- The ~/bin directory is a good place to put scripts intended for personal use. If we write a script that everyone on a system is allowed to use, the traditional location is /usr/local/bin.
- export PATH=~/bin:"$PATH": Add this line to the ~/.bashrc to add the 'bin' folder to the PATH variable. 


### Configuring vim for Script Writing
- **:syntax on**: Turn on syntax highlighting.
- **:set hlsearch**: Turn on the option to highlight search results.
- **:set tabstop=4**: Set the number of columns occupied by a tab character.
- **:set autoindent**: Turn on the “auto indent” feature. (To stop indentation, press ctrl-D.)
- These changes can be made permanent by adding these commands (without the leading colon characters) to your '~/.vimrc' file.


### Useful commands
- **chmod 755 hello_world**: 755 for scripts that everyone can execute.
- **./hello_world**: Execute our script. We must precede the script name with an explicit path.
- **echo $PATH**: View the contents of PATH. If our script is located in any of the directories in the list we don't need to specify the explicit path.

## 25. Starting a Project

### Hints
- The shell makes no distinction between variables and constants. A common convention is to use uppercase letters to designate constants and lowercase letters for true variables.
- It’s good practice is to enclose variables and command substitutions in double quotes to limit the effects of word-splitting by the shell.

### Examples of scripts

#### Variables declarations
```bash 
a=z # Assign the string "z" to variable a.
b="a string" # Embedded spaces must be within quotes.
c="a string and $b" # Other expansions such as variables can be expanded into the assignment.
d="$(ls -l foo.txt)" # Results of a command.
e=$((5 * 7)) # Arithmetic expansion.
f="\t\ta string\n" # Escape sequences such as tabs and newlines.
```

#### Retrieve a file from a remote FTP server

Using <<-, the shell will ignore leading tab characters (but not spaces) in the here document. This allows a here document to be indented, which can improve readability. The string \_EOF\_ (meaning end of file, a common convention) was selected as the token and marks the end of the embedded text.

```bash 
#!/bin/bash
# Script to retrieve a file via FTP
FTP_SERVER=ftp.nl.debian.org
FTP_PATH=/debian/dists/stretch/main/installer-amd64/current/images/cdrom
REMOTE_FILE=debian-cd_info.tar.gz
ftp -n <<- _EOF_
     open $FTP_SERVER
     user anonymous me@linuxbox
     cd $FTP_PATH
     hash
     get $REMOTE_FILE
     bye
     _EOF_
ls -l "$REMOTE_FILE"
```

## 26. Top-Down Design

### Shell examples

The following is a script that demonstrates the use of a shell function:
```bash
1 #!/bin/bash
2
3 # Shell function demo
4
5 function step2 {
6 echo "Step 2"
7 return
8 }
9
10 # Main program starts here
11
12 echo "Step 1"
13 step2
14 echo "Step 3"
```

Here is an example script that demonstrates how local variables are defined and used:
```bash
#!/bin/bash
# local-vars: script to demonstrate local variables
foo=0 # global variable foo
funct_1 () {
local foo # variable foo local to funct_1
foo=1
echo "funct_1: foo = $foo"
}
funct_2 () {
local foo # variable foo local to funct_2
foo=2
echo "funct_2: foo = $foo"
}
echo "global: foo = $foo"
funct_1
echo "global: foo = $foo"
funct_2
echo "global: foo = $foo"
```

## 27. Flow Control: Branching with if

The if statement has the following syntax:
```bash
if commands; then
    commands
[elif commands; then
    commands...]
[else
    commands]
fi
```

### Useful commands
- **\[ expression \]**: The test command performs a variety of checks and comparisons.


Here we have a script that demonstrates some of the file expressions:

```bash
#!/bin/bash
# test-file: Evaluate the status of a file
FILE=~/.bashrc
if [ -e "$FILE" ]; then
     if [ -f "$FILE" ]; then
         echo "$FILE is a regular file."
     fi
     if [ -d "$FILE" ]; then
         echo "$FILE is a directory."
     fi
     if [ -r "$FILE" ]; then
         echo "$FILE is readable."
     fi
     if [ -w "$FILE" ]; then
         echo "$FILE is writable."
     fi
     if [ -x "$FILE" ]; then
         echo "$FILE is executable/searchable."
     fi
else
    echo "$FILE does not exist"
    exit 1
fi
exit
```

Here is a script that incorporates string expressions:
```bash
#!/bin/bash
# test-string: evaluate the value of a string
ANSWER=maybe
if [ -z "$ANSWER" ]; then
     echo "There is no answer." >&2
     exit 1
fi
if [ "$ANSWER" = "yes" ]; then
     echo "The answer is YES."
elif [ "$ANSWER" = "no" ]; then
echo "The answer is NO."
     elif [ "$ANSWER" = "maybe" ]; then
echo "The answer is MAYBE."
else
     echo "The answer is UNKNOWN."
fi
```

Here is a script that uses integer expressions:
```bash
#!/bin/bash
# test-integer: evaluate the value of an integer.
INT=-5
if [ -z "$INT" ]; then
     echo "INT is empty." >&2
     exit 1
fi
if [ "$INT" -eq 0 ]; then
     echo "INT is zero."
else
     if [ "$INT" -lt 0 ]; then
          echo "INT is negative."
     else
          echo "INT is positive."
     fi
     if [ $((INT % 2)) -eq 0 ]; then
          echo "INT is even."
     else
          echo "INT is odd."
     fi
fi
```

It is possible to use also logical operators (&&, ||, !)

## 28. Reading Keyboard Input

read can assign input to multiple variables, as shown in this script:
```bash
#!/bin/bash
# read-multiple: read multiple values from keyboard
echo -n "Enter one or more values > "
read var1 var2 var3 var4 var5
echo "var1 = '$var1'"
echo "var2 = '$var2'"
echo "var3 = '$var3'"
echo "var4 = '$var4'"
echo "var5 = '$var5'"
```

With the -p option, we can provide a prompt string. With the -t and -s options, we can write a script that reads “secret” input and times out if the input is not completed in a specified time:
```bash
#!/bin/bash
# read-secret: input a secret passphrase
if read -t 10 -sp "Enter secret passphrase > " secret_pass; then
     echo -e "\nSecret passphrase = '$secret_pass'"
else
     echo -e "\nInput timed out" >&2
     exit 1
fi
```

If no variables are listed after the read command, a shell variable, REPLY, will be assigned all the input.

```bash
#!/bin/bash
# read-single: read multiple values into default variable
echo -n "Enter one or more values > "
read
echo "REPLY = '$REPLY'"
```

A common type of interactivity is called menu-driven:
```bash
#!/bin/bash
# read-menu: a menu driven system information program
clear
echo "
Please Select:
1. Display System Information
2. Display Disk Space
3. Display Home Space Utilization
0. Quit
"
read -p "Enter selection [0-3] > "
if [[ "$REPLY" =~ ^[0-3]$ ]]; then
     if [[ "$REPLY" == 0 ]]; then
          echo "Program terminated."
          exit
     fi
     if [[ "$REPLY" == 1 ]]; then
          echo "Hostname: $HOSTNAME"
          uptime
          exit
     fi
     if [[ "$REPLY" == 2 ]]; then
          df -h
          exit
     fi
     if [[ "$REPLY" == 3 ]]; then
          if [[ "$(id -u)" -eq 0 ]]; then
               echo "Home Space Utilization (All Users)"
               du -sh /home/*
          else
               echo "Home Space Utilization ($USER)"
               du -sh "$HOME"
          fi
          exit
     fi
else
     echo "Invalid entry." >&2
     exit 1
fi
```

## 29. Flow Control: Looping with while/until

A bash script could be constructed as follows:
```bash
#!/bin/bash
# while-count: display a series of numbers
count=1
while [[ "$count" -le 5 ]]; do
     echo "$count"
     count=$((count + 1))
done
echo "Finished."
```

Here we see a version of the while-menu program incorporating both break and continue:
````bash
#!/bin/bash
# while-menu2: a menu driven system information program
DELAY=3 # Number of seconds to display results
while true; do
     clear
     cat <<- _EOF_
     Please Select:
     1. Display System Information
     2. Display Disk Space
     3. Display Home Space Utilization
     0. Quit
     _EOF_
     read -p "Enter selection [0-3] > "
     if [[ "$REPLY" =~ ^[0-3]$ ]]; then
          if [[ "$REPLY" == 1 ]]; then
               echo "Hostname: $HOSTNAME"
               uptime
               sleep "$DELAY"
               continue
          fi
          if [[ "$REPLY" == 2 ]]; then
               df -h
               sleep "$DELAY"
               continue
          fi
          if [[ "$REPLY" == 3 ]]; then
               if [[ "$(id -u)" -eq 0 ]]; then
                    echo "Home Space Utilization (All Users)"
                    du -sh /home/*
               else
                    echo "Home Space Utilization ($USER)"
                    du -sh "$HOME"
               fi
               sleep "$DELAY"
               continue
          fi
          if [[ "$REPLY" == 0 ]]; then
               break
          fi
     else
          echo "Invalid entry."
          sleep "$DELAY"
     fi
done
echo "Program terminated."
```

### Hints
- How indentation works:
   - Next lines after 'then', 'else' have increased indentation.
   - 'fi', 'else', 'done' have decreased indentation. At the same level of 'if', 'while'.
   
## 30. Troubleshooting
