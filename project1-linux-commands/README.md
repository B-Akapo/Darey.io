# Table Of Content
1. [Introduction](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands#introduction-to-linux-and-its-commands)

2. [File Manipulation](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands#file-manipulation)

   - [sudo command](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands#1-sudo-command)
   - [pwd command](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands#2-pwd-command)
   - [cd command](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands#3-cd-command)
   - [ls command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#4-ls-command)
   - [cat command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#5-cat-command)
   - [cp command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#6-cp-command)
   - [mv command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#7-mv-command)
   - [mkdir command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#8-mkdir-command)
   - [rmdir command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#9-rmdir-command)
   - [rm command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#10-rm-command)
   - [touch command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#11-touch-command)
   - [locate command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#12-locate-command)
   - [find command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#13-find-command)
   - [grep command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#14-grep-command)
   - [df command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#15-df-command)
   - [du command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#16-du-command)
   - [head command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#17-head-command)
   - [tail command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#18-tail-command)
   - [diff command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#19-diff-command)
   - [tar command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#20-tar-command)

3. [File Permissions and Ownership](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands#file-permissions-and-ownership)
   - [chmod command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#21-chmod-command)
   - [chown command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#22-chown-command)
   - [jobs command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#23-jobs-command)
   - [kill command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#24-kill-command)
   - [ping command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#25-ping-command)
   - [weget command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#26-weget-command)
   - [uname command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#27-uname-command)
   - [top command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#28-top-command)
   - [history command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#29-history-command)
   - [man command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#30-man-command)
   - [echo command](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/README.md#31-echo-command)

4. [Conclusion]()

#
# Introduction to Linux and Its Commands
Linux is an open-source operating system kernel that serves as the foundation for various Unix-like operating systems. Known for its stability, security, and flexibility, Linux has become a popular choice for servers, embedded systems, and desktop environments.

Linux commands are essential tools for interacting with the operating system. They provide users with the ability to navigate the file system, manage processes, configure system settings, and perform a wide range of tasks. Understanding Linux commands is crucial for both beginners and experienced users, as it empowers efficient system administration and customization. This project will cover fundamental commands to help users navigate and harness the power of Linux effectively.

# File Manipulation

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
The mkdir command in Linux is used to create new directories (folders).

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/mkdir-command.png)

## 9. rmdir command
The `rmdir` command in Linux  is used to remove empty directories.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/rmdir-command.png)

## 10. rm command
The rm command in Linuxis used to remove files and directories(that are not empty). The remove a non- empty directory, you use `rm -r`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/rm-command.png)

## 11. touch command

The `touch` command in Linux is used to create empty files or update the timestamp of existing files.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/touch-command.png)

## 12. locate command
The `locate` command in Linux is used to find the path of files and directories by searching an index/database of the file system.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/locate-command.png)

## 13. find command
The `find` command in Linux is used to search for files and directories within a specified directory hierarchy based on various criteria.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/find-command.png)

## 14. grep command
The `grep` command in Linux is used to search for specific patterns within files or streams of text, enabling filtering based on regular expressions.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/grep-command.png)

**Note:** You can recursively search for the "pattern" within all files in the specified directory and its subdirectories using `grep -r "pattern" /path/to/directory`

## 15. df command
The `df` command in Linux is used to display disk space usage information for filesystems.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/df-command.png)

## 16. du command
The `du` command in Linux is used to estimate file and directory space usage.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/du-command.png)

## 17. head command
The `head` command in Linux is used to display the first 10 fines of a file by default.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/head-command.png)

**Note:** To display a specified number of lines use `head -n 10 filename` (Replace 10 with the desired number of lines.)

## 18. tail command
The tail command in Linux is used to display the ending part of files, typically the last 10 lines.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/tail-command.png)

**Note:** To display a specified number of lines use `tail -n 10 filename` (Replace 10 with the desired number of lines.)

## 19. diff command
The `diff` command in Linux is used to compare and show the differences between two files line by line.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/diff-command.png)

## 20. tar command
The tar command in Linux is used to create, view, extract, or manipulate tar archives, which are collections of files and directories bundled together into a single file. to create a **.tar** file, use `tar -cvf archive.tar files/directories`. To extract the files use `tar -xvf archive.tar`

# File Permissions and Ownership

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/tar-command.png)

## 21. chmod command
The `chmod` command in Linux is used to change the permissions (read, write, execute) of files and directories.It uses symbolic or numeric representation to modify permissions, allowing users to control who can read, write, and execute files and directories.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/chmod-command.png)

## 22. chown command
The `chown` command in Linux is used to change the ownership of files and directories. For example:

- To change ownership of a file or directory use `chown newowner filename/directoryname`. Replace `newowner` with the new owner's username or user ID and filename/directoryname with the target file or directory.

`chown user1 file.txt` changes the owner of the file `file.txt` to `user1`.

## 23. jobs command
The `jobs` command in Unix-like operating systems is used to list the current jobs running in the background or suspended in the current shell session.

`# List current jobs
jobs`

Running `jobs` displays a list of all background jobs spawned from the current shell session, along with their job IDs and status information. This command is particularly useful when multiple processes are running concurrently in the background, allowing users to monitor and manage them.

## 24. kill command
The `kill` command in Linux is used to terminate processes by sending a signal to a specified process ID (PID) or job.

**Code snippet example:**
```
# Terminate a process by PID
kill PID

# Forcefully terminate a process by PID
kill -9 PID
```

Replace PID with the process ID of the target process.

- The first example (kill PID) sends the default **SIGTERM** signal to the specified process, allowing it to perform cleanup before termination.
- The second example (kill -9 PID) sends the **SIGKILL** signal, forcibly terminating the specified process without allowing it to perform any cleanup tasks. Use this cautiously as it immediately ends the process.

`kill` provides a means to manage running processes by stopping or ending them based on their process IDs.


## 25. ping command
The `ping` command in Linux is used to test network connectivity by sending ICMP echo request packets to a target host and waiting for replies. For example `ping google.com`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/ping-command.png)

## 26. weget command
The `wget` command in Linux is used to retrieve files from the internet via various protocols, including HTTP, HTTPS, FTP, and more.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/weget-command.png)

**Note:** 
- To download a zipped file from a specified url use `wget https://example.com/file.zip`
- `wget -O output_file https://example.com/file` downloads the file from the URL and saves it with the specified name output_file.

## 27. uname command
The `uname` command in Linux is used to display system information, including the system name, kernel version, hardware architecture, and more.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/uname-command.png)

Some options to use for `uname` are:
- `uname -a` provides comprehensive system information, including the kernel name, network node hostname, kernel release, kernel version, machine hardware name, and the operating system
- `uname -s` is used to display the operating system name
- is used to display the network node hostname of the system. It retrieves and displays the name assigned to the system on the network.

## 28. top command
The `top` command in Linux is used to display system processes in real-time, providing a dynamic, interactive view of system resource usage. Running `top` in the terminal presents a live, updating list of processes, showing information such as CPU usage, memory usage, process IDs (PIDs), running time, and more. It's a powerful tool for monitoring system performance and identifying resource-intensive processes.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/top-command.png)

## 29. history command
The `history` command in Linux is used to display a list of previously executed commands in the current shell session.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/history-command.png)

## 30. man command
The `man` command in Linux is used to display the manual pages (documentation) for various commands and functionalities within the system. For example `man ls` will give you the manual for the `ls` command

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/man-command.png)

## 31. echo command
The `echo` command in Linux is used to display text or variables to the terminal or standard output.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/echo-command1.png)

`echo` can also be used to create a new file like the `touch` commmand. However, the files created by `echo` are not empty. that makes it different from `touch`. To use te echo command type `echo "<string>" > filename`. Becareful though, using echo again on the same file will overwrite what you previously saved. To avoid this use `echo "<string>" >> filename`. `>>` appends the new content to the last line instead of overwriting the whole file. 

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/echo-command2.png)

## 32. zip and unzip command
The `zip` command in Linux is used to compress files into a ZIP archive format. While `unzip` is used to extract files from a ZIP archive.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/zip-unzip-command.png)

## 33. hostname command
The `hostname` command in Linux is used to display or set the system's hostname.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/hostname-command.png)

## 34. useradd, userdel command
The `useradd` command in Linux is used to add new user accounts to the system. While `userdel` command is used to delete user accounts from the system.

I'd advice you to check the list of users first. you cando this using `cut -d: -f1 /etc/passwd`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/useradd-command1.png)

In the screenshot you can see my useer name `bunmi`. To add a new user run the command `useradd <username>` (replace username with the desired name). if you are not running the command as a root user then you will need to use `sudo useradd <username>`. To give you new user a password run the command `sudo passwd <username>`. You will be prompter to enter the new password twice

Once you have created the new user you can run `cut -d: -f1 /etc/passwd` to see the new added user. In the screenshot below you can see i added `guest` as the new user. 

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/useradd-command2.png)

To delete and existing user is easy. Simply run the command `userdel <username>`. If you aren't running the command as a root user, then you will need to run `sudo userdel <username>`. By default, the `userdel` command will remove the user from the system account files, deleting all entries that refer to the username. However, it will not delete the user's home directory or mail spool. If you want to remove the user's home directory and mail spool as well, you can use `sudo userdel -r <username>`

## 35. apt-get command
The `apt-get` command in Debian-based Linux distributions is used to manage software packages. It allows users to install, update, upgrade, and remove packages from the system. In the screenshot below you can see me using `apt-get` to instal `jed` package

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/apt-get-command.png)

You can also use `apt-get` to:
- Update the local package index by downloading the latest package lists from the repositories. This can be done using `sudo apt-get update`
- Upgrade installed packages to their latest versions. This can be done by running `sudo apt-get upgrade`

## 36. nano, vi, jed command
**Nano** is a simple and user-friendly text editor often favored by beginners for its straightforward interface and keybindings. To use nano, you run `nano <filename>` (replace filename with the name of your file). 

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/nano-command.png)

Once in nano text editor, you can exit using `Ctrl + X`, you will be asked if you want to save or not enter `Y` for yes and `N` for no. 

**vi (or vim)** is a powerful and widely used text editor with a steep learning curve but efficient once mastered. Vim is an improved version of Vi. To use vi, you run `vi <filename>` (replace filename with the name of your file). 

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/vi-command.png)

To exit vi or vim you first make sure you are in command mode by pressing the Esc key. Then you can:
- Type `:q!` and press Enter to quit without saving any changes. This command discards any modifications made to the file.
- Type `:wq` and press Enter to save the changes and quit. This command writes the changes to the file before exiting.
- Alternatively, you can use the shortcut `Shift+zz` to save and quit. This command is equivalent to `:wq`.

**jed** is a lightweight text editor known for its extensibility and suitability for programming tasks. To use vi, you run `jed <filename>` (replace filename with the name of your file). 

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/jed-command.png)

To exit jed you first make sure you are in command mode by pressing the Esc key. Then you can:
- Type `:q` and press Enter to quit Jed without saving any changes. This command discards any modifications made to the file.
- Type `:wq` and press Enter to save the changes and quit Jed. This command writes the changes to the file before exiting.
- Alternatively, you can use the shortcut `Ctrl+X Ctrl+C` to exit Jed. This command is equivalent to `:wq`.

## 37. alias and unalias command
The `alias` command in Linux is used to create custom shortcuts or aliases for longer commands. The syntax for alias is `alias shortcut_name='longer_command`. For exampl

`alias b='bunmi'`

In this case the command is **bunmi** which is long. I have replaced it with a shorter alias **b**. This means any time i want to run the command, I can simply type **b**

The `unalias` command removes previously defined aliases, reverting them to their original command form. THe syntaxt is `unalias shortcut_name`. Using our example about, to revert to using **bunmi** as my command i simply run 

`unalias b`

## 38. su command
The `su` command in Linux is used to switch users or assume the identity of another user. The syntax is `su <username>`

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/su-command.png)

To switch back to the original user, use the same command `su <username>` or simply type `exit`

## 39. htop command
The `htop` command in Linux is an interactive process viewer, providing a more user-friendly and feature-rich alternative to the traditional `top` command. Running `htop` in the terminal launches an interactive, color-coded process manager displaying system resource usage, CPU, memory, and a list of processes, allowing users to manage and monitor processes in a more intuitive manner. 

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/htop-command.png)

To exit the htop screen, simply run `Ctrl + X`

## 40. ps command
The `ps` command in Linux is used to display information about active processes. Running `ps ` without any flags or arguments shows a snapshot of currently running processes on the system. The ps command offers various options to display specific information about processes, such as their IDs, states, resource usage, and more, depending on the specified flags.

![Alt Text](https://github.com/B-Akapo/Darey.io/blob/main/project1-linux-commands/images/ps-command.png)

# Conclusion
Linux commands cover a wide spectrum, from navigation and file manipulation to system monitoring and administration. They form a robust toolkit, offering options for:
- File management (**ls, cp, mv**),
- System insights (**top, htop, ps**),
- user management (**useradd, userdel, su**).
- Software management (**apt-get, wegt**)
- File management (**chmod, chown, namo, vi, jed**) and
- Utility management (**tar, zip, and unzip**)

With Linux, there's a command for almost every task, offering flexibility and efficiency in managing Linux systems, you just need to take time to learn and practice them








