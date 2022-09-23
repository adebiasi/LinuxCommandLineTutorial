# Tutorial of the Linux Command Line

*“Graphical user interfaces make easy tasks easy, while command line interfaces make difficult tasks possible”*

Tutorial extracted from the book *The Linux Command Line by William Shotts*.

## Introduction

### Useful commands
- **df**: To see the current amount of free space on our disk drives.
- **free**: to display the amount of free memory, enter the free command.
- **exit (or CTRL-D)**: to end a terminal session.

## Navigation
### Hints:
- do not embed spaces in filenames.

### Useful commands
- **pwd**: Print name of current working directory.
- **cd**: Change directory.
- **ls**: List directory contents.

### Other

Example of absolute pathnames: 
> cd /usr/bin

Example of relative pathnames (. means 'current working directory'): 
> cd ./bin or cd bin

## Exploring the System

### Useful commands
- **ls**: List directory contents.
- **ls -l**: to reveal more detail.
- **file**: Determine file type.
- **less**: View file contents.

### Hints: 
- If you are using a mouse, you can double-click a filename to copy it and middle-click to paste it into commands.

## Manipulating Files and Directories

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
- **ln file link**: Create a hard link.
- **ln -s file link -r**: Create a symbolic link. They operate in much the same way as a Windows shortcut.

### Hints
- Whenever you use wildcards with rm, test the wildcard first with ls.


