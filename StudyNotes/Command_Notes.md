# RHCSA Commands
### Getting Around The Command Line
### Documentation Commands
 - `man` is the best source to get extensive usage information
 - `man -k` to search the man database based on keywords
 - For the basic administration, the following sections matter most `man` (1) Executable programs or shell commands (5) File formats and conventions (8) System administration commands `passwd` 
- `grep` to filter the results

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
-  `cat` To display a text file
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
- `/sys` Kernels view of the hardware
- `/boot` Kernel image
- `/proc` View of internal kernal data
- `/dev` Special device files
- `/tmp` Temporary files

- ### Essential File Management Commands
- `whereis` To find binary files
- `Find` For a more advanced search with more parameters such as date of creation or modification, the owner, the group, permissions and the size
- `mount` /dev/sdb1 /`mnt` to mount a device to a directory `mnt` is the most common directory used for mounting devices
- `findmnt` shows all currently mounted devices and their place in the filesystem
- `lsblk` list block devices, devices that are not mounted yet
- `umount` is used to unmount a device
