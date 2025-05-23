### Виконала самостійно Слобожан Софія РПЗ-23А
# Laboratory work № 9 
### Topic: “System and user protection in Linux. Creating users and groups”
### Objective: Obtaining practical skills in working with the Bash command shell.Familiarization with basic actions when creating new users and new user groups.
## Preliminary Preparation

### Glossary of Terms

| Term       | Meaning                                       |
|------------|-----------------------------------------------|
| `sudo`     | Run commands as administrator                 |
| `su`       | Switch to another user                        |
| `id`       | Show user and group ID                        |
| `groupadd` | Create a new group                            |
| `usermod`  | Modify user properties                        |
| `getent`   | Query system databases                        |
| `chage`    | Manage password aging policies                |

---

### Theoretical Questions

### 1. What is the concept of UPG and when is it appropriate to use them?
- **User  Private Group (UPG)**:
  - A User Private Group (UPG) is a group that is automatically created for each user when they are added to the system. The group name is the same as the username, and the only member of this group is the user themselves.
  - **When to Use UPG**:
    - UPGs are particularly useful in environments where users need to have their own private space for files and directories. This setup enhances security and privacy, as files created by the user can be owned by their private group, preventing other users from accessing them unless explicitly allowed.
    - UPGs are beneficial in collaborative environments where users may need to share files with specific individuals while keeping their personal files secure from others.

### 2. What commands can be used to create user groups? Provide examples.
- **Commands to Create User Groups**:
  - `groupadd`: This command is used to create a new group in the system.
    - **Example**:
      ```bash
      groupadd super_admins
      groupadd noob_users
      groupadd good_students
      ```
  - In the above examples, three groups are created: `super_admins`, `noob_users`, and `good_students`.

### 3. What commands can be used to change user group settings? Provide examples.
- **Commands to Change User Group Settings**:
  - `groupmod`: This command is used to modify an existing group’s settings, such as changing the group name or GID (Group ID).
    - **Example**:
      ```bash
      groupmod -n new_group_name old_group_name
      groupmod -g new_gid group_name
      ```
    - In the first example, the group name `old_group_name` is changed to `new_group_name`. In the second example, the GID of `group_name` is changed to `new_gid`.
  
  - `gpasswd`: This command can also be used to administer /etc/group and /etc/gshadow, allowing you to add or remove users from a group.
    - **Example**:
      ```bash
      gpasswd -a username group_name
      gpasswd -d username group_name
      ```
    - In the first example, `username` is added to `group_name`, while in the second example, `username` is removed from `group_name`.
## Command description table:
| **Command**        | **Purpose and Functionality**                                                                 |
|--------------------|-----------------------------------------------------------------------------------------------|
| `id`               | Displays UID, GID, and groups of the current or specified user.                              |
| `who`              | Shows a list of users currently logged into the system.                                       |
| `w`                | Displays who is logged in and what they are doing.                                            |
| `last`             | Shows the login history of users, including reboots.                                          |
| `groupadd`         | Creates a new user group.                                                                     |
| `groupmod`         | Modifies a group name or GID.                                                                 |
| `groupdel`         | Deletes a user group from the system.                                                         |
| `useradd`          | Adds a new user account.                                                                      |
| `passwd`           | Sets or changes a user's password.                                                            |
| `usermod`          | Modifies user account properties (e.g., add to group).                                        |
| `userdel`          | Deletes a user account.                                                                       |
| `groups`           | Lists the groups a user belongs to.                                                           |
| `getent`           | Retrieves entries from system databases (e.g., passwd, group).                                |
| `grep`             | Searches for patterns in files (e.g., in /etc/group or /etc/passwd).                          |
| `chage`            | Manages password aging policies.                                                              |
| `sudo`             | Executes a command with superuser privileges without switching users.                         |
| `su`               | Switches to another user (often root).                                                        |
| `finger` (optional)| Shows user information like full name, home directory, login shell (if installed).            |
## Practical Tasks in the Terminal

### 1. Display Information About the Current User
- Use the following commands to display information about the current user:


![image](https://github.com/user-attachments/assets/7b211e9e-9a9d-4601-92c4-833ae24d2879)



### 2. Practice with `last`, `w`, and `who` Commands
- Execute the following commands and compare their outputs:


![image](https://github.com/user-attachments/assets/4f575106-d535-412c-9ff6-8883f107c463)




#### Comparison of Outputs:
- last: Shows the history of user logins, including the time and date of each login. It does not show currently active sessions.
- w: Displays currently logged-in users along with their active processes and idle time. It provides more detailed information about user activity.
- who: Lists users currently logged in but does not show their active processes or idle time. It provides the least amount of detail compared to the other two commands.

### 3. Create New User Groups
- Create the following user groups and determine their identifiers:


![image](https://github.com/user-attachments/assets/37c364a1-27c1-42b8-9676-d9da3bd2a3bd)


### 4. Create New Users
- Create three new users and set passwords for each:


![image](https://github.com/user-attachments/assets/e1587575-a031-4eed-9817-077ea7c48a6b)



### 5. Add New Users to Groups
- Add users to the created groups:


![image](https://github.com/user-attachments/assets/355f1370-6b35-4756-9842-a84c791d2728)



### 6. View Group Information
- Check the group information and the users in each group:


![image](https://github.com/user-attachments/assets/b24723ab-1425-440e-95a6-34f4327ab32a)



#### Explanation:
- The output will show the group name, GID, and the members of each group. You should see that `super_admins` contains `user1` and `user2`, `noob_users` contains `user2` and `user3`, and `good_students` contains all three users.

### 7. Delete the First Created User
- Delete the first user and check if information about them remains in the groups:


![image](https://github.com/user-attachments/assets/629edce0-f0e4-4c1a-b3b3-6bdb1492b1a1)



### 8. Delete the Second User
- Delete the second user and check if information about them remains in the groups:


![image](https://github.com/user-attachments/assets/25a9ebaa-3c3f-4d03-ae4a-e6b79a096de1)



### 9. Delete the Third User
- Delete the third user and check if information about them remains in the groups:


![image](https://github.com/user-attachments/assets/09b65b1f-9f84-4796-966e-894984ceff30)



### 10. View Existing User Groups
- Check the existing user groups:


![image](https://github.com/user-attachments/assets/dd404fee-d507-469f-94a2-2f9e6b725db0)



### 11. Delete Created User Groups
- Delete the created user groups:


![image](https://github.com/user-attachments/assets/e464bf03-f4a6-4406-9305-4293907f6958)



### 12. View Information About Existing User Groups
- Check if the groups were successfully deleted:


![image](https://github.com/user-attachments/assets/0de614f1-0a2c-4c51-a301-4ee9318c4d44)


## Control Questions and Answers

### 1. Why are passwords not stored in plain text in configuration files?
- Passwords are not stored in plain text to enhance security. Storing passwords in an encrypted or hashed format prevents unauthorized access and protects user credentials from being easily compromised. If an attacker gains access to the configuration files, they would not be able to retrieve the actual passwords.

### 2. Why is it not recommended to perform everyday operations using the root account?
- Using the root account for everyday tasks is discouraged because it poses a significant security risk. The root account has unrestricted access to all system files and commands, which increases the likelihood of accidental changes or deletions that could harm the system. Additionally, if malware or an attacker gains access to the root account, they can cause extensive damage.

### 3. What is the difference between the privilege escalation mechanisms `su` and `sudo`?
- **`su` (substitute user)**: This command allows a user to switch to another user account, typically the root account. When using `su`, the user must provide the target user's password.
- **`sudo` (superuser do)**: This command allows a permitted user to execute a command as the superuser or another user, as specified by the security policy. With `sudo`, the user does not need to know the target user's password; instead, they provide their own password. `sudo` also logs the commands executed, providing an audit trail.

### 4. Why is the home directory of the root user not located in the `/home` directory?
- The home directory of the root user is located in `/root` instead of `/home` because `/home` is designated for regular user accounts. This separation helps to maintain security and organization within the file system, ensuring that the root user's files are kept distinct from those of regular users.

### 5. What is the purpose of the `getent` command?
- The `getent` command is used to retrieve entries from the system databases, such as user accounts, groups, and other information stored in the Name Service Switch (NSS) databases. It can be used to query information from various sources, including local files and network services.

### 6. How can a user's password be changed?
- A user's password can be changed using the `passwd` command followed by the username. For example:
  ```bash
  passwd username
  ```
  The system will prompt for the new password and confirm it.

### 7. How can existing user groups be deleted? Will any information about them remain in the system?
- Existing user groups can be deleted using the `groupdel` command followed by the group name. For example:
  ```bash
  groupdel groupname
  ```
  Once a group is deleted, all information about that group is removed from the system, and it will no longer exist in the group database.

### 8. What is the purpose of the `chage` command?
- The `chage` command is used to change user password expiry information. It allows administrators to set parameters such as the minimum and maximum age of a password, warning periods before expiration, and the inactivity period after which the account will be disabled.

### 9. What parameters of the `usermod` command do you consider the most commonly used?
- The most commonly used parameters of the `usermod` command include:
  - `-aG`: Adds a user to supplementary groups without removing them from other groups.
  - `-l`: Changes the username of the user.
  - `-d`: Changes the user's home directory.
  - `-s`: Changes the user's login shell.
---
## Conclusion

In this practical work, we explored various aspects of user and group management in a Linux environment. We began by understanding the importance of user private groups (UPGs) and their role in enhancing security and privacy for individual users. Through hands-on exercises, we learned how to create user groups, add users to these groups, and manage user accounts effectively.Overall, this practical work provided valuable insights into the administration of user accounts and groups in Linux, equipping us with the necessary skills to manage user permissions and enhance system security effectively. The knowledge gained will be beneficial for future tasks involving system administration and user management in Linux environments.


