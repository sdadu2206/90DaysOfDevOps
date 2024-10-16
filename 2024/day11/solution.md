# Day 11 Answers: Error Handling in Shell Scripting

## Learning Objectives
Understanding how to handle errors in shell scripts is crucial for creating robust and reliable scripts. Today, you'll learn how to use various techniques to handle errors effectively in your bash scripts.

## Topics to Cover
1. **Understanding Exit Status**: Every command returns an exit status (0 for success and non-zero for failure). Learn how to check and use exit statuses.
2. **Using `if` Statements for Error Checking**: Learn how to use `if` statements to handle errors.
3. **Using `trap` for Cleanup**: Understand how to use the `trap` command to handle unexpected errors and perform cleanup.
4. **Redirecting Errors**: Learn how to redirect errors to a file or `/dev/null`.
5. **Creating Custom Error Messages**: Understand how to create meaningful error messages for debugging and user information.

## Tasks with Answers

### Task 1: Checking Exit Status
- Write a script that attempts to create a directory and checks if the command was successful. If not, print an error message.

**Answer**

![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day11/image/task1.png?raw=true)

### Task 2: Using `if` Statements for Error Checking
- Modify the script from Task 1 to include more commands (e.g., creating a file inside the directory) and use `if` statements to handle errors at each step.

**Answer**

![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day11/image/task2.png?raw=true)

### Task 3: Using `trap` for Cleanup
- Write a script that creates a temporary file and sets a `trap` to delete the file if the script exits unexpectedly.

**Answer**

![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day11/image/task3.png?raw=true)

### Task 4: Redirecting Errors
- Write a script that tries to read a non-existent file and redirects the error message to a file called `error.log`.

**Answer**

![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day11/image/task4.png?raw=true)

### Task 5: Creating Custom Error Messages
- Modify one of the previous scripts to include custom error messages that provide more context about what went wrong.

**Answer** 

![image](https://github.com/sdadu2206/90DaysOfDevOps/blob/master/2024/day11/image/task5.png?raw=true)

## Example Scripts

### Example 1: Checking Exit Status
```bash
#!/bin/bash

mkdir /path/to/directory
if [ $? -eq 0 ]; then
    echo "Directory created successfully."
else
    echo "Error: Failed to create the directory."
fi
```

### Example 2: Trap
```bash
#!/bin/bash

temp_file=$(mktemp)
trap "rm -f $temp_file; echo 'Temporary file deleted on exit.'" EXIT

echo "Working with temp file: $temp_file"

# Simulating some work
sleep 5

echo "Script completed. Temporary file will be deleted."
```

### Example 3: Redirecting Errors
```bash
#!/bin/bash

cat /path/to/nonexistentfile 2> error.log

echo "Error message; Check error.log for details."
```

### Example 4: Custom Error Messages
```bash
#!/bin/bash

mkdir /path/to/directory 2> /dev/null
if [ $? -ne 0 ]; then
    echo "Custom Error: Directory creation failed. Check if the directory already exists or if you have sufficient permissions." 
    exit 1
fi

touch /path/to/directory/file.txt 2> /dev/null
if [ $? -ne 0 ]; then
    echo "Custom Error: File creation failed inside the directory. Ensure the directory exists and you have write permissions."
    exit 1
fi

echo "Script completed successfully."
```

[LinkedIn](https://www.linkedin.com/in/sdadu2206/)
