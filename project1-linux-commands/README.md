# Introduction to Linux and Its Commands
Linux is an open-source operating system kernel that serves as the foundation for various Unix-like operating systems. Known for its stability, security, and flexibility, Linux has become a popular choice for servers, embedded systems, and desktop environments.

Linux commands are essential tools for interacting with the operating system. They provide users with the ability to navigate the file system, manage processes, configure system settings, and perform a wide range of tasks. Understanding Linux commands is crucial for both beginners and experienced users, as it empowers efficient system administration and customization. This project will cover fundamental commands to help users navigate and harness the power of Linux effectively.

## 1. sudo command
The `sudo` command in Linux allows a permitted user to execute a command as the superuser or another user, as specified by the security policy. It is commonly used to perform administrative tasks that require elevated privileges. for example: `sudo apt upgrade`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/sudo-command.png)

## 2. pwd command
The `pwd` (print working directory) command in Linux and Unix-like operating systems displays the current working directory, showing the full path to the directory you are currently in.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/pwd.png)

## 3. cd command
The `cd` (change directory) command in Linux is used to navigate between directories, allowing users to change their current working directory. Simply type `cd <directoryname>` or `cd /path/to/directory`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/cd-command.png)

## 4. ls command
The `ls` command in Linux is used to list the files and directories in the current working directory. The `ls` command default is to list all the files and subdirectories within a directory. However there are somany options you can attach to `ls`. For example:
- `ls -a`: list all the files including the hidden files
- `ls -l`: list all the file information including the permissions dates and owner
- To learn more about the options use `man ls` or `info ls`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/ls-command.png)

## 5. cat command
The cat command in Linux is used to concatenate and display the contents of files. It is also frequently used to create, append, and display the contents of files.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/cat-command.png)

## 6. cp command
The `cp` command in Linux is used to copy files and directories. you can copies files within the same directory or copy from one directory to another.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/cp-command.png)

**Note:** To copy a directory and its contents recursively, use `cp -r sourcedirectory destination` (the -r is for recursive)

## 7. mv command
The `mv` command in Linux is used to move or rename files and directories.

- `mv sourcefile destination` moves a file to a specified destination or renames the file if the destination is within the same directory.
- `mv sourcedirectory destination` moves a directory to a specified destination or renames the directory if the destination is within the same parent directory.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/mv-command.png)

## 8. mkdir command
The mkdir command in Linux  is used to create new directories (folders).

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/mkdir-command.png)
