# RHCSA Commands
### Getting Around The Command Line
### Documentation Commands

 - `man` is the best source to get extensive usage information
 - `man -k` to search the man database based on keywords
 - For the basic administration, the following sections matter most `man` (1) Executable programs or shell commands (5) File formats and conventions (8) System administration commands `passwd` 

### Editors

 - `nano` easy-to-use editor
 - `vi` or `vim` advanced editor,

### Vim Commands 

 - `:wq!` is how you write and quit the `vim` editor,
 - `Esc` Enter command mode,
 - `i` Enter input mode,
 - `o` Open new line in input mode,
 - `:q!` Quit without saving anything,
 - `dd` Delete the current line,
 - `yy` Copy (yank) the current line,
 - `p` Paste the text currently in the buffer,
 - `v`Enter visual mode,
 - `u` Undo the last operation,
 - `Ctrl-r` Redo the last operation,
 - `gg` Go the top of the document,
 - `G` Go to the end of the document,
 - `/text` Search for "text",
 - `?text` Search backwards for "text",
 - `^` Move to the start of line,
 - `$` Move to the end of line,
 - `w` Move to the next word

### Basics of Bash Shell

- `ls` list contents
- `cd` Change Directory
- `pwd` Present Working Directory
-  `>` combine files into a single `output`
-  `>>` append files
-  `2>/dell/null` will only see the regular output without error messages
-  `|` pipe command to combine commands
-  `touch` Create a file
-  `echo` To display a variable
-  `alias` can be used to define custom commands
-  `mkdir` Create a folder
-  `rm` Used to remove a file
-  `rmdir` To remove a directory with no files within them
-  `rm -r` To remove a directory with the contents inside
-  `cp` Use to copy and duplicate the file in the new location and leanve the old one in place.
-  `mv` Used to rename a file and move a file from one location and removes it from the old location

### Filesystem Hierarchy

- `/` The home directory of the root user
- `/etc` Contains the Linux configuration files-files that control when and how programs start up
- `/home` The users home directory
- `/mnt` Where other filesystems are attached or mounted to the filesystem
- `/media` Where CDs and USB devices are usually attached or mounted to the filesystem
- `/bin` Where application binaries (the equivalent of executables in Microsoft Windows) reside
- `/lib` Where you'll find libraries, shared programs similar to Windows DLLs
- `/sys` This contains system information related to kernel features and connected devices
- `/boot` Kernel image, files used by the system to boot
- `/proc` View of internal kernal data. This is a special virtual filesystem representing the processes running in the system.
- `root` The home folder for the "root" super-user. This is not present in /home in case it gets full so that root can always log in to the system
- `/srv` This contains system information related to kernel features and connected devices
- `/usr` This contains the read-only user data, including libraries, binaries, headers, sources and other shared data
- `/var` This is the directory to be used to host content to be managed by different programs, from virtual machines to logs
- `/dev` The directory that includes files representing the devices connected to it (whether disk, keyboards, or audio devices, they are represented here)
- `/tmp` Temporary files
- `/usr/bin` This is the directory for the regular binaries used in the system
- `/usr/lib` This is the directory for the holding the libraries used in the system
- `/usr/local` This indicates local data specific to this host. When building local scripts or binaries for this specific system, host them here
- `/usr/sbin` This is the directory for the binaries to be used by the superuser only.

 ### Essential File Management Commands
 
- `whereis` To find binary files
- `Find` For a more advanced search with more parameters such as date of creation or modification, the owner, the group, permissions and the size
- `mount` /dev/sdb1 /`mnt` to mount a device to a directory `mnt` is the most common directory used for mounting devices
- `findmnt` shows all currently mounted devices and their place in the filesystem
- `lsblk` list block devices, devices that are not mounted yet
- `umount` is used to unmount a device
- `ln` is used to create hard links and the `ln -s` is used to created the symbolic link. These are comparable to shortcuts, as links are pointers to files in different locations.
- `tar` Compress, extract or list
- `tar -cvf` my_archive.tar /home/etc is used to create an archive
- `tar -tvf` will show contents of an archive
- `tar -xvf` my_archive extracts to the current directory
- `-z` gzip is the most common compression utility ,`-j` bzip2 is an alternative and `-J`xz shows more often. These are used to add compression, example 'tar -czvf` my_archive.tgz /home/etc
- `.tar` `.tgz` `.bz2` `.xz` naming convention that goes with gzip, bzip2 and xz 

 ### Managing Text Files Commands

 - `grep` to filter the results
 - `head` will show the first 10 lines of a text file
 - `tail` will show the last 10 lines of a text file
 - `cat` To display a text file

### Managing users, group and root privileges

- `su` is used to switch users or using root.
- `sudo` is used to perform administrative task
- `ssh` remote into machines

### Create and Manage Users
- `useradd` Create user accounts
- `usermod` Modify user accounts
- `usermod -L` Lock user account
- `usermod -U` Unlock user account
- `usermod -e` to set expiration example `usermod -e 2025-01-01 anna`
- `userdel` Delete user accounts
- `userdel -rf` To remove the user and all the files associated with the user
- `passwd` or `chage` Set passwords
- `groupadd` add group
- `groupdel` delete group
- `groupmod` modify group
- `groupmod -U` to add user to group name 
- `lid -g groupname` to list all users in the group

  ### Changing Ownership and Setting Permissions
- `chown user[:group]file` to set user-ownership, example chown lisa newfiles/ (user lisa is now owner of the newfiles/) also `chown linda:sales newfiles/` (lisa from group sales is the owner of newfiles/) also `chown sales: newfiles/`( group sales is owner of newfiles/`
- Use chgrp group fileto set group-ownership
