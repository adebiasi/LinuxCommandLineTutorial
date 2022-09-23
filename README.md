# Tutorial of the Linux Command Line (Part one)

*“Graphical user interfaces make easy tasks easy, while command line interfaces make difficult tasks possible.”*

*“Everything is a file.”*

Tutorial extracted from the book *The Linux Command Line by William Shotts*.

## 1. Introduction

### Useful commands
- **df**: To see the current amount of free space on our disk drives.
- **free**: to display the amount of free memory, enter the free command.
- **exit (or CTRL-D)**: to end a terminal session.

## 2. Navigation
### Hints:
- do not embed spaces in filenames.

### Useful commands
- **pwd**: Print name of current working directory.
- **cd**: Change directory.
- **cd \<and nothing else\>**: Change the working directory to your home directory.
- **cd -**: Changes the working directory to the previous working directory.
- **ls**: List directory contents.

### Other

Example of absolute pathnames: 
> cd /usr/bin

Example of relative pathnames (. means 'current working directory'): 
> cd ./bin or cd bin

## 3. Exploring the System

### Useful commands
- **ls**: List directory contents.
- **ls -l**: to reveal more detail.
- **file**: Determine file type.
- **less**: View file contents.

### Hints: 
- If you are using a mouse, you can double-click a filename to copy it and middle-click to paste it into commands.

## 4. Manipulating Files and Directories

### Wildcards
- **\***: Matches any characters.
- **\?**: Matches any single character.
- **[characters]**: Matches any character that is a member of the set characters.
- **[!characters]**: Matches any character that is not a member of the set characters.
- **[[:class:]]**: Matches any character that is a member of the specified class (e.g. alnum, alpha, digit, lower, upper).

### Useful commands
- **cp**: Copy files and directories.
- **cp dir1/\* dir2**: copy all the files in dir1 into dir2. The directory dir2 must already exist.
- **cp dir1 .**: copy all the files in dir1 into the current working directory.
- **mv**: Move/rename files and directories.
- **mv file1 file2 dir1**: Move file1 and file2 into directory dir1. The directory dir1 must already exist.
- **mkdir**: Create directories (e.g. mkdir dir1 dir2 dir3).
- **rm**: Remove files and directories.
- **rm -r file1 dir1**: Delete file1 and dir1 and its contents.
- **ln file link**: Create a hard link. When we create hard links, we are actually creating additional name parts that all refer to the same data part.
- **ln -s file link -r**: Create a symbolic link. They operate in much the same way as a Windows shortcut.

### Hints
- Whenever you use wildcards with rm, test the wildcard first with ls.

## 5. Working with Commands

### Useful commands
- **type**: Indicate how a command name is interpreted. It can be used to find out whether the name of a command that you want to create is already being used.
- **which**: Display which executable program will be executed. It determine the exact location of a given
executable. It works only for executable programs.
- **help**: Get help for shell builtins. When square brackets appear in the description of a command's syntax, they indicate optional items.
- **man**: Display a command’s manual page.
- **apropos**: Display a list of appropriate commands.
- **info**: Display a command’s info entry.
- **whatis**: Display one-line manual page descriptions.
- **alias**: Create an alias for a command. It vanishes when your shell session ends.
- **cd /usr; ls; cd -**: Example of three combined commands on one line.
- **alias foo='cd /usr; ls; cd -'**: Create the command 'foo' from the previous example.
- **unalias foo**: To remove the alias 'foo'.
- **alias \<and nothing else\>**: To see all the aliases defined in the environment.

## 6. Redirection

### Useful terms
- By default, both **standard output (stdout)** and **standard error (stderr)** are linked to the screen and not saved into a disk file.
- By default **standard input (stdin)** is attached to the keyboard.

### Useful commands
- **cat**: Concatenate files
- **sort**: Sort lines of text
- **uniq**: Report or omit repeated lines
- **grep**: Print lines matching a pattern
- **wc**: Print newline, word, and byte counts for each file
- **head**: Output the first part of a file
- **tail**: Output the last part of a file
- **tee**: Read from standard input and write to standard output and files
