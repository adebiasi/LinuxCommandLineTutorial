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
- **ip**: Show/manipulate routing, devices, policy routing, and tunnels.
- **netstat**: Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
- **ftp**: Internet file transfer program. FTP (in its original form) is not secure because it sends account names and passwords in cleartext.
- **ftp fileserver**: Invoke the ftp program and have it connect to the FTP server fileserver.
- **sftp remote-sys**: It does not require an FTP server to be running on the remote host. It requires only the SSH server.
- **get filename**: In the ftp session, it tells the remote system to transfer the file 'filename' to the local system.
- **bye** (also 'quit' or 'exit'): In the ftp session, it logs off the remote server and end the ftp program session.
- **wget**: Non-interactive network downloader.
- **wget http://linuxcommand.org/index.php**: To download the first page of linuxcommand.org.
- **ssh**: OpenSSH SSH client (remote login program).
- **ssh remote-sys**: Connect to a remote host named 'remote-sys'.
- **ssh bob@remote-sys**: Connect to a remote host named 'remote-sys' specifying as user 'bob'.
- **ssh remote-sys \<command\>**: Execute a single command on a remote system.
- **ssh remote-sys 'ls *' \> dirlist.txt**: Perform an ls on the remote system and redirect the output to a file on the local system.
- **ssh remote-sys 'ls * \> dirlist.txt'**: Perform an ls on the remote system and redirect the output to a file on the remote system.
- **scp remote-sys:document.txt .**: Copy a document named document.txt from our home directory on the remote system, remote-sys, to the current working directory on our local system. scp requires the OpenSSH package.

## 17. Searching for Files

### Useful commands
