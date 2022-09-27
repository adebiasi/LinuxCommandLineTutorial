
## 11. The Environment

### Hints:
- Hidden files start with a period.
- Shell scripts and bash startup files use a # symbol to begin a comment.

### Useful commands:
- **printenv | less**: Display only the environment variables.
- **printenv USER**: List the value of a specific variable.
- **set | less**: Display both the shell and environment variables.
- **echo $HOME**: View the contents of a variable.
- **alias**: Display the aliases.
- **cp .bashrc .bashrc.bak**: Create a backup of the file '.bashrc' (.bak, .sav, .old, and .orig are all popular ways of indicating a backup file).
- **source ~/.bashrc**: Force bash to reread the modified .bashrc file.

### Popular text-based editors:
- **nano**: simple, easy-to-use editor. ctrl-X to exit (notation ^X). ctrl-O to save.
- **vi (or vim)**: traditional editor for Unix-like systems.
- **emacs**: gigantic, all-purpose, doeseverything programming environment.

## 12. A Gentle Introduction to VI (pronounced “vee eye”)

### Hints:
- When vi starts, it begins in command mode.
- Press 'i' to go to *insert mode*.
- Press 'ESC' key to go to *command mode*.

### Useful commands:
- **vi**: To start vi.
- **vi foo.txt**: Create the file 'foo.txt' and open it in vi.

### Useful commands in vim:
- **esc key twice**: To find you way if you get “lost” in vi.
- **:q**: To exit.
- **:q!**: To exit discarding unsaved changes.
- **:w**: To save.
- **u**: To undu.
- **A**: Append text to the end of a line.
- **o**: Insert the line below the current line.
- **O**: Insert the line above the current line.
- **x**: Delete a character at the cursor location.

In the book there are many other commands not mentioned here.

### 13. Customizing the Prompt

### Hints:
- The prompt is defined by an environment variable named PS1. Look at it typing 'echo $PS1'.
- **PS1="\A \h \$ "**:  to add time-of-day to our prompt.
- We can make the prompt permanent by adding it to our .bashrc file.
