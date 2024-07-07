### Lesson 4 Lab
- Locate the `man` page that shows how to set a password
- Use the `man` page for `useradd` and create a user with the name Joy
- Set the password for user Joy to "password"
- Use `vim` to create a file with the name users, and make sure that it contains the names alex, linda, and belinda on separate lines

 ![Screen Shot 2024-03-04 at 2 10 14 PM](https://github.com/Mario7F/RHEL9/assets/59115100/cf7d47ba-0c1a-4120-ab08-e5043eb6d0c9)

 ![Screen Shot 2024-03-04 at 2 19 34 PM](https://github.com/Mario7F/RHEL9/assets/59115100/c37ffc59-daeb-4561-85a6-d8d4f0f8b029)

 ![Screen Shot 2024-03-04 at 2 21 48 PM](https://github.com/Mario7F/RHEL9/assets/59115100/f63b5ff2-cd45-4a30-8030-d93d1d527bc1)

 ![Screen Shot 2024-03-04 at 2 23 50 PM](https://github.com/Mario7F/RHEL9/assets/59115100/42ed38f4-2e34-4fa3-9cc3-e4f70b25e3cc)

 ![Screen Shot 2024-03-04 at 2 25 03 PM](https://github.com/Mario7F/RHEL9/assets/59115100/ee96ac8d-4020-4498-9e5e-944bc79d5854)

 ### Lesson 5 Lab
 - Set a variable `color` to the value `red` and ensure that this setting is available every time your currrent user account logs in
 - Also create an alias that runs the command `ls -ltr` while executing the `dir` command
 - Ensure that the Bash History file can grow to a maximum size of 2500 entries

 ![Screen Shot 2024-03-05 at 7 00 09 AM](https://github.com/Mario7F/RHEL9/assets/59115100/69c5c3ed-3175-499b-aad5-840773c990c4)

 ![Screen Shot 2024-03-05 at 7 33 30 AM](https://github.com/Mario7F/RHEL9/assets/59115100/09d4b7a9-1d53-4cdb-a894-b0276fcb2d0f)

 ![Screen Shot 2024-03-05 at 7 44 11 AM](https://github.com/Mario7F/RHEL9/assets/59115100/a3df539d-6bc8-46f1-81cb-ce26f3d9eb0e)

 ![Screen Shot 2024-03-05 at 7 45 25 AM](https://github.com/Mario7F/RHEL9/assets/59115100/6c5496bd-31f3-453d-a32f-35a147d3ae52)

 ### Lesson 6 Lab
 - Use `tar` to create a compressed archive of all files in the /etc and /opt directories. Write this archive to your home directory
 - Create a symbolic link to the archive you've just created in the /tmp directory
 - Remove the archive from your home directory.

  ![Screen Shot 2024-03-06 at 11 21 16 AM](https://github.com/Mario7F/RHEL9/assets/59115100/e612b9bf-ca13-402c-b6d8-32cb0e662912)

  ![Screen Shot 2024-03-06 at 11 26 03 AM](https://github.com/Mario7F/RHEL9/assets/59115100/272c0cda-2202-4cbb-b100-7041032a63ee)

  ![Screen Shot 2024-03-06 at 11 23 18 AM](https://github.com/Mario7F/RHEL9/assets/59115100/235f9701-7cb1-4b13-9870-23fe93478f01)

  ![Screen Shot 2024-03-06 at 11 24 58 AM](https://github.com/Mario7F/RHEL9/assets/59115100/f750aad9-9748-4d21-ae5c-b0728acc56da)

  ### Lesson 7 Lab
  - Use `head` and `tail` to display the fifth line of the file /etc/passwd
  - Use `sed` to display the fifth line of the file /etc/passwd (-n 5p)
  - Use `awk` in a pipe to filter the last column out of the results of the command `ps aux` {print $NF}'
  - Use `grep` to show the names of all files in /etc that have lines that contains the text "root" as a word
  - Use `grep` to show all lines from all files in /etc that contain exactly 3 characters
  - Use `grep` to find all files that contain the string "alex", but make sure that "alexander" is not included in the result

![Screen Shot 2024-03-07 at 8 38 28 AM](https://github.com/Mario7F/RHEL9/assets/59115100/a8f4970e-9ba0-4225-bda5-f90b68882277)

![Screen Shot 2024-03-07 at 8 41 27 AM](https://github.com/Mario7F/RHEL9/assets/59115100/cb05cb25-6a99-44ab-9060-0c3bcb20873d)

![Screen Shot 2024-03-07 at 8 45 04 AM](https://github.com/Mario7F/RHEL9/assets/59115100/e4524402-8973-4bd1-8233-6103d91f756c)

![Screen Shot 2024-03-07 at 8 46 04 AM](https://github.com/Mario7F/RHEL9/assets/59115100/8179591c-2630-454b-8dff-0c9e86977e33)

  

### Lesson 8 Lab

- Use `useradd linda` to create a user linda
- Create a sudo configuration that allows linda to perform common user management tasks
  - Allow using useradd, usermod and userdel
  - Allow changing passwords, but not the password for user root
- Ensure that the user only needs to enter a password for `sudo` operations every 60 minutes

![Screen Shot 2024-03-02 at 11 39 24 AM](https://github.com/Mario7F/RHEL9/assets/59115100/a9e6592d-dc39-4cc2-8541-6ac85358fd7f)

![Screen Shot 2024-03-02 at 11 46 48 AM](https://github.com/Mario7F/RHEL9/assets/59115100/4d02a892-8a59-4b1b-a8fb-9434d3709039)

![Screen Shot 2024-03-02 at 11 47 43 AM](https://github.com/Mario7F/RHEL9/assets/59115100/97e79fa8-55b5-405c-bf0d-2e8e0694c5be)

![Screen Shot 2024-03-02 at 11 50 27 AM](https://github.com/Mario7F/RHEL9/assets/59115100/3076d7c3-a780-4808-92ce-ddce0c6c1691)

![Screen Shot 2024-03-02 at 11 54 31 AM](https://github.com/Mario7F/RHEL9/assets/59115100/c7d1f100-6729-4c77-b4bc-b6ebb297d404)


### Lesson 9 Lab

- Make sure that new users require a password with a maximal validity of 90 days
- Ensure that while creating users, an empty file with the name newfile is created to their home directory
- Create users anna, audrey, linda, and lisa
- Set the passwords for anna and audrey to 'password', disable the passwords for linda and lisa
- Create the groups profs and students, and make users anna and audrey members of profs, and linda and lisa members of students

![Screen Shot 2024-03-02 at 8 14 10 PM](https://github.com/Mario7F/RHEL9/assets/59115100/815acaba-8a3d-4218-b5f4-5d583bdf7b53)

![Screen Shot 2024-03-02 at 8 10 44 PM](https://github.com/Mario7F/RHEL9/assets/59115100/8682c74a-1dcb-4218-96ee-6a4de2b79af3)

![Screen Shot 2024-03-02 at 8 16 02 PM](https://github.com/Mario7F/RHEL9/assets/59115100/8cd21a2a-7984-4d98-bceb-09c24a2abf9c)

![Screen Shot 2024-03-02 at 8 17 53 PM](https://github.com/Mario7F/RHEL9/assets/59115100/83084055-1372-44a0-941a-6d3183454c97)


![Screen Shot 2024-03-02 at 8 19 04 PM](https://github.com/Mario7F/RHEL9/assets/59115100/fd84ee35-7a2f-4f7d-a39e-30d58aa79952)

![Screen Shot 2024-03-02 at 8 19 55 PM](https://github.com/Mario7F/RHEL9/assets/59115100/cdd972ec-6962-44e8-97ea-ab13aacc6cb9)

![Screen Shot 2024-03-02 at 8 20 45 PM](https://github.com/Mario7F/RHEL9/assets/59115100/9ea34763-a804-4038-b295-f2ec39683640)

![Screen Shot 2024-03-02 at 8 26 49 PM](https://github.com/Mario7F/RHEL9/assets/59115100/cfa8540f-cd1e-4732-a37e-bddb779c5409)

![Screen Shot 2024-03-02 at 8 29 39 PM](https://github.com/Mario7F/RHEL9/assets/59115100/01a2efae-321f-458a-9b90-7d26a9641100)

### Lesson 10 Lab
- Create a shared group directory structure /data/profs and /data/students that meets the following conditions
   - Members of the groups have full read and write access to their directories, others has no permissions at all
- Modify default permission settings such that normal users have a umask that allow the user and group to write, create and execute files and directories while denying all other access to others

- ![Screen Shot 2024-03-04 at 8 19 39 AM](https://github.com/Mario7F/RHEL9/assets/59115100/6a40600b-78f7-4792-990d-b65399ba169a)

- ![Screen Shot 2024-03-04 at 8 30 15 AM](https://github.com/Mario7F/RHEL9/assets/59115100/7b7e78ff-95b2-4301-bb54-3fb6c20aa2c8)

- ![Screen Shot 2024-03-04 at 8 34 55 AM](https://github.com/Mario7F/RHEL9/assets/59115100/4b30bbce-a98d-479b-83f4-fa6eb9f18464)

- ![Screen Shot 2024-03-04 at 8 37 45 AM](https://github.com/Mario7F/RHEL9/assets/59115100/5b753bf3-ff96-446e-9527-01f842d1d5c9)

  ### Lesson 11 Lab
  - Set the hostname for your server to rhcsaserver.example.com
  - Set your server to a fixed IP address that matches your current network configuration
  - Also set a second IP address 10.0.0.10/24 on the same network interface
  - Enable host name resolution for your local server hostname
  - Reboot and verify your network is still working with the new settings
 
  - ![Screen Shot 2024-03-26 at 6 09 35 AM](https://github.com/Mario7F/RHEL9/assets/59115100/09c8bf18-c260-4b3a-a1f2-6878be333864)
 
  - ![Screen Shot 2024-03-26 at 6 07 37 AM](https://github.com/Mario7F/RHEL9/assets/59115100/88d53b3e-4dc8-4422-a41c-2b3687051aba)
 
  - ![Screen Shot 2024-03-26 at 6 08 44 AM](https://github.com/Mario7F/RHEL9/assets/59115100/bd651caf-f0c6-44fe-9553-13ecae69574f)
 
  - ![Screen Shot 2024-03-26 at 6 10 35 AM](https://github.com/Mario7F/RHEL9/assets/59115100/20c0a55c-e0cb-4653-bd23-517d10762f17)
 
  - ![Screen Shot 2024-03-26 at 6 11 06 AM](https://github.com/Mario7F/RHEL9/assets/59115100/797fb856-9212-4f3d-94ea-82d0f62578a0)
 
  - ![Screen Shot 2024-03-26 at 6 12 00 AM](https://github.com/Mario7F/RHEL9/assets/59115100/456bdbfa-5323-4304-8bfd-515a0d1c44b1)
 
  - ![Screen Shot 2024-03-26 at 6 19 54 AM](https://github.com/Mario7F/RHEL9/assets/59115100/4d8d51c9-000d-453d-83ba-e5e9ec0697e4)
 
  - ![Screen Shot 2024-03-26 at 6 21 13 AM](https://github.com/Mario7F/RHEL9/assets/59115100/022022b1-7554-4583-af0f-e23e5a2d975b)
 
  - ![Screen Shot 2024-03-26 at 6 23 25 AM](https://github.com/Mario7F/RHEL9/assets/59115100/3ee69ede-4e1d-4197-8694-67eb97967ca4)
 
  - ![Screen Shot 2024-03-26 at 6 26 00 AM](https://github.com/Mario7F/RHEL9/assets/59115100/c5d1027e-17d5-4c89-a02e-cf7ab2d60c8c)


### Lesson 12 Lab: Managing Software
- Ensure your system is using a repository for base packages as well as application streams
- Find the package that contains the seinfo program file and install it
- Download the httpd package from the repositories without installing it, and query to see if there are any scripts in it

### Lesson 14 Lab: Managing Processes
- Create a user linda and open a shell as this user
- As linda, run two background processes `sleep 600`; one of them with the highest possible priority, the other one with the lowest possible priority
- Use the most efficient way to terminate all current sessions for user linda

![Screen Shot 2024-04-24 at 4 19 34 PM](https://github.com/Mario7F/RHEL9/assets/59115100/78241599-24bc-41a0-ad35-6cce70bb55f5)

![Screen Shot 2024-04-24 at 4 19 59 PM](https://github.com/Mario7F/RHEL9/assets/59115100/bd64eb85-db17-4ac3-bea0-351b56dcf5af)


![Screen Shot 2024-04-24 at 4 22 39 PM](https://github.com/Mario7F/RHEL9/assets/59115100/98bd8788-e767-429f-ba47-0b4ed2fabda1)


### Lesson 15 Lab: Working with Systemd

- Make sure the httpd service is automatically started
- Edit its configuration such that on failure, it will continue after 1 minute

### Lesson 15 Lab: Running Schedule Jobs

- Ensure the systemd timer that cleans up tmp files is enabled
- Run a cron job that will issue the command `touch /tmp/cronfile` 5 minutes from now
- Use `at` to schedule a job to power off your system at a convenient time later today

### Lesson 27 Lab: Configuring a Firewall

- Configure `firewalld` such that remote access to the SSH and FTP processes is allowed. Make sure the configuration is applied immediately as well as persistently.

![Screen Shot 2024-07-06 at 12 37 16 PM](https://github.com/Mario7F/RHEL9/assets/59115100/49ee5309-6488-448d-ae2b-033e7b8d2824)


![Screen Shot 2024-07-06 at 12 35 23 PM](https://github.com/Mario7F/RHEL9/assets/59115100/b319756d-2059-435a-bdfc-ec63982734e5)


![Screen Shot 2024-07-06 at 12 40 57 PM](https://github.com/Mario7F/RHEL9/assets/59115100/9a4c79ad-ba5d-4968-a0ae-d6ce8a5ccd45)


![Screen Shot 2024-07-06 at 12 42 17 PM](https://github.com/Mario7F/RHEL9/assets/59115100/f3b5f880-0a55-491a-9d34-e6dc9797f090)


### Lesson 29 Lab: Configuring Time Services

- Configure your system to synchronize time with the servers in pool.ntp.org
  
![Screen Shot 2024-07-06 at 8 22 59 PM](https://github.com/Mario7F/RHEL9/assets/59115100/c874cbab-631e-4d74-9e93-ea490b86016e)

![Screen Shot 2024-07-06 at 8 24 20 PM](https://github.com/Mario7F/RHEL9/assets/59115100/daffd868-fada-418f-8476-1b0b58227b0e)

![Screen Shot 2024-07-06 at 8 25 27 PM](https://github.com/Mario7F/RHEL9/assets/59115100/07a41bc2-2ba7-4d3a-9dbd-e1df7f1f2be7)


![Screen Shot 2024-07-06 at 8 27 36 PM](https://github.com/Mario7F/RHEL9/assets/59115100/45082c8f-68db-4738-9065-d868fb68c050)


![Screen Shot 2024-07-06 at 8 28 52 PM](https://github.com/Mario7F/RHEL9/assets/59115100/e7c5fa5d-be5d-4fb4-8b9f-59b7a9aa7148)

