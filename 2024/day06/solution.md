# Day 6 Answers: File Permissions and Access Control Lists

### Tasks

1. **Understanding File Permissions:**
   - Create a simple file and run `ls -ltr` to see the details of the files.
   - Each of the three permissions are assigned to three defined categories of users. The categories are:
     - **Owner:** The owner of the file or application.
       - Use `chown` to change the ownership permission of a file or directory.
     - **Group:** The group that owns the file or application.
       - Use `chgrp` to change the group permission of a file or directory.
     - **Others:** All users with access to the system (outside the users in a group).
       - Use `chmod` to change the other users' permissions of a file or directory.
   - Task: Change the user permissions of the file and note the changes after running `ls -ltr`.

   **Answer**
   
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task1.png?raw=true)
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task1-1.png?raw=true)


3. **Writing an Article:**
   - Write an article about file permissions based on your understanding from the notes.

   **Answer**

    Check out my article: [LinkedIn](https://www.linkedin.com/posts/sdadu2206_file-permissions-access-control-day-6-activity-7250210896835219456-nmqV?utm_source=share&utm_medium=member_desktop)

4. **Access Control Lists (ACL):**
   - Read about ACL and try out the commands `getfacl` and `setfacl`.
   - Task: Create a directory and set specific ACL permissions for different users and groups. Verify the permissions using `getfacl`.

   **Answer**
   
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task3.png?raw=true)

6. **Additional Tasks:**
   - **Task:** Create a script that changes the permissions of multiple files in a directory based on user input.

   **Answer**
   
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task4.png?raw=true)
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task4-1.png?raw=true)

   - **Task:** Write a script that sets ACL permissions for a user on a given file, based on user input.

   **Answer**
   
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task4-2.png?raw=true)
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task4-2-1.png?raw=true)

8. **Understanding Sticky Bit, SUID, and SGID:**
   - Read about sticky bit, SUID, and SGID.
     - Sticky bit: Used on directories to prevent users from deleting files they do not own.
     - SUID (Set User ID): Allows users to run an executable with the permissions of the executable's owner.
     - SGID (Set Group ID): Allows users to run an executable with the permissions of the executable's group.
   - Task: Create examples demonstrating the use of sticky bit, SUID, and SGID, and explain their significance.

   **Answer**
   
     - Sticky bit:
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task5.png?raw=true)
     - SUID:
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task5-1.png?raw=true)
     - SGID:
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task5-2.png?raw=true)

10. **Backup and Restore Permissions:**
   - Task: Create a script that backs up the current permissions of files in a directory to a file.

   **Answer**
   
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task6.png?raw=true)
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task6-1.png?raw=true)

   - Task: Create another script that restores the permissions from the backup file.

   **Answer**
   
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task6-2.png?raw=true)
   ![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day06/image/task6-2-1.png?raw=true)
