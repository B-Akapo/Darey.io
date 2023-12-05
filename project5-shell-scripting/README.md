# Introduction
In the world of computing, efficiency is key. Enter shell scripting—a powerful toolset that unlocks the potential of the command line interface. If you're new to shell scripting, you're about to discover a world where automation and customization reign supreme.

# What is Shell Scripting?
At its core, shell scripting involves writing a series of commands in a plain text file that can be executed by the command line interpreter, or "shell." These scripts are incredibly versatile, allowing you to combine multiple commands, logic, variables, and control structures to perform tasks or automate workflows. These scripts act as a bridge between human-readable instructions and the system's ability to perform tasks swiftly and accurately.

# Why Use Shell Scripts?
Shell scripting offers several advantages:
- **Automation:** Repetitive tasks become a breeze with scripts, saving time and reducing human error.
- **Customization:** You have full control over how commands are executed, allowing for tailored solutions.
- **Portability:** Shell scripts are compatible across different Unix-based systems, providing flexibility.

# Writing Your First Script
**Step 1: Create A Directory In Your Terminal**
- If you dont know much about linux and navigating through it using the Command Line Interface (CLI), you can quickly brush up using the documnetation [here](https://github.com/B-Akapo/Darey.io/tree/main/project1-linux-commands)
- Use `mkdir` command to create a new directory and `cd` into the directory
```
mkdir shell-scripting; cd shell-scripting
```
Note: I am calling my directory `shell-scripting`. Feel free to name it whatever you want. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/create-directory.png)

**Step 2: Create An Empty File**
- To create and empty file run the command
```
touch user-input.sh
```
Shell script files always have an `.sh` extention. 
- To be sure your file has been created, you can run the `ls` command

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/ls-command.png)

**Step 3: Change Permisiion**
- For your script to run, it needs executable permission. Use the `chmod` command to grant this permission. This command allows the file to be executed as a program.
```
chmod +x user-input.sh
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/chmod.png)

**Step 4: Writing Your Script**
- Open your file in your choosen editor. I will be using vim
```
vim user-input.sh
```
- Add a `shebang` at the top of your file. The `shebang`, also known as a hashbang, is a special sequence of characters `(#!)` at the beginning of a script followed by the path to the interpreter that should execute the script. This line tells the system which interpreter should be used to execute the script—in this case, the Bash shell. Note that the shebang syntax is `#! <pathway/to/bash>`. To know where your bash is located simply rn `which bash` in your terminal

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/bash.png)

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/shebang.png)

- Let's write a script that allows the user to input an answer
```
# Prompt user for their name
read -p "Enter your name: " NAME

# Greet user using their name
echo "Hello $NAME. Nice to meet you"
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/user-input.png)

a. `read`: This command reads input from the user.

b. `-p "Enter your name: "`: This flag prompts the user by displaying "Enter your name: " and waits for input.

c. `NAME`: This is a variable where the entered value will be stored.

So, when you run this script, it will display "Enter your name: " and wait for you to type your name. Once you hit Enter, it will store what you typed into the NAME variable.

d. `echo`: This command prints text to the terminal.

e. `"Hello $NAME. Nice to meet you"`: This string contains text and a reference to the NAME variable using the $ sign followed by the variable name.

After you input your name, this line will display a greeting that includes the name you entered. For example, if you entered "John," it would print: "Hello John. Nice to meet you."

**Step 5: Run Your Script**
- Save your file. If you are using `vim` like me. Ensure you first hit `Esc` then type `:wq` to save. If you have any troubles exiting `vim`, you can use this [video](https://www.youtube.com/watch?v=KwCvEVblJl8)
- Now run your script using the command
```
./user-inut.sh
```
You should get a prompt asking you to enter your name. Once you enter your name you should see your greeting. Well done, you have written you first script. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/first.png)

# Directory Manipulation and Navigation
Alright, now lets write a script that creates a directory, creates files in the directory, moves into the directory and deletes the directory. Don't worry it seems like a lot but it isnt. Let's start

**Step 1: Create An Empty File**
- To create an empty file, run the command
```
touch navigating-linux-filesystem.sh
```
Remember, you can name your file whatever you want. Run `ls` command to see if your file has been created

![Alt text](new-file.png)

**Step 2: Give the file Permission**
- To make your file executable you need to give it the right permission
```
chmod +x navigating-linux-filesystem.sh 
```

**Step 3: Add A Shebang in the file**
- Open the file with your choosen editor
```
vim navigating-linux-filesystem.sh
```
- For the system to know to run your file as a program, it must have a `shebang`.
```
#! /usr/bin/bash
```

**Step 4: Write a script that displays the current directory**
```
#! /usr/bin/bash

# Display the Current Directory
echo "Current Directory: $PWD"
```
Note that the variable `$PWD` already exists in your system. So you dont need to declare it. 

**Step 5: Write a script to create a new directory**
```
#! /usr/bin/bash

# Display the Current Directory
echo "Current Directory: $PWD"

# Let user know a new directory is being created
echo "Creating a new directory..."

# Create a new directory
mkdir my_directory

# Let user know directory is created
echo "New directory created..."
```

**Step 6: Change into new directory**
```
#! /usr/bin/bash

# Display the Current Directory
echo "Current Directory: $PWD"

# Let user know a new directory is being created
echo "Creating a new directory..."

# Create a new directory
mkdir my_directory

# Let user know directory is created
echo "New directory created..."

# Let user know you are switching directory
echo "Changing directory..."

# Change into new directory
cd my_directory

# Display the Current Directory
echo "Current Directory: $PWD"
```
**Step 7: Create files in the new directory**
```
#! /usr/bin/bash

# Display the Current Directory
echo "Current Directory: $PWD"

# Let user know a new directory is being created
echo "Creating a new directory..."

# Create a new directory
mkdir my_directory

# Let user know directory is created
echo "New directory created..."

# Let user know you are switching directory
echo "Changing directory..."

# Change into new directory
cd my_directory

# Display the Current Directory
echo "Current Directory: $PWD"

# Let users know you are creating some file
echo "Creating files..."

# Create two new files
touch file1.txt
touch file2.txt

# Let users know the files have been created
echo "Files created..."

# List the files in the current directory
ls
```
**Step 8: Move one level up**
```
#! /usr/bin/bash

# Display the Current Directory
echo "Current Directory: $PWD"

# Let user know a new directory is being created
echo "Creating a new directory..."

# Create a new directory
mkdir my_directory

# Let user know directory is created
echo "New directory created..."

# Let user know you are switching directory
echo "Changing directory..."

# Change into new directory
cd my_directory

# Display the Current Directory
echo "Current Directory: $PWD"

# Let users know you are creating some file
echo "Creating files..."

# Create two new files
touch file1.txt
touch file2.txt

# Let users know the files have been created
echo "Files created..."

# List the files in the current directory
ls

# Let users kow you are moving one level up
echo "Moving one level up..."

# Move one level up
cd ..

# Display the Current Directory
echo "Current Directory: $PWD"
```
**Step 9: Remove/Delete Directory**
```
#! /usr/bin/bash

# Display the Current Directory
echo "Current Directory: $PWD"

# Let user know a new directory is being created
echo "Creating a new directory..."

# Create a new directory
mkdir my_directory

# Let user know directory is created
echo "New directory created..."

# Let user know you are switching directory
echo "Changing directory..."

# Change into new directory
cd my_directory

# Display the Current Directory
echo "Current Directory: $PWD"

# Let users know you are creating some file
echo "Creating files..."

# Create two new files
touch file1.txt
touch file2.txt

# Let users know the files have been created
echo "Files created..."

# List the files in the current directory
ls

# Let users kow you are moving one level up
echo "Moving one level up..."

# Move one level up
cd ..

# Display the Current Directory
echo "Current Directory: $PWD"

# Let users know you are removing directory
echo "Removing the new directory"

# Remove directory
rm -rf my_directory

# Confirm directory has been remove
echo "Directory removed!"

# show the files in the current directory
echo "Files in the current directory: "
ls
```
Your script is done now save your file.  Hit `Esc` and the type `:wq` to save and exit

**Step 10: Run your file**
```
./navigating-linux-filesystem.sh
```

![Alt text](navigate.png)














