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
