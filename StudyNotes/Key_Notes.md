r# Notes From Sander Van Vught RHCSA RHEL 9 Course

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

  ### Lesson 12 Managing Software 
  
  #### 12.1 Understanding RPM Packages
  
   - Software on RHEL is installed using packages Red Hat Package Manager (RPM) format
     - An RPM package contains a compressed archive, as well as package metadata
     - In the metadata, package dependencies are identified
     - To handle dependency management, RHEL uses repositories for package installation
     - If a dependency was found, it is installed automatically from the repository
     - Installed packages are registered in the RPM database

  ##### Managing RPM Packages
    
   - The `rpm` command can be used for some package management tasks
     - Some commands query the RPM database
       - `rpm -qa` shows all packages that are currently installed
       - `rpm -qf filename` shows from which package filename was installed
       - `rpm -ql` list files installed from a package
       - `rpm -q --scripts` shows scripts executed while installing the package
       - `rpm -q --changelog` shows the change log for a package

       ##### Extracting RPM Packages
       - Contents of an RPM package can be extracted to the current directory (without installing)
       - `rpm2cpio mypackage-1.0.rpm | cpio -tv` will show the content a package
       - `rpm2cpio my package-1.0.rpm` | cpio -idmv` extracts the packages contents to the current directory

     #### 12.2 Setting Up Repository Access

     - A repository is a collection of RPM package files with an index that contains the repository contents
     - Repositories are often offered through web sites, but local repositories can be created also
     - The `dnf` command is used as the default command to install packages from repositories
     - In RHEL 9, `dnf` is preferred over `yum` command which was used in previous versions of RHEL
     - `dnf` and `yum` are offering the same functionality

      #### Accessing Repositories
     - To access repositories, a RHEL system must be registered using `subscription-manager`
     - `subscription-manager` tries to access the online Red Hat Repositories
     - As an alternative to online repositories, repositories can be offered through Red Hat Satellite
     - If no Internet connection, nor Red Hat Satellite are available, no repositories will be available by default
     - In that case, you'll have manually configured repository access
    
     #### Manually Configuring Repository Access
     - To access repositories that are offered through subscription manager, use `dnf config-manager --enable name-of-the-repository` to add repository access
     - Third party repositories can be added using a repo file in `/etc/yum.repos.d/, or using `dnf config-manager`
     - `dnf config-manager --add-repo="file:///repo/AppStream"
     - `cat>> /etc/yum.repos.d/AppStream.repo << EOF
       > [AppStream]
       > name=AppStream
       > baseurl=file:///repo/AppStream
       > gpgcheck=0
       EOF

     #### 12.3 Managing Packages with dnf
     - `dnf` was created to be intuitive
         - `dnf list` lists installed and available packages
         - `dnf list "selinx*"` to show the selinux packages installed
     - 'dnf search' searches in name and summary. Use `dnf search all` to search in description as well
     -  - `dnf search seinfo`
        - `dnf search all seinfo`
     - 'dnf provides' searches in package file lists for the package that provides a specific file
         - `dnf provides */Containerfile`
     - `dnf info` shows information about the package
     - `dnf install` installs packages as well as anay dependencies
     - `dnf remove` removes packages, as well as packages depending on this packages - potentially dangerous
     - `dnf update` compares current package version with the package version listed in the repository and updates if necessary
        - `dnf update kernel` will install the new kernel and keeps the old kernel as a backup
      
     #### 12.4 Using dnf Groups
     - A `dnf group` is a colletion of packages
     - A regular group is just a collection of packages
     - An environment group is used to install a specific usage pattern, ad may consist of packages and groups
     - Use `dnf group list` to see a list of groups
     - Some groups are normally only installed through environment groups and not seperately, and for that reason don't show who is using `dnf group list`
     - Use `dnf group list hidden` to see these groups as well
     - Use `dnf group info "<groupname>"` to see packages within a group
     - Packages are marked as mandatory, default, or optional
     - To install optional packages also, use `dnf group install --with-optional`
     - As group names often contain spaces, the entire group name must be referred to using double qoutes
    
     #### 12.5 Exploring Modules and Application Streams
     - `dnf` uses modularity, meaning that different versions of the same package can be maintained in the same repository
     - Modularity is useful for packages that have a lifetime that differs from the core operating system packags
     - RHEL 9 offers 2 main repositories:
       - BaseOS has core OS content for RHEL. Packages in BaseOS share the OS lifecycle
       - AppStream is used for packages that don't have the same lifecycle as RHEL
       
     ##### Understanding AppStream Packages
     - AppStream packages are offered as individual packages or as modules
     - In RHEL 9.0 no modules are provided by default, they may be offered separately later
     - In a module, different streams can be offered, where each package version has its own stream
     - Module, profiles provide common installation patterns, such as server, client and more.
    
     #### 12.6 Managing dnf Updates and History
     - All transaction that `dnf` perform are logged to `/var/log/dnf.rpm.log`
     - Use `dnf history` for a summary of all installation and removal transactions
     - Use `dnf history undo n` to undo a specific transaction
    
     #### 12.7 Using subscription-manager
     - To use RHEL, you need to register the system and attach a subscription
       - Before completing this procedure, you'll have no repository access
     - To register, use `subscription-manager register`
       - You'll be prompted for the username of the user account to which the subscription is connected
     - To attach a subscription, use `subscription-manager attach --auto`
     - To unregister a system use `subscription-manager unregister`
    
     ##### Understanding Entitlement Certificates
     - After attaching subscriptions to a system, entitlement certificates are created
     - - `/etc/pki/product` indicates the installed Red Hat products
       - `/etc/pki/consumer` identifies the Red Hat account for registration
       - `/etc/pki/entitlement` indicates which subscription is attached
     - Use `rct` command to check current entitlements
     - - `rct cat-cert /etc/pki/entitlement/xyxxxyyzzz.pem`
      
   ### Lesson 13 Monitoring Activity

   #### 13.1 Exploring Jobs and Processes

   ##### Understanding Jobs and Processes

   - All task are started as processes
   - Processes have a PID
   - Common Process Management task include scheduling priority and sending signals
   - Some processes are starting multiple threads, individual threads cannot be managed
   - Tasks that are started from a shell can be managed as jobs
   - Shell jobs can be started in the foreground or background

#### 13.2 Managing Shell Jobs

  - Use `&` to start a job in the background
  - To move a job to the background
    - First, stop it using `Ctrl-Z`
    - Next, type `bg` to move it to the background
 - Use `jobs` for a complete overview of running jobs
 - Use `fg` to move the last job back to the foreground

#### 13.3 Understanding Process States

##### Understanding Process Running State

  - When a new process is started (forked) it is scheduled and after being scheduled, it will get a runnable state (R).
    - In this state it is waiting in the queue to be scheduled
  - Runnable processes will get a time slice, which allows them to get a running state, in either kernel space or user space
  - Runnable processes can get preempted or rescheduled
    - In that case, they will return to a runnable state and wait in the queue for a new time slice
  - A runnable process can be stopped (ctrl-z) and will show as TASK_STOPPED (T), and after being stopped it can receive another signal to resume and return to a runnable state

##### Understanding Process Waiting States

  - While running, the process may have to wait
    - This is also referred to as "blocking" state, but "blocking" is not an offical state in the Linux kernel
  - Waiting processes can have different flags
    - TASK_INTERRUPTIBLE (S): the process is waiting for hardware request, system resource access or a signal
    - TASK_INTERRUPTIBLE (D): the process is waiting but does not respond to signals
    - TASK_KILLABLE (K): the process is waiting but may be killed
    - TASK_REPORT_IDLE (I): Used for kernel threads, this process will not count for the load average

##### Understanding Exit States

  - When a process exits, it will briefly enter the EXIT_ZOMBIE (Z) state. This is where it signals the parent process that it exits and all resources except for the PID are released.
  - In the next stage the process will enter the EXIT_DEAD (X) state. In this state will be reaped and all remaining processes are cleaned up

##### Understanding Zombies

- A process becomes a Zombie when it has completed its task, but the parent process hasn't collected its execution status
- Zombies are already dead so they can't and don't have to be killed
- The most important disadvantage, is that Zombies occupy a PID
- To get rid of the Zombie, the parent process must collect the child execution status
  - Send SIGCHLD to the parent to ask the parent to reap the Zombie
  - Kill the parent process
  - When the parent is killed, the Zombie becomes a orphan and will be adpoted by the init process

#### 13.4 Observing Process Information with ps

  - The `ps` command has two different dialects: BSD and System V
  - - In BSD, options do not have a leading -
    - In System V, options do have a leading -
 - Therefore `ps -L` and `ps L` are two completely different commands!
 - `ps` shows an overview of current processes
 - Use `ps aux` for an overview of all processes
 - `ps -fax` shows hierarchical relatiosn between processes
 - `ps -fU linda` shows all processes owned by linda
 - `ps -f --forest -C sshd` shows a process tree for a specific process
 - `ps L` shows format specifiers
 - `ps -eo pid, ppid, user, cmd` uses some of these specifiers to show a list of processes

#### 13.5 Understanding Memory Use

 - Linux places as many files as possible in cache to guarantee fast access to the files
 - For that reason, Linux memory often shows as saturated
 - Swap is used as an overflow buffer of emulated RAM on disk
 - The Linux kernel moves inactive application memory to swap first
 - Inactive cache memory will just be dropped
 - Use `free -m` to get details about current memory usage
 - More detailed memory information is in /proc/meminfo

##### Understanding Write Cache

  - While writing files, a write cache (buffers) is used
  - This write cache is periodically committed to disk by the `pdflush` kernel thread
  - As a result, after committing a file write, it's not immediately secure
  - To ensure that a file is committed to disk immediately, use the `sync` command

#### 13.6  Observing CPU Load

  - CPU load is checked through `uptime`
  - CPU load is expressed as the average number of runnable processes over the last 1, 5 and 15 minutes
  - As a rough guideline, this number should not exceed the number of CPU cores on a system
  - Use `lscpu` to check the number of CPU cores

#### 13.7 Monitoring System Activity with top

  -  `top` is a dashboard that allows you to monitor current system activity
  -  Press `f` to show and select from available display fields
  -  Type `M` to filter on memory usage
  -  Press `W` to save new display settings
  -  `htop` is a common alternative for `top`, but not installed by default

### Lesson 14 Managing Processes

#### 14.1 Using Signals to Manage Process State

  - A signal allows the operating system to interrupt a process from software and ask it to do something
  - Interrupts are comparable to signals, but are generated from hardware
  - A limited amount of signals can be used and is documented in `man 7 signals`
  - Not all signals work in all cases
  - The `kill` command is used to send signals to PID's
  - You can also use `k` from top
  - Different kill-like commands exist, like `pkill` and `killall`


#### 14.2 Managing Process Priority

  Understanding Priortiy Management
  
  - Linux Cgroups provide a framework to apply resource restrictions to Linux systems
  - Cgroups can limit the amount of CPU cycles, available memory, and more
  - If processes are equal from a perspective of Cgroups, the Linux `nice` and `renice` commands can be used to manage priority

  ##### Understanding Cgroups
  
  - In Cgroups, the Linux system is divided in 3 slices
    - System: all systemd processes
    - User: all user processes
    - Machine: Virtual machines and containers
  - Each clice has an equal CPU weight
  - That means that if one or more processes within a slice request a maximum amount of CPU cycles, each slice will get an equal amount of CPU shares
    - So 20 systemd processes together gets as much as one user process that claims full CPU usage!
  - In systemd, the CPUWeight can be set on individual systemd units

##### Managing nice

 - If no specific Cgroups are defined, Linux `nice` and `renice` can be used to define CPU priority
 - To change priorities of non-realtime processes, the `nice` and `renice` commands can be used
 - Nice values range from -20 up to 19
 - Negative nice value indicates an increased priortiy, a positive nice value indicates decreased priority
 - Users can be set their processes to a lower priority, to increase priorities you need root access
   
#### 14.3 Using Tuned Profiles

##### Understanding System Tuning

- Kernel tunables are provided through the /proc/sys directory in the /proc pseudo file system
- Different files in the /proc/sys directory contain the current setting as its value
- Change the current value by echoing a new value into the file:
  - `cat /proc/sys/vm/swappiness`
  - `echo 40 > /proc/sys/vm/swamppiness`
 
##### Understanding Tuned

- To make system tuning easier, `tuned` is provided
- `tuned` is a systemd service that works with different profiles
- `tuned-adm list` shows current profiles
- `tuned-adm profile virtual-guest` sets another profile as default
- Each profile contains a file with the name tuned.conf, that has a wide range of performance related settings.
- The `reapply_sysctl = 1` parameter in `/etc/tuned/tuned-main.conf` ensures that, in case of contflict, the `sysctl` parameter wins

##### Creating Custom Profiles

- Custom `tuned` profiles are stored as directories in `/etc/tuned`
- Each profile should have file `tuned.conf`, containing the requested performance settings
- After creating the directory with the corresponding `tuned.conf`, it will automatically be picked up
  
#### 14.4 Managing User Sessions and Processes

##### Using Common Utilities

- Use `ps -u username` to show processes owned by a specific user
- Use `pkill -u username` to remove processes owned by a specific user

##### Using loginctl

- `loginctl` is a part of `systemd`, which manages users and sessions
- One user can have multiple sessions open simultaneously
- `loginctl list-users` and `loginctl list-sessions` shows users and sessions
- `loginctl user-status <UID>` shows a tree of processes currently open by this user
- `loginctl terminate-session` and `loginctl terminate-user` can be used to stop current sessions or users

### Lesson 15 Working With Systemd


#### 15.1 Exploring Systemd Units

- Service units are used to start processes
- Socket units monitor activity on a port and start the corresponding Service unit when needed
- Timer units are used to start services periodically
- Path units can start Service units when activity is detected in the file system
- Mount units are used to mount file systems
- Other unit types are available, though less relevant for RHCSA

##### Understanding Service Units

- Service units are often used to start daemon processes
- Other types of Service units are available as well
  - Type=oneshot can be used to start any command through systemd
    
#### 15.2 Managing Systemd Services

- `systemctl status` shows the current status of any unit
  - `systemctl status sshd`
- The Active: line in the output shows the current status
- The Loaded: line in the output shows which configuration is loaded, and whether the unit is enabled for automatic starting
- Use `systemctl status` to get current status
- `systemctl start` will start a unit that is not currently active
- `systemctl stop` will stop the unit
- `systemctl enable` is used to flag the unit automatic starting upon system start
- `systemctl disable` is used to flag the unit to be no longer automically started
- `systemctl reload` will reload the unit configuration without restarting the unit
- `systemctl restart` restarts the unit after which thee process it manages gets a new PID
  
#### 15.3 Modifying Systemd Service Configuration

- Default system-provided systemd unit files are in `/usr/lib/systemd/system
- Custom unit files are in `/etc/systemd/system`
- Run-time automatically-generated unit files are in /run/systemd
- While modifying a unit file, do NOT edit the file in /usr/lib/systemd/system but create a custom file in /etc/systemd/system that is used as an overlay file
- Better: use `systemctl edit unit.service` to edit unit files
- Use `systemctl show` to show available parameters
- Using `systemctl reload` may be required
  
#### 15.4 Managing Unit Dependencies

- Systemd units normally depend on other unitis
- Use `systemctl list-dependencies` for a complete overview of all currently loaded units and their dependencies
- Use `systemctl list-dependencies UNIT` to see dependencies for any specific unit
  
#### 15.5 Masking Services

- Some units cannot work simultaneously on the same system
- To prevent administrators from accidentally starting these units, use systemctl mask
- `systemctl mask` links a unit to the /dev/null device, which ensures that it cannot be started
- `systemctl unmask` removes the unit mask

### Lesson 16: Task Scheduling

#### 16.1 Exploring RHEL Scheduling Options

##### RHEL 9 Scheduling Options

- `systemd` timers are the primary solution for scheduling recurring jobs on RHEL 9
- `crond` is an older scheduling solution which is still supported and a bit easier to schedule custom tasks
- `at` is available to schedule non-recurring user tasks
  
#### 16.2 Scheduling Tasks with Systemd Timers

##### Understanding systemd Timers

- Systemd provides unit.timer files that go together with unit.service files to schedule the service file
- When using `systemd` timers, the timer should be enabled / started, and NOT the service unit
- `systemd` timers are often installed from RPM packages
- In the timer unit file, the `OnCalendar` option specifies when the service should be started
- On RHEL 9, `systemd` timers are the default way for scheduling recurring services

##### Understanding Timer Activation

- The `systemd` timer `OnCalendar` option uses a rich language to express when the timer should activate
- Use `OnUnitActivateSec` to start the unit a specific time after the unit was last activated
- Use `OnBootSec` or `OnStartupSec` to start the unit a specific time after booting
- Read `man 7 systemd-time` for specification of the time format to be used
  
#### 16.3 Scheduling Tasks with cron

##### Understanding cron

- `cron` is an old UNIX scheduling option
- It uses `crond` , a daemon that checks its configuration to run cron jobs periodically
- Still on RHEL 9, `crond` is enabled as a `systemd` service by default
- Most services that need scheduling are scheduled through `systemd` timers

##### Using Cron

- The `cron` service checks its configuration every minute
- `/etc/crontab` is the main (managed) configuration file
- `/etc/cron.d/` is used for drop-in files
- `/etc/cron.{hourly, daily, weekly, monthly}` is used as a drop-in for scripts that need to be scheduled on a regular basis
  - Make sure these scripts have the execute bit set!
- User specific cron jobs can be created using `crontab -e`

##### Understanding Cron Time Specification

- Cron time specifications are specified as minute, hour, day of month, month, day of week
- `0**dec 1-5` will run a cron job every monday thru friday on minute zero in December
- The /etc/crontab file has a nice syntax example
- Do NOT edit /etc/crontab, put drop-in files in /etc/cron.d instead
  
#### 16.4 Understanding anacron

- `anacron` is a service behind `cron` that ensures that jobs are executed on a regular basis, but not at a specific time
- It takes care of the jobs in /etc/cron.{hourly,daily,weekly,monthly}
- Configuration is in /etc/anacrontab
- Don't change anything in /etc/anacrobtab, use `systemd` timers instead
  
#### 16.5 Using at

- The `atd` service must be running to run once-only jobs using `at`
- Use `at <time>` to schedule a job
  - Type one or more job specifications in the at interactive shell
  - Use Ctrl-D to close this shell
- Use `atq` for a list of jobs currently scheduled
- Use `atrm` fto remove jobs from the list

#### 16.6 Managing Temporary Files

##### Understanding Temporary Files

- In the past, temporary files were created in the /tmp directory
- Without management, these files could stay around for a long time
- As a solution, the /tmp directory could be created on a RAM drive
- Nowadays, `systemd-tmpfiles` is started while booting, and manages temporary files and directories
- It will create and delete tmp files automatically, according to the configuration files in the following locations:
  - /usr/lib/tmpfiles.d/
  - /etc/tmpfiles.d/
  - /run/tmpfiles.d/

##### Understanding systemd-tmpfiles

- `systemd-tmpfiles` works with related services to manage temporary files
- `systemd-tmpfiles-setup.service` creates and removes temporary files according to the configuration
- `systemd-tmpfiles-clean.timer` calls the `systemd-tmpfiles-clean.service` to remove temporary files
  - By default 15 minutes after booting
  - And also on daily basis

##### Managing Temporary Files

- In the configuration files, specify what to do with temporary files
  - `d /run/myfiles 0750 root root` - will create the directory /run/myfiles if necessary. No action if it already exists
  - `D /run/myfiles 0750 root root 1d` will create the directory if necessary, and wipe its contents if it already exists. Files older than 1 day are eligible for automatic removal
- `man tmpfiles.d` provides detailed information and examples

### Lesson 17 Configuring Logging

#### 17.1 Exploring RHEL Logging Options

- `systemd-journald` is receiving log messages from different locations
  - The kernel
  - Early boot procedure
  - Syslog events
  - Standard output and error from daemons
- The systemd journal is non-persistent by default
- The `rsyslog` service reads syslog messages and writes them to different locations
  - Files in /var/log
  - According to output modules
- Services may also write to /var/log
  
#### 17.2 Using systemd-journald

##### Viewing Systemd Journal Messages

- `systemctl status name.unit` provides easy access to the last messages that have been logged for a specific service
- `journalctl` prints the entire journal
- - Important messages are shown in red
- `journalctl -p err` shows only messages with a priority error and higher
- `journalctl -f` shows the last 10 lines, and add new messages while they are added
- `journalctl -u sshd. service` shows messages for sshd.service only
- `journalctl --since "-1 hour"; journalctl --since today` allows time specification
- `journalctl -o verbose` adds verbose messages

##### Viewing Boot Logs

- `journalctl -b` shows the current boot log
- `journalctl -xb` adds explanation texts to the boot log messages
- `journalctl --list-boots` shows all boots that have been logged (on persistent journal only)
- `journalctl -b 3` shows messages from the third boot log only
  

#### 17.3 Preserving the Systemd Journal

##### The Need for Persistency

- The systemd journal is non-persistent
- Persistency is taken care of by the rsyslog service
- Rsyslog offers all the filtering you need to fine-tune log persistency
- If desired, the systemd journal can be made persistent as well

##### Making the Journal Persistent

- Systemd journal settings are in /etc/systemd/journal.conf
- The setting `Storage=auto` ensures  that persistent storage is happening automatically after creating the directory /var/log/journal
- Other options are:
  - persistent: stores journals in /var/log/journal
  - volatile: stores journals in the temporary /run/log/journal directory
  - none: doesn't use any storage for the journal at all

##### Managing Persistent Journal Size

- In journal.conf, default settings apply to ensure that the journal can't grow in an unlimited way
- - Log ration triggers monthly
  - No more than 10% of the file system size can be used
  - No more than 15% of the file systemfree size can be used
- Use `journalctl | grep -E 'Runtime Journal | System Journal` to check current settings
#### 17.4 Configuring rsyslogd

##### Understanding Rsyslog

- Rsyslog needs the `rsyslogd` service to be running
- The main configuration file is /etc/rsyslog.conf
- Snap-in files can be place in /etc/rsyslog.d/
- Each logger line contains three items
  - facility: the specific facility that the log is created for
  - severity: the severity from which should be logged
  - destination: the file or other destination the log should be written to
- Log files normally are in /var/log
- Use the `logger` command to write messages to rsyslog manually

##### Understanding Facilities

- `rsyslogd` is and must be backwards compatible with the ancient syslog service
- In syslog, a fixed number of facilities was defined, like kern, authpriv, cron, and more
- To work with services that don't have their own facility local{0..7} can be used
- Because of the lack of facilities, some services take care of their own logging and don't use rsyslog
  
#### 17.5 Using logrotate

##### Understanding logrotate

- The `logrotate` command is started by a systemd timer to prevent them from growing too big
- After rotation, the file is renamed to a file with the rotation date as extension
- When too many files are rotated, according to the settings, the oldest file will be discarded
- Log rotation is configured in the files in /etc/logrotate.conf and /etc/logrotate.d/

### Lesson 18: Working with Partions and Mounts

#### 18.1 Understanding Disk Layout
#### 18.2 Exploring Linux Storage Options
#### 18.3 Understanding GPT and MBR Partitions
#### 18.4 Creating Partitions with fdisk
#### 18.5 Creating and Mounting File Systems
#### 18.6 Mounting Partitions through /etc/fstab
#### 18.7 Using UUID and Labels
#### 18.8 Defining Systemd Mounts
#### 18.9 Creating a Swap Partition

### Leson Lesson 20: Managing Stratis

#### 20.1 Understanding the Storage Stack

- The block device layer allows RHEL to use different storage solutions by including the appropriate driver in the Linux kernel
- Multipath is an optional component that is used in storage network to provide redundancy to different block devices
- Partitions make it possible to allocate different storage units on a block device
- RAID allows for the creation of redundant storage volumes
- LVM creates dynamic volumes from one or more block devices
- Storage volumes can be used for different purposes
  - File systems
  - Database
  - Ceph OSDs (Cloud storage)
    
#### Understanding LVM Usage Options

- LVM can be used with LUKS encryption to provide device-based block encryption
- LVM can be used with VDO deduplication and compression as feature of logical volumes
- LUKS and VDO can be used without LVM also


#### 20.2 Creating Stratis Volumes

- Stratis volumes always use the XFS filesystem
- Stratis volumes are thin provisioned by nature
- Volume storage is allocated form the stratis pool
- Each stratis volume needs a minimal size of 4 GiB
- Because of the thin provisioning, stratis tools must be used to monitor available storage space

#### Managing Stratis

- To work with stratis, you'll need the `stratisd` and `stratis-cli` packages
- Use the `stratis` command to create pools and filesystems
- This command has awesome tab completion
- While working with stratis, use `stratis pool list` to ensure the pool has sufficient space remaining
- To mount stratis volumes:
  - Use UUID
  - Include `x-systemd.requires=stratisd.service` as a mount option

#### 20.3 Using Stratis Snapshots

- A stratis snapshot is a metadata copy that allows you to access the state of the snapshot at anytime
- A snapshot is NOT a backup, but can be helpful in accessing deleted files
- A snapshot is mounted by its device name, not by UUID

### Lesson 21: Managing the Boot Procedure

#### 21.1 Exploring the Boot Procedure

- Fireware (computer) > Boot Device (Hard Disk) > Grub (Boot Loader) > Kernel > Systemd (manages everything on the system) > Early-state > Services > Shell (user login)

#### 21.2 Modifying Grub2 Runtime Parameters

- From the Grub2 boot menu, press e to edit runtime boot options to the end of the line that starts with linux
  - `systemd.unit=emeregency.target`
  - `systemd.unit=rescue.target`
- Press c to enter the Grub2 command mode
  - From command mode, type help for an overview of available options

#### 21.3 Changing Grub2 Persistent Parameters

- To edit persistent Grub2 parameters, edit the configuration file in `/etc/default/grub`
- After writing changes, compile changes to grub.cfg
  - `grub2-mkconfig -o /boot/grub2/grub.cfg`
  - `grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg'
 
#### 21.4 Managing Systemd Targets

- A systemd target is a group of unit files
- Some targets are isolatable, which means that they define the final state a system is starting in
- - emergency.target
  - rescue.target
  - multi-user.target
  - graphical.target
    
- When enabling a unit, it is added to a specific target

#### 21.5 Setting Default Systemd Target

- Use `systemctl get-default` to see the current default target
- Use `systemctl set-default` to set a new default target

#### 21.6 Booting into a Specific Target

- On the Grub 2 boot prompt, use `systemctl.unit=xxx.target` to boot into a specific target
- To change between targets on a running system, use `systemctl isolate xxx.target`

### Troubleshooting RHEL

#### 22.1 Troubleshooting Modes
#### 22.2 Changing the Root Password
#### 22.3 Using the Boot Debug Shell

- If something goes wrong early in the boot procedure, it may be useful to have an option to open a debug shell
- `systemctl enable --now debug-shell.service`
- While booting access a virtual terminal on TTY9
- - Ctrl-Atl-F9
  - (Mac: Cmd-Opt-Fn-F9)
  - Enter a root shell without entering a password
  - `systemctl disable --now debug-shell.service`
    
#### 22.4 Troubleshooting Filesystems Issues

- Real corruption does occur, but not often, and is automatically fixed
- Problems occur when making typo's in /etc/fstab
- To fix: if necessary, remount filesystem in read/write state and edit /etx/fstab
- Fragmentation can be an issue, different tools exist to fix
  - `xfs_fsr` is the XFS File System Reorganizer, it optimizes the XFS file systems
  - `e4defrag` can be used to defragment Ext4
 
##### Preventing /etc/fstab Related Issues

- Issues often occur after modifying /etc/fstab
- To prevent having issues, do the following after making modifications
- - Use `mount -a` to mount all filesystems in `/etc/fstab` that haven't been mounted yet
  - Use `findmnt --verify` to verify syntax
  - To verify that all works well, use `reboot` after making changes to `/etc/fstab`

#### 22.5 Fixing Network Issues

- Wrong subnet mask: all nodes in the same network should be in the same subnet
- Wrong router: the router must always be in the lcoal network
- DNS not working: verify /etc/resolv.conf contents

#### 22.6 Managing Performance Issues

- Troubleshooting performance is an art on its own
- Focus on the four key areas of performance
  - Memory
  - CPU load
  - Disk load
  - Network
- Use `top` to get a generic image, and more specialized tools only if you have a strong indication of what is wrong
  
#### 22.7 Troubleshooting Software Issues

- Dependency problems with RPM's
  - Should not occur when using repositories
- Library problems
  - Run `ldconfig` to update the library cache
- Use containers to avoid software dependecy version issues
  
#### 22.8 Fixing Memory Shortage

- Memory issues appear if available memory as shown by `free` is low
  - The definition of low depends on server workload
- As a first help to fix memory issues, swap space can be used
- Use `vmstat 2 25` to make sure that adding swap space doesn't lead too much I/O traffic
  
#### 22.9 Consulting Red Hat Websites for Tips

- Log into Redhat.com > Find Documentation

### Lesson 23: Automating with Bash Scripts

#### 23.1 Understanding Bash Scripts

##### Understanding Shell Scripts

- A shell script is an executable file, used to run tasks
- Shell scripts are used to automate common tasks
- A shell script can be as simple as a number of commands that is sequentially executed
- Scripts normally work with variables to make them react differently in a different environments
- Conditional statements such as `for`, `if`, `case` and `while` can be used to execute tasks only in specific conditions

##### Bash Scripts Compared

- Shell scripts are common as they are easy to learn and implement
- Also, a shell will always be available to interpret code from shell scripts
- If the script uses internal commands only, it's fast as nothing needs to be loaded
- There is no need to compile anything
- For more complex work, advanced scripting language like python, or automation solutions like ansible are commonly used
  
#### 23.2 Exploring Essential Script Components
- To run scripts independently, store them as executable files
- It is good practice, but not mandatory to use the .sh extension
- Each script should start with `#!/bin/bash`, the so called shebang
  - This identifies the shell that should be used to run the script code
- Use `#` for comments
- Use white lines for readability

##### Using Aurguments and Variables

- Variables are used to work with dynamic or site specific values
- Variables can be provided in many ways
  - By defining `key=value` inside the script
  - By providing an argument while running the script; the value of the argument is stored in the positional parameter $1
  - To define a variable, no $ is needed, to refer to it put a $ in front
    - `color=red`
    - `echo color`
    - `echo $color`
#### 23.3 Executing Conditional Code with `if` and `test`

##### Understanding test

- The `test` command can be used to test many things
  - Properties of files
  - Contents of strings
  - Values of integers
  - and much more
- `test` is commonly used in `if`...`then`..`else` statements
- The common use is `test condition`

##### Using if..then..else

-`if` statements are used to run commands only if a specific condition is true
- To identify the commands to be run, `then` is used
- `else` can optionally be used to run other commands if the condition is not true
- `fi` must be used to close an `if` statement

  
#### 23.4 Using `for` and `while`

- `while` is used to run commands as long as a specific condition is true
- `for` is used to iterate over a series of elements
  - Use to process all values of a variable
  - Or to work on all files in a directory that match a specific pattern
 
### Lesson 24: Managing SSH

#### 24.1 Understanding SSH Key-based Login

#### 24.2 Setting up SSH Key-based Login

- `ssh-keygen` creates a public/private key pair for the current user
  - Setting a passphrase for the private key makes it more secure, but less convenient
- `ssh-copy-id` copies the public key over to the target server

#### 24.3 Caching SSH Keys

- When using passphrases, entering a passphrase for every single command is inconvenient
- `ssh-agent /bin/bash` allocates space in the bash shell to cache the private key passphrase
- `ssh-add` adds the current passphrase to the cache
- Cached passphrases stay available for the rest of the session duration

#### 24.4 Defining SSH Client Configuration

- SSH client options can be set on the command line
  - `ssh -X` enables X forwarding. Forwarded sessions are subject to X11 security extentions controls
  - 'ssh -Y` enables trusted X forwarding
- SSH client options can be set persistently in `/etc/ssh/ssh_config` or `~/.ssh/ssh_config`
  
#### 24.5 Exploring Common SSH Server Options

- Server options are set in `/etc/ssh/sshd_config`
- - Port 22
  - PermitRootLogin
  - PubkeyAuthentication
  - PasswordAuthentication
  - X11 Forwarding
  - AllowUsers

#### 24.6 Copying Files Securely

- `scp` can be used to securely copy files over the network, using the `sshd` process
  - `scp file1 file1 student@remoteserver:/home/student`
  - `scp -r root@remoteserver:/tmp/files`
`sftp` offers an FTP client interface to securely transfer files using SSH
  - Use `put /my/file` to upload a file
  - Use `get /your/file` to download a file to the current directory
  - Use `exit` to close an `sftp` session
 
#### 24.7 Synchronizing Files Securely

- `rsync` is using SSH to synchronize files
- If source and target files already exists, `rsync` will synchronize their differences
- The `rsync` command can be used with many options, of which the following are common
- - `-r` will recursively synchronize the entire directory tree
  - `-l` synchronizes symbolic links
  - `-p` preservers symbolic links
  - `-n` will do a dry run before actually synchronizing
  - `-a` uses archive mode, which is equivalent to `-rlptgoD`
  - `-A` uses archive mode and also synchronizes ACLs
  - `-X` will synchronize SELinux context as well

### Lesson 23: Running HTTP Services

#### 25.1 Exploring HTTP Configuration

- Apache (httpd) is a common web server on Linux
- Nginx is another common web server
- The main httpd configuration file is `/etc/httpd/conf/httpd.conf`
- Additional drop-in files can be stored in `/etc/httpd/conf.d`
- The default DocumentRoot is `/var/www/htdocs`
- Apache looks for a file with the name index.html in this directory

#### 25.2 Creating a Basic Web Site


    
### Lesson 27: Apply Network Security

#### 27.1 Analyzing Service Configuration with ss

##### Monitoring Network Sockets with SS

- A network socket is a connection endpoint, consisting of an IP address followed by a port
- Sockets also exist as UNIX sockets, which are endpoints in communication with services on Linux/UNIX
- `ss` is the standard tool to show socket information
  - `ss` show all connections
  - `ss -tu` shows connected TCP and UDP sockets
  - `ss -tua` adds sockets that are in listening state
  - `ss -tln` shows TCP sockets that are in listening state only, without resolving host names
  - `ss -tulpn` shows TCP and UDP sockets in listening state, and adds process name or PID to the output
  
#### 27.2 Managing RHEL Firewalling

- The linux kernel provides the netfilter framework to take care of firewall related network operations:
  - packet filtering
  - network address translation
  - port forwarding
- Netfilter forwards specific operations to kernel modules
- `nftables` is the framework that applies firewalling
- `firewalld` is a service, managed by systemd, which RHEL uses as the front end to manage `nftables` firewalls
  
#### 27.3 Exploring Firewalld Components

- Firewalld is using different components to make firewalling easier
  - Service: the main component, contains one or more ports as well as optional kernel modules that should be loaded
  - Zone: a default configuration to which network cards can be assigned to apply specific settings
  - Ports: optional elements to allow access to specific ports
  - Additional components are available as well, but not frequently used in a based firewall configuration
    
#### 27.4 Configuring a Firewall with firewall-cmd

- The `firewall-cmd` command is used to write firewall configuration
- Use the option `-- permanent` to write to persistent (but not to runtime)
- Without `--permanent` the rule is written to runtime (but not to persistent)
- `systemctl status firewalld` (To make sure it is running)
- `firewall-cmd --list-all` (to see all of the configurations)
- `firewall-cmd --get-services` (To get an overview of the different services)
- `firewall-cmd --add-service http --permanent` (To add an service, in this case http)

### Lesson 29: Configuring Time Services

#### 29.1 Exploring Linux Time

- While booting, the system gets its time from the hardware clock
- System time is set next, according to the hardware clock
- Interent time can be used to synchronize time

##### Managing Linux Time

- `hwclock` is used to set hardware time
- Also use it to synchronize time
  - `hwclock --systohc`
  - `hwclock --hctosys`
- `date` is used to show and set time
- `timedatectl` is used to manage time and time zone configuration
  
#### 29.2 Setting Time with timedatectl

- `timedatectl` is a new utility that allows you to manage all aspects of system time
  - `timedatectl status` will show all time properties currently used
  - `timedatectl set-time` is used to change the time
  - `timedatectl set-timezone` is used to change the timezone
  - `timedatectl set-ntp` enables or disables NTP time synchronization
- To synchronize time using NTP, an NTP service must be configured
  - RHEL 9 uses `chrony`
  - `systemd-timesyncd.service` is another NTP service - not currently used on RHEL
    
#### 29.3 Managing an NTP Client

- `chronyd` is the default RHEL 9 NTP service
- Use `/etc/chrony.conf` to specify synchronization parameters
  - `pool 2.rhel.pool.ntp.org iburst` configures a pool of NTP servers
  - `server myserver.example.com` configures a single NTP time source
  - Use `iburst` to permit fast synchronization
- After modifying its contents, use `systemctl restart chronyd` to restart the `chronyd` service
- Use `chronyc sources` to verify proper synchronization 

### Lesson 30: Using Remote Filesystems and Automount

#### 30.2 Mounting NFS Shares

- Make sure that `nfs-utils` is installed
- Use `showmount -e nfsserver` to show exports
- Use `mount nfsserver:/share /mnt` to mount
  
#### 30.3 Understanding Automount

- Automount is a autofs service that observes directories, upon the directory activity the mount will happen.
- In `/etc/auto.master` you'll identify the directory that automount should manage, and the file that is used for additional mount information.
  - `/data /etc/auto.nfsdata`
- In `/etc/auto.nfsdata` you'll identify the subdirectory on which to mount, and what to mount exactly.
  - `files -rw nfsserver:/nfsdata`
- Ensure the autofs service is started:
  - `systemctl enable --now autofs`
Tip: check /etc/auto.msic for syntax examples on the exam
    
#### 30.5 Setting up Automount for Home Directories

- Automount is common for home directory access
- In this scenario, an NFS server is providing access to home directories, and the homedirectory is automounted by a user while logging in
- To support different directory names in one automount line, wildcards are used
  - `* -rw nfsserver:/home/ldap/&`
 
### Lesson 31: Running Containers

#### 31.1 Understanding Containers

##### Understanding Containers

- A container is like an app on a smartphone; it's a package that contains all that is needed to run an application
- This makes containers the solution for the dependency challenge
- Containers are started from container images
- Images are provided through image registries

##### Containers and Linux

- Containers rely on features provided by the Linux operating system
  - Control groups set limits to the amount of resources that can be used
  - Namespaces provide isolation to ensure the container only has access to its own data and configuration
  - SELinux enforces security
    
##### Understanding Rootless Containers

- Containers need a user ID to be started on the host computer
- Root containers are started by the root user
- Rootless containers are started as a non-root user
  - Rootless containers can generate a UID dynamically, or be preconfigured to use a specific UID
- Rootless containers have a few limitations
  - No unlimited access to the filesystem
  - Can't bind to privileged network ports

##### Containers and Microservices

- Complex applications are typically composed of multiple containers
- Normally one container runs one application
- This offers the benefit of better manageability
- To manage microservices, orchestration platforms like Kubernetes or Red Hat OpenShift are used

##### Understanding Red Hat Container Tools

- podman manages containers and container images
- buildah is advanced tool to create container images
- skopeo is an advanced tool to manage, copy, delete and sign images
  
#### 31.2 Managing Containers

- Container images are used to package container applications with all of their dependecies
- Images are built according to the Open Containers Initiative (OCI) specification
- The OCI standard guarantees compatibility so that images can be used in different environments, like `podman` on RHEL or `docker`

##### Using Registries

- Public registries such as hub.docker.com provide access to community-provided container images
- Private registries can be created to host container images internally
- Images optimized for use in Red Hat environments are provided through quay.io
- Red Hat distributes certified images that are accessible only with Red Hat credentials
  - registry.redhat.io is for official Red Hat products
  - registry.connect.redhat.com is for third-party products
- Red Hat container catalog (https://catalog.redhat.com) is a web interface to the Red Hat images

##### Accessing Red Hat Registries

- Red Hat registries can be accessed with a Red Hat account
- Devoloper account (https://developers.redhat.com) do qualify
- Use `podman login registry.redhat.io` to login to a registry
- Use `podman login registry.redhat.io --get-login` to get your current login credentials

##### Configuring Registry Access

- Registry access is configured in `/etc/containers/registries.conf`
- Default registries are in the [registries.search] section
- Registries that don't have an SSL certificate are in [registries.insecure]
- A user specific registries.conf file can be created as `~/.config/containers/registries.conf`

##### Using Containerfile

- A Containerfile (previously known as Dockerfile) is a text file with instructions to build a container image
- Containerfiles have instructions to build a custom container based on a base image such as the UBI image
- UBI is the Universal Base Image, an image that Red Hat uses for all of its products
  
#### 31.3 Running Containers

- Use `podman run` to run a container image
  - It will search for the image in the configured registries
  - If found, it will pull the image and run the container
- Use `podman ps` to verify that the image currently is running
- If not seen, use `podman ps -a` to also show containers that have stopped
- Use `podman inspect` to see what is inside an image or a container

##### Understanding Container Commands

- When started with `podman run`, the container runs its default command
- To run an alternative command, it can often (not always) be specified as a command line arguement
- - `podman run ubi8 sleep`
- To run an image from a specific registry, specify the complete image name
- Command line options for the specific `podman` command need to be specified before the name of the image

##### Running Containers

- Troubleshooting containers is often troubleshooting the container primary command
- Notice that some containers run to completion and there's nothing really to troubleshoot if you don't see them!
- Use `podman inspect container` to see which command is started
- Use `podman run -it`... start the container with an interactive terminal
- Use `podman logs` to explore logs created by the container
  
#### 32.4 Mapping Ports and Configuring Variables

##### Managing Environment Variables

- Some images require site-specific information to be passed while running
- Use `-e KEY=VALUE` to pass these values through environment variables while running the container

##### Configuring Application Access

- Container access happens through port mappings
- A port on the container host is exposed and forwards traffic to the container port
- Port mappings can be set while starting the container, but not on a container that has already been started
- Rootless containers can only map to a non-privileged port (higher than 1024)

#### 31.5 Providing Persistent Storage

##### Rootless Containers and Namespaces

- Rootless containers are launched in a namespace
- The namespace provides isolation, allowing the container inside the namespace to have root access which does not exist outside the namespace
- This means that inside the container namespace different UIDs are used than outside of the namespace
- To ensure that access is working all right, UIDs are mapped between the namespace and the host OS
- The `podman unshare` command can be used to run commands inside the container namespace
- To get the UID mapping, use `podman unshare cat /proc/self/uid_map`

##### Managing Containers Using Systemd Services

- Create a regular user account to manage all containers
- Use `podman` to generate a user systemd file for an existing container
- 
#### 31.6 Starting Containers as Systemd

- Create a regular user account to manage all containers
- Use `podman` to generate a user systemd file for an existing container
- Before, `mkdir ~/.config/systemd/user; cd ~/.config/systemd/user`
- Notice the file will be generated in the current directory
- - `podman generate systemd --name myweb --files --new`
- To generate a service file for a root container, do it from `/etc/systemd/system` as the current directory

##### Understanding podman generate --new

- The `podman generate --new` optoin will create a new container when the systemd unit is started, and delete that container when the unit is stopped
- Without the `--new` option, the container is not newly created or deleted when it is stopped

##### Creating User Unit Files

- Use `podman generate` to create user-specific unit files in `~/.config/systemd/user`
- Edit the file that is generated and change the `WantedBy` line such that its read `WantedBy=default.target`
- Manage them using `systemctl --user`
- - `systemctl --user daemon-reload`
  - `systemctl --user enable myapp.service` (requires linger)
  - `systemctl --user start myapp.service`
- `systemctl --user` commands only work when logging in on console or SSH and do not work in sudo and su sessions

##### Surviving all Challenges

- Log in as the user that should start the container, do NOT use `su -`
- - set a password to do so
- As that user, `mkdir -p ~/.config/systemd/user;cd ~/.config/systemd/user`
- From that directory: `podman generate --new`
- After generating, make sure that the container-name.service file has `WantedBY=default.target` (not just multi-user.target)

#### 31.7 Building Images from Containerfiles

