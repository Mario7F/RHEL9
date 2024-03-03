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
