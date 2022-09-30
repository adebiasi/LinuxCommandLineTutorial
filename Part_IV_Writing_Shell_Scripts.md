## 24. Writing Your First Script

## Hints
- The \#\! (called 'shebang') is used to specify the interpreter that should be used to execute the script that follows. Every shell script should include this as its first line (e.g. '#!/bin/bash').
- The ~/bin directory is a good place to put scripts intended for personal use. If we write a script that everyone on a system is allowed to use, the traditional location is /usr/local/bin.
- export PATH=~/bin:"$PATH": Add this line to the ~/.bashrc to add the 'bin' folder to the PATH variable. 


## Configuring vim for Script Writing
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
