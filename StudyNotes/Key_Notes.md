# Notes From Sander Van Vught RHCSA RHEL 9 Course

### Lesson 4 Exploring The Essential Tools
 -
 -
 -


### Lesson 5 Understanding The Bash Shell
-
-
-
### Lesson 6 Using The Essential File Management Tools
-
-
-
### Lesson 7 Managing Text Files
-
-
-
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
- Sudo configuration is managed through /etc/sudoers
- Don't edit this file directly, only edit it through `visudo`
- Instead of editing /etc/sudoers, consider creating drop-in files in /etc.sudoers.d
- /etc/sudoers is installed from packages and may be overwritten, drop-in files will never be overwritten

  ##### *Providing Administator Access*
  - Users that are member of the group `wheel` get full sudo access
   - This is accomplished by `%wheel ALL=(ALL) ALL` in /etc/sudoers
   - Use `usermod -aG wheel myuser` to add a user to the group Wheel
  - Do NOT enable the line `%wheel ALL =(ALL) NOPASSWD: ALL`
   - It will provide full sudo access  without entering a password and is very dangerous
  --If you don't like entering your user password every five minutes, increase authentication token expiration by adding the following `Defaults timestamp_type=global,timestamp_timeout=60`

 #### Providing Access To Specific Task
 - Use drop-in files to provide admin access to specific task
  - username `ALL=/sbin/useradd,/usr/bin/passwd
- Consider using command arguments to make the commands more specific
  - `%users ALL=/bin/mount /dev/sdb,/bin/umount /dev/sdb
  - username `ALL=/usr/bin/passwd,! /usr/bin/passwd root

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
- #### 9.2 Setting User Properties
- User properties are managed in /etc/password
   - *Name:* the name of the account
   - *Password:* the secret that is used for authentication, may be disabled
   - *UID:* a unique identifier for users
   - *GID:* the ID of the primary group
   - *GECOS:* additional non-mandatory information about the user
   - *Home Directory:* the environment where users create personal files
   - *Shell:* the program that will be started after successful authentication
 
### Lesson 10 Securing Files With Permissions
-
-
-

