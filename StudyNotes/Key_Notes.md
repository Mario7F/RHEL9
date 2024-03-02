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
  
### Lesson 9 Managing Users And Groups
-
-
-
### Lesson 10 Securing Files With Permissions
-
-
-

