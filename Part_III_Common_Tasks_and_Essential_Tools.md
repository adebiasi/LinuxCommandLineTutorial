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
