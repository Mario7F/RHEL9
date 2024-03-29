# Notes From Sander Van Vught RHCSA RHEL 9 Course

### Lesson 4 Exploring The Essential Tools
  #### 4.2 Finding the man page
 - `man` is the best source to get extensive usage information
   - Sections define command types
   - Many `man` pages have examples
   - Search for text using `/`
 - Other documentation solutions are available, but not as important
   - GNU software has full documentation available through `info`
   - `pinfo` is an easier interface to navigate than `info`
   #### 4.3 Using an Editor
 - All `man` pages are indexed in the mandb
 - Use `man -k` or `apropos` to search the mandb based on a keyword
 - A lot results can show, use `grep` to filter the results
 - Manually Trigger a rebuild using `sudo mandb`

  #### 4.4 Understanding vim
 - `vi` was released in 1976 as a scxreen-oriented editor for the operating system
 - `vim` is the improved version `vi` and has replaced the original `vi` command
 - As command line work in the 1070's was line oreiented, and not screen oriented, `vi` was developed with advanced features to program text file modifications
 - Because of these advanced features, `vim` is still the most commonly used editor
 - Best practice: Use `nano` to edit text files in an easy way, use `vim` if you want to get respect in the Linux Community
 - Command mode is the default mode after opening
   - Use command mode to enter editing commands
   - Get to command mode by pressing the `Esc` key
 - Insert mode is where you can enter text
   - Press `i` to enter insert mode
   - After inserting text, don't forget to get back to command mode to save your text and exit

  #### 4.5 Exploring vim
  - `Esc` Enter command mode
  - `i` `a` Enter input mode
  - `o` Open new line in input mode
  - `:wq!` Write and quit
  - `:q!` Quit without saving anything
  - `dd` Delete the current line
  - `yy` Copy the current line
  - `p` Paste the text currently in the buffer
  - `v` Enter visual mode
  - `u` Undo the last operation
  - `Ctrl-r` Redo the last operation undone


### Lesson 5 Understanding The Bash Shell
   #### 5.1 Using I/O Redirection and Piping
- Redirection uses STDIN, STDERR and STDOUT to work with command input and ouput in a flexible way
   - `>` example using `ls` command to list the directories and use the `>` to create an output for the list, `cat` the output to display the list
  - `>>`
  - `2>/dev/null` (redirect error messages)
- In piping, the STDOUT of the first command is used as STDIN of the second command
  
 #### 5.2 Exploring History
- Bash registers recently used commands
- Type 'history' for an overview
- Commands are kept in ~/.bash_history to make them available beyond sessions
- The `HISTSIZE` and `HISTFILESIZE` variables are used to define the number of entries kept in history
- `history -w` synchronizes the current history from memory to history file
- `history -c` clears current history, don't forget to also use `history -w` when you want to remove everything
- `history -d nn` removes line `nn` from current history

- #### 5.3 Using Keyboard Shortcuts
- 
 #### 5.4 Introducing Shell Expansion
- Shell expansion allows for more efficient command line use
- Globbing expands filenames based on wildcards
  - `ls*`
  - `ls a?*`
  - `ls [a-e]*`
- Other types of expansion also exist
  - Brace expansion: touch file{1..9}, useradd {lisa,linda,anna}
  - Tilde expansion: cd ~
  - Command substitution: ls -l $(which ls)
  - Variable substitution: `echo $PATH`
    
 #### 5.5 Escaping Special Characters
- In expansion, special characters are interpreted by the shell to attribute a special meaning to the variables
- In escaping, this special meaning is taken away
- Double quotes suppress globbing and shell expansion but do allow command and variable substitution
  - Single quotes take away the special meaning of any characters
  - Backslash protects the following charcter only from expansion
 #### 5.6 Applying Variables
- Variables are used to seperate site-specific data from generic code
- The shell comes with standard system variables in the environment
- Type `env` to show the current value of the environment
- Users can define variables using `[export] key=value`, defining my own variable example `export color=red`
- Defining your own variables is mainly useful in scripting
- To make variables persistent, they should be stored in the startup files
  
 #### 5.7 Using alias
- `alias` can be used to define custom commands
- Some commands define as an alias are provided as system default
- Type `alias` for an overview of all current aliasses
- Use `alias key=value` to define your own alias
   - `alias del=rm -rf /tmp`
- Use `unalias` to remove an alias
- Custom aliasses are stored in the Bash startup files
  
 #### 5.8 Tuning The Bash Environment
- /etc/profile is the generic Bash startup file containing all system
- /etc/bashrc if processed while opening a subshell
- ~/.bash_profile is the user-specific version of /etc/profile
- ~/.bashrc is the user-specific version of /etc/bashrc
- Use custom startup files to make settings like variables and alias persistent
  
### Lesson 6 Using The Essential File Management Tools

 #### 6.1 Exploring the Filesystem Hierarchy
- Directory usage on Linux is highly standadized
- Standard directories are defined in the Filesystem Hierarchy Standard (FHS), which is maintained by Linux Foundation: https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html
- The starting point of the filesystem is the root directory
- Different devices may be integrated in the filesystem by using mounts
  
 #### 6.2 Using Essential File Management Commands
- `ls` list files
- `mkdir` make a directory
- `cp` copy files
- `mv` move files
- `rmdir` remove an empty directory
- `rm` remove files
  
- #### 6.3 Finding Files
- `which` looks for binaries in $PATH
- `locate` uses a database, building by `updatedb` to find files in a database
- `find` is the most flexible tool that allows you to find files based on many criteria
  
 #### 6.4 Mounting Filesystems
- To access a device, it must be connected to a directory
- This is known as mounting the device
- The Linux filesystem typically are on different devices for multiple reasons
  - security
  - manageability
  - specific mount options
- To mount a device, use `mount /dev/devicename /directory`
- - `mount /dev/sdb1 /mnt`
- The `findmnt` command shows all currently mounted devices and their place in the filesystem
  
 #### 6.5 Using Links
- Links are pointers to files in a different location
- Compare to shortcuts on other operating systems
- Link can be useful to make the same file available on multiple locations
- Linux uses hard links and symbolic links
- Create hard links with `ln` and symbolic links with `ln -s`
  
- #### 6.6 Archiving Files
- `tar` is the Tape Archiver and was created a long time ago
- By default, it doesn't compress data
- Basic use is to compress, extract, or list
- - `tar -cvf my_archive.tar /home/etc` to create a tar file
  - `tar -tvf` will show contents of an archive
  - `tar -xvf my_archive` extracts to the current directory
- To add compression, use `-z`, `-j` or `-J`

### Lesson 7 Managing Text Files

#### 7.1 Exploring Common Text Files

- Use `head` to show the first 10 lines of a text file
- Use `tail` to show the last 10 lines
- Use `[-n ]nn` to specify another number of lines
- `cat` dumps text file contents on screen

#### 7.2 Using Grep
- `grep` is excellent to find text in files or in output

#### 7.3 Applying Regular Expressions
- Regular Expressions are text patterns that are used by tools like grep and others
- Alaways put your regex between single quotes!
- Don't confuse regular expressions with globbing (shell wildcards)!
- For use with specific tools only (`grep`, `vim` , `awk` and `sed`)
- See `man 7 regex` for details

#### 7.4 Exploring awk
-`awk` is a powerful text processing utility that is specialized in data extraction and reporting
- It can perform actions based on selections

#### 7.5 Using sed
- `sed` is the stream editor, used to search and transform text
- It can be used to search for text, and perform an operation on matching text

### Lesson 8 Using Root Privileges 

#### 8.1 Understanding the root User
   - A user account with UID 0 exist to perform administration tasks
   - This user by default has the name root
   - The root user operates in kernel space and for that reason has unlimited access to all parts of the system
   - If the root user is not activated, the administrative user is used for administration tasks
   - To activate the root user, you'll just have to set a password
   - From a security perspective, it may be a good idea not to have an active root user
   - Additional measures are possible to restrict root user access to a system
      - Remote root login using secure shell (SSH) can be allowed or not
   - The `su` command is used to switch current user account from a shell environment
   - If `su` is used with the `-`option, the complete environment of the target user is loaded
   - While using `su`, the password of the target user is entered
   - If the root user has a password, `su -` can be used
   - Using `su -` to open a root shell is considered bad practice, use `sudo -i` instead
   - The `su` command can be useful for testing other user accounts

  #### 8.3 Performing Administrator Tasks with Sudo
   - `sudo` is a more secure mechanism to perform administration task
   - Behind `sudo` is the /etc/sudoers configuration file
   - While editing /etc/sudoers through visudo, very detailed administration privileges can be assigned
   - To run administration task using `sudo`, use `sudo` command
   - This will prompt for the current user password, and the run the command if this is allowed through /etc/sudoers
   - To open a root shell, `sudo -i` can be used

  #### 8.4 Managing sudo Configuration
   ##### *Exploring /etc/sudoers*
- Sudo configuration is managed through `/etc/sudoers`
- Don't edit this file directly, only edit it through `visudo`
- Instead of editing `/etc/sudoers`, consider creating drop-in files in `/etc.sudoers.d`
- `/etc/sudoers` is installed from packages and may be overwritten, drop-in files will never be overwritten

  ##### *Providing Administator Access*
  - Users that are member of the group `wheel` get full sudo access
   - This is accomplished by `%wheel ALL=(ALL) ALL` in `/etc/sudoers`
   - Use `usermod -aG wheel myuser` to add a user to the group Wheel
  - Do NOT enable the line `%wheel ALL =(ALL) NOPASSWD: ALL`
   - It will provide full sudo access  without entering a password and is very dangerous
  --If you don't like entering your user password every five minutes, increase authentication token expiration by adding the following `Defaults timestamp_type=global,timestamp_timeout=60`

 #### Providing Access To Specific Task
 - Use drop-in files to provide admin access to specific task
  - username `ALL=/sbin/useradd,/usr/bin/passwd` (Able to add users and change their password)
- Consider using command arguments to make the commands more specific
  - `%users ALL=/bin/mount /dev/sdb,/bin/umount /dev/sdb`
  - username `ALL=/usr/bin/passwd,! /usr/bin/passwd root` (able to change passwords but not for the root account)

 #### 8.5 Using Secure Shell
 - By default, all RHEL servers run a Secure Shell (SSH) server
    - Use `systemctl` to verify
     - `systemctl status sshd`
 - SSH access is allowed through the firewall by default
 - Notice that root access is often denied
 - Use `ssh` to connect to a remote server
   - On the remote server, use `ip a` to find the IP address
   - `ssh <ip>` is an example to connect to an IP address using your current user account
   - `ssh user@<ip>` will connect as a specific user
  
### Lesson 9 Managing Users And Groups
  #### 9.1 Understanding the Purpose of User Accounts
   - A user is a security principle, user accounts are used to provide people or processes access to system resources
   - Process using system accounts
   - People are using regular user accounts
 #### 9.2 Setting User Properties
- User properties are managed in /etc/password
   - *Name:* the name of the account
   - *Password:* the secret that is used for authentication, may be disabled
   - *UID:* a unique identifier for users
   - *GID:* the ID of the primary group
   - *GECOS:* additional non-mandatory information about the user
   - *Home Directory:* the environment where users create personal files
   - *Shell:* the program that will be started after successful authentication
 #### 9.4 Defining User Default Settings
 - Use `useradd -D` to specify default settings (advised not to do this)
 - Settings in /etc/default/useradd apply to `useradd` only (Not advised either)
 - Alternatively, write default settings to `/etc/login.defs` (preferred)
 - Files in `/etc/skel` are created to the user home direction upon creation
#### 9.6 Managing Group Membership
- *Limit Access*
  - User accounts can be temporarily locked
  - `usermod -L anna` will lock anna
  - `usermod -U anna` will unlock anna
- User accounts can be set to expire also
  - `usermod -e 2025-01-01 anna` expires user account anna on 01-01-2025
- Set `/sbin/nologin` as the shell users that are not intended to log in at all
  - `usermod -s /sbin/nologin myapp`
 
#### 9.7 Creating and Managing Groups
- Use `groupadd` to add groups
- `groupmod -U` to add `user` to `groupname`
- `lid -g` `groupname` is how you would list the users in the `groupname`
- `groupdel` and `groupmod` can be used to delete and modify groups
- Use `lid -g groupname` to list all users that are members of a specific group

#### 9.8 Setting Password Properties
- *Password Encryption*
- Encrypted passwords are stored in /etc/shadows
- The encrypted string shows 3 pieces of information
  - The hashing algorithm
  - The random salt
  - The encrypted hash of the user password
- *Manage Password Settings*
- Basic password requirements are set in `/etc/login.defs`
- For advanced password properties, Pluggable Authentication Modules (PAM) can be used
  - Look for the pam_faillock module
- To change password settings for current users, use `chage` or `passwd` as root
 
 
### Lesson 10 Securing Files With Permissions
- #### 10.1 Understanding Ownership
  - To determine which permissions a user has, Linux uses ownership
  - Every file has a user-owner, a group-owner and the others entity that is also
  - Linux permissions are not additive, if you're the owner, permissions are applied and that's all
  - Use `ls -l` to display current ownership and associated permissions
  - Best practice: Set ownership before modifying permissions
 
  #### 10.2 Changing File Ownership
   - `chown user[:group]file` to set user-ownership, example `chown lisa newfiles/` (user lisa is now owner of the newfiles/) also `chown linda:sales newfiles/ (lisa from group sales is the owner of newfiles/) also `chown sales: newfiles/`( group sales is owner of newfiles/)
   - Use `chgrp group file`to set group-ownership
     
 #### 10.3 Understanding Basic Permissions
   - Read(4), able to open the file and on the directory you are able to list the files
   - Write(2), modify files and on the directory you are able to create or delete files
   - Execute(1), run an executable on the file and on the directory you are able to `cd` to get inside the directory

 #### 10.4 Managing Basic Permissions
   - `chmod` is used to manage permissions
   - It can be used in absolute or relative mode
   - `chmod 750 myfile` (absolute mode, using digits to refer to the permissions you want to set) (The 7 is related to the user, 5 to the group and the 0 to others. The 7 is (4+2+1 which is read+write+execute) the 5 is (read +execute) and the 0 is none
   - `chmod +x myscript` is the relative mode if you want to apply a indivual to a file

     #### 10.5 Configuring Shared Group
  - Understanding Shared Group Directories
      - If members of the same group need to share files within a direcory, some special permissions are required
      - The Set Group ID (SGID) permission ensures that all files created in the shared group directory are group owned by the group owner of the directory
      - The sticky bit permission ensures that only the user who is owner of the file, or the directory that contains the file, is allowed to delete the file
  - Applying Shared Group Permissions
      - `chmod g+s mydir` will apply SGID to the directory
      - `chmod +t mydir` assigns sticky bit to the directory
      - In absolute mode, a four digit number is used, of which the first digit is for the special permissions
      - `chmod 3770 mydir` assigns SGID and sticky it, as well as rwx for user and group 

       #### 10.6 Securing Files with Permissions
  - Applying Default Permissions
      - The `umask` is a shell setting that subtracts that umask from the default permissions
        - Default is set in /etc/bashrc
        - Set user-specific overrides in ~/.bashrc
      - Default permissions for file are 666
      - Default permissions for directory are 777
   
    #### 11.1 Understanding IPv4 Networking
       - In IPv4, each node needs its own IP address, written in dotted decimal notation (192.168.4.200/24)
       - Each IP address must be indicated with the subnet mask behind it
       - The default router or gateway specifies which server to forward packets to that have an external destination
       - The DNS nameserver is the IP address of a server that helps to resolve names to IP address and the other way around
       - IPv4 is still the most common IP version, but IPv6 addresses can be used as well
       - IPv6 addresses are written in hexadecimal notation (fd01::8eba:210)
       - IPv4 and IPv6 can co-exist on the same network interface
     
    #### 11.2 Exploring IPv6 Networking
       - IPv6 was introducted in the 1990's to overcome the shortage of world-wide unique IPv4 addresses
       - IPv6 is used extensively by ISP to address the core internet infrstructure
       - End-users and companies mostly use IPv4 behind a NAT router
       - Red Hat Enterprise Linux offers dual stack IPv4 and IPv6
   
    #### 11.3 Understanding NIC Naming
    - Device Names
      - IP address configuration needs to be connected to a specific network device
      - Use `ip link show` to see current devices, and `ip addr show` to check their configuration
      - Every system has an Io device, which is for internal networking
      - Apart from that, you'll see the name of the real network device, which is presented as a BIOS name
    
    -BIOS Device Names
       - Classical naming is using device names like etho0, eth1 and so on
         - These device names don't reveal anyi information about physical device location
       - BIOS naming is based on hardware properties to give more specific information in the device name
       - - em[1-N] for embedded NICs
         - eno[nn] for embedded NICs
         - p<slot>p<port> for NICs on the PCI bus
       - If the driver doesn't reveal network device properties, classical naming is used
         
    #### 11.4 Defining Host Names and Host Name Resolution
       - `hostnamectl set-hostname` is used to manage hostnames (example to change the hostname "mario.localdomain", use hostnamectl server1.example.com)
       - The hostname is written to /etc/hostname
       - Use `hostname` to provide the hostname of the machine
       - To resolve hostnames /etc/hosts is used (vim /etc/hosts) 
         - 10.0.0.11 server2example.com server2 (provide IP address to the FQDN) 
       - /etc/resolv.conf contains DNS client configuration
       - The order of host name resolution is determined through /etc/nsswitch.conf
    
    #### 11.5 Analyzing Network Configuration
       - The `ip` tool can be used to manage all aspects of IP networking
       - It replaces the legacy `ifconfig` tool, do not use `ifconfig` anymore
       - Use `ip addr` to manage address properties
         - ip addr add dev ens33 10.0.0.10/24 (example, to add a temporary IP address get the get the IP of the device, ip a a dev <device name, found after using `ip a` command> set the IP address you want to assign and netmask (usually /24)
       - Use `ip link` to show link properties
         - ip -s link
       - Use `ip route` to manage route properties
         - `ip route show` (to show the routing table)
         - `ip route add` default (or an IP) via 10.0.0.1
         
    #### 11.6 Understanding Network Manager
       - NetworkManager is the systemd service that manages network configuration
       - Configuration is stored in files in /etc/NetworkManager/system-connections
         - Legacy files in /etc/sysconfig/network-scripts are still supported but deprecated
       - Different applications are available to interface with NetworkManager
         - `nmcli` is a powerful command line utility
         - `nmtui` offers a convenient text user interface
         - GNOME offers graphical tools also
        
         ##### Connections and Devices
         - In NetworkManager, devices are network interfaces
         - Connections are collections of configuration settings for a device, stored in the configuration file in /etc/NetworkManager/system-connections
         - Only one connection caxn be active for a device
        
         ##### NetworkManager Permissions
         -Permissions to modify settings in NetworkManager are applied through `dbus`
         - Non-privileged users that are logged in on the console can change network settings
         - Non-privileged users that are logged in through `ssh` cannot
         - Use `nmcli general permissions` for an overview of current permissions that apply
    
    #### 11.7 Managing Persistent Network Configuration with nmcli
       - `nmcli` has awesome tab completion
       - `nmcli con show` shows current connections
       - `nmcli dev status` shows current network devices
       - `nmcli con add on-name mynewconnection ifname ens33 ipv4.addresses 10.0.0.10/24 ipv4.gateway 10.0.0.1 ipv4.method manual type ethernet` will add a new connection
       - `nmcli con up mynewconnection` will activate the new connection
       - `nmcli con show mynewconnection` shows all connection settings (helps to analyze issue)
       - `nmcli con mod` will modify connection settings: use tab completion
       - `nmcli con reload` will reload the modified connection
       - Use `ipv4.method manual` on connections that don't use DHCP
         
    #### 11.8 Managing Persisten Network Configuration with nmtui
       - Use for exam, use the `nmtui` command
       - provides a gui to edit connection (profile name, device, IP configuration, gateway, dns server)
       - Make sure you select the automatically connect
       - After configuring the network configuration, activation the connection (press enter to activate)
   
    #### 11.9 Troubleshooting Networking
       - Use `ping` to verify connectivity
         - `ping -c 4 myserver` sends 4 packets and then stops
         - `ping6 2001::210` uses ping6
       - When using `ping6` on link-local addresses, you must include the NIC name in the command
   
    ##### Troubleshoot Routing
       - `ip route` prints the routing table
       - `ip -6 route` shows the IPv6 routing table
       - `tracepath example.com` shows the entire networking path
       - `tracepath6 example.com` does the same for an IPv6 path (if existing)
       - `ss` is used to analyze socket statistics (replacement for netstat)
         - ss -tu
         - ss -tuna
         - ss -tunap

