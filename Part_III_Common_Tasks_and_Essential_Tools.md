# Part III Common Tasks and Essential Tools

## 14. Package Management

### Hints
- Package management is a method of installing and maintaining software on the system.
- **Package file**: Compressed collection of files that comprise the software package.


Packaging System Families:
- Debian-style (.deb): Debian, Ubuntu, Linux Mint, Raspbian.
- Red Hat–style (.rpm): Fedora, CentOS, Red Hat Enterprise Linux, OpenSUSE.

### Useful commands for packages from a Repository (apt-get)
- **apt-get update; apt-get install emacs**: Install the emacs text editor from an apt repository on a Debian system.
- **apt-get remove emacs**: Uninstall the emacs package from a Debian-style system.
- **apt-get update; apt-get upgrade**: Apply all available updates to the installed packages on a Debian-style system.
- **apt-cache show emacs**: See a description of the emacs package on a Debian-style system

### Useful commands for packages from a file (dpkg)
- **dpkg -i emacs-22.1-7.fc7-i386.deb**: Install or update the dowloaded emacs package.
- **dpkg -l**: Display a list of all the packages installed on the system.
- **dpkg -s emacs**: display whether emacs package is installed.
- **dpkg -S /usr/bin/vim**: See what package installed the /usr/bin/vim file on Debian.

## 15. Storage Media

### Useful commands
- **ls /dev**: List the names devices.
- **tail -f /var/log/messages**: Watch what the system is doing in near real-time.
- **mount**: Mount a file system. Entering the command without arguments will display a list of the file systems currently mounted.
- **mkdir /mnt/cdrom; mount -t iso9660 /dev/sdc /mnt/cdrom**: Create a directory and mount the '/dev/sdc' in the created directory.
- **mkdir /mnt/iso_image; mount -t iso9660 -o loop image.iso /mnt/iso_image**: Create a directory and mount the image file as though it were a device and attach it to the file system tree.
- **umount**: Unmount a file system (e.g. 'umount /dev/sdc').

### Less useful commands
- **fsck**: Check and repair a file system.
- **fdisk**: Manipulate disk partition table.
- **mkfs**: Create a file system.
- **dd**: Convert and copy a file.
- **genisoimage**: (mkisofs) Create an ISO 9660 image file.
- **wodim**: (cdrecord) Write data to optical storage media.
- **md5sum**: Calculate an MD5 checksum.

## 16. Networking

### Useful commands
- **ping**: Send an ICMP ECHO_REQUEST to network hosts. For example 'ping linuxcommand.org'. Press 'ctrl-C' to interrupt the command.
- **traceroute**: Print the route packets trace to a network host.
- **ssh**: OpenSSH SSH client (remote login program).
- **ssh remote-sys**: Connect to a remote host named 'remote-sys'.
- **ssh bob@remote-sys**: Connect to a remote host named 'remote-sys' specifying as user 'bob'.
- **ssh remote-sys \<command\>**: Execute a single command on a remote system.
- **ssh remote-sys 'ls \*' \> dirlist.txt**: Perform an ls on the remote system and redirect the output to a file on the local system.
- **ssh remote-sys 'ls * \> dirlist.txt'**: Perform an ls on the remote system and redirect the output to a file on the remote system.
- **scp remote-sys:document.txt .**: Copy a document named document.txt from our home directory on the remote system, remote-sys, to the current working directory on our local system. scp requires the OpenSSH package.

### Less useful commands
- **ip**: Show/manipulate routing, devices, policy routing, and tunnels.
- **netstat**: Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
- **ftp**: Internet file transfer program. FTP (in its original form) is not secure because it sends account names and passwords in cleartext.
- **ftp fileserver**: Invoke the ftp program and have it connect to the FTP server fileserver.
- **sftp remote-sys**: It does not require an FTP server to be running on the remote host. It requires only the SSH server.
- **get filename**: In the ftp session, it tells the remote system to transfer the file 'filename' to the local system.
- **bye** (also 'quit' or 'exit'): In the ftp session, it logs off the remote server and end the ftp program session.
- **wget**: Non-interactive network downloader.
- **wget http://linuxcommand.org/index.php**: To download the first page of linuxcommand.org.


## 17. Searching for Files

### Useful commands
- **find**: Search for files in a directory hierarchy.
- **find ~**: Produce a listing of our home directory.
- **find ~ | wc -l**: Count the number of files in our home directory.
- **find ~ -type f -name "\*.JPG" -size +1M | wc -l**: Look for all the regular files that match the wildcard pattern \*.JPG and are larger than one megabyte.
- **find ~ -type f -name '\*.bak' -print**: Every file in the user’s home directory (and its subdirectories) is searched for filenames ending in .bak. '-print' can be removed.
- **find ~ -type f -name '\*.bak' -delete**: Revove every file in the user’s home directory (and its subdirectories) ending in .bak.

### Less useful commands
- **locate**: Find files by name. Very recent files do not show up when using locate. To overcome this, run 'updatedb'.
- **locate bin/zip**: Search its database of pathnames and output any that contain the string 'bin/zip'.
- **xargs**: Build and execute command lines from standard input.
- **touch**: Change file times.
- **stat**: Display file or file system status.


## 18. Archiving and Backup

### Hints
- If you apply compression to a file that is already compressed, you will usually end up with a larger file. For example 'gzip picture.jpg'.
- gzip is a compression tool, tar is an archiver tool, zip is both.

### Useful commands
- **zip -r playground.zip playground**: Make a zip archive of our playground (r means recursive).
- **unzip ../playground.zip**: Extract the contents of a zip file.

### Less useful commands
- **gzip**: Compress or expand files.
- **gzip foo.txt**: Replace the original file with a compressed version named 'foo.txt.gz'.
- **gunzip foo.txt** (or gzip --decompress foo.txt.gz): Uncompress the file. It assumes that filenames end in the extension .gz, so it’s not necessary to specify it.
- **bzip2**: A block sorting file compressor.
- **tar cf playground.tar playground**: Create a tar archive named playground.tar that contains the entire playground directory hierarchy.
- **tar cf /media/BigDisk/home.tar /home**: Same command as above.
- **tar tf playground.tar**: List the contents of the archive.
- **tar xf ../playground.tar**: Extract the playground in a new location.
- **sudo tar xf /media/BigDisk/home.tar**: Same command as above.


## 19. Regular Expressions

### Hints
- Expression metacharacters: 
    - \^: the next element 'at the beginning' or 'negation' inside brackets.
    - \$: the preceding element 'at the end'.
    - \.: 'any single char'.
    - \[ \]: set of chars.
    - \{ \}: to express minimum and maximum numbers of required matches.
    - \-: range.
    - \?: make the preceding element optional.
    - \*: the item may occur any number of times.
    - \+: at least one instance of the preceding element.
    - \( \): 
    - \|: or. 
    - \\: next metachar is treated as normal char.
- When we pass regular expressions containing metacharacters on the command line, they must be enclosed in 'quotes'.

### Useful commands
- **grep -i '^..j.r$' /usr/share/dict/words**: “What’s a five-letter word whose third letter is j and last letter is r that means . . . ?”
- **grep -h xxx dirlist\*.txt**: We searched for any line in our files ...
   - **'.zip'**: that matches the regular expression .zip (any char followed by 'zip').
   - **'^zip'**: ... zip located at the beginning of the line.
   - **'zip$'**: ... zip located at the end of the line.   
   - **'\[bg\]zip'**: ... that contains the string bzip or gzip.
   - **'\[\^bg\]zip'**: ... preceded by any character except b or g.
   - **'\^\[ABCDEFGHIJKLMNOPQRSTUVWXZY\]'**: ... beginning with an uppercase letter.
   - **'^\[A-Z\]'**: ... beginning with an uppercase letter.
   - **^\[A-Za-z0-9\]'**: ... starting with letters and numbers.
   - **'\^(bz\|gz\|zip)'**: ... starting with either bz, gz, or zip.

## 20. Text Processing

### Useful commands
- **cat**: Concatenate files and print on the standard output.
- **sort**: Sort lines of text files.
- **uniq**: Report or omit repeated lines.
- **cut**: Remove sections from each line of files.
- **paste**: Merge lines of files.
- **join**: Join lines of two files on a common field.
- **comm**: Compare two sorted files line by line.
- **diff**: Compare files line by line.
- **patch**: Apply a diff file to an original.
- **tr**: Translate or delete characters.
- **sed**: Stream editor for filtering and transforming text.
- **aspell**: Interactive spellchecker.
