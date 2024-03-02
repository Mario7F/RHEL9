# Notes From Sander Van Vught RHCSA RHEL 9 Course

### Lesson 4 Exploring the essential tools
 -
 -
 -


### Lesson 5 Understanding the bash shell
-
-
-
### Lesson 6 Using the essential file management tools
-
-
-
### Lesson 7 Managing Text Files
-
-
-
### Lesson 8 Using Root Privileges 
- A user account with UID 0 exist to perform administration tasks
- This user by default has the name root
- The root user operates in kernel space and for that reason has unlimited access to all parts of the system
- If the root user is not activated, the administrative user is used for administration tasks
- To activate the root user, you;ll just have to set a password
- From a security perspective, it may be a good idea not to have an active root user
- Additional measures are possible to restrict root user access to a system
  - Remote root login using secure shell (SSH) can be allowed or not
- The `su` command is used to switch current user account from a shell environment
- If `su` is used with the `-`option, the complete environment of the target user is loaded
- While using `su`, the password of the target user is entered
- If the root user has a password, `su -` can be used
- Using `su -` to open a root shell is considered bad practice, use `sudo -i` instead
### Lesson 9 Managing Users And Groups
-
-
-
### Lesson 10 Securing Files With Permissions
-
-
-

