## Table of Contents

1. [Introduction](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#introduction)
2. [What is Shell Scripting?](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#what-is-shell-scripting)
3. [Why Use Shell Scripts?](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#why-use-shell-scripts)
4. [Writing Your First Script](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#writing-your-first-script)
5. [Directory Manipulation and Navigation](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#directory-manipulation-and-navigation)
6. [File Operations And Sorting](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#file-operations-and-sorting)
7. [Working With Numbers And Calculations](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#working-with-numbers-and-calculations)
8. [File Backup And Time Stamping](https://github.com/B-Akapo/Darey.io/tree/main/project5-shell-scripting#file-backup-and-time-stamping)
#

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

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/new-file.png)

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

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/navigate.png)

# File Operations And Sorting
Now lets try writing a script that creates a set of files and the sorts them in a certain order.

**Step 1: Create a new file**
- In the same directory create a new file
```
touch sorting.sh
```
Remember, you can name your file whatever you want. Run `ls` command to see if your file has been created

**Step 2: Give the file Permission**
- To make your file executable you need to give it the right permission
```
chmod +x sorting.sh
```
**Step 3: Add A Shebang in the file**
- Open the file with your choosen editor
```
vim sorting.sh
```
- For the system to know to run your file as a program, it must have a `shebang`.
```
#! /usr/bin/bash
```
**Step 4: Create your files**
```
#! /usr/bin/bash

# Let users know you are creating files
echo "Creating files..."

# Create 3 files
echo "This is file3." > file3.txt
echo "This is file1." > file1.txt
echo "This is file2." > file2.txt

# Let users know the file has been created. The first echo creates and empty line for aesthetics
echo " "
echo "Files created"

# Display the files in their current order
echo " "
echo "Files in their current order"
ls
```
**Step 5: Sort Filesk Alphabetically**
```
#! /usr/bin/bash

# Let users know you are creating files
echo "Creating files..."

# Create 3 files
echo "This is file3." > file3.txt
echo "This is file1." > file1.txt
echo "This is file2." > file2.txt

# Let users know the file has been created. The first echo creates and empty line for aesthetics
echo " "
echo "Files created"

# Display the files in their current order
echo " "
echo "Files in their current order"
ls

# Let users know you are sorting files
echo " "
echo "Now sorting in alphabetical order

# Sort the files into a new file
ls | sort > sorted_files.txt

# Let users know the files have been sorted
echo "Files sorted..."

# Display sorted files
echo " "
echo "Sorted files: "
cat sorted_files.txt
```
**Step 6: Remove the new files created**
```
#! /usr/bin/bash

# Let users know you are creating files
echo "Creating files..."

# Create 3 files
echo "This is file3." > file3.txt
echo "This is file1." > file1.txt
echo "This is file2." > file2.txt

# Let users know the file has been created. The first echo creates and empty line for aesthetics
echo " "
echo "Files created"

# Display the files in their current order
echo " "
echo "Files in their current order"
ls

# Let users know you are sorting files
echo " "
echo "Now sorting in alphabetical order

# Sort the files into a new file
ls | sort > sorted_files.txt

# Let users know the files have been sorted
echo "Files sorted..."

# Display sorted files
echo " "
echo "Sorted files: "
cat sorted_files.txt

# Let users know you are removing files
echo " "
echo "Now removing files"

# Remove files
rm file1.txt file2.txt file3.txt

# Let users know that the files have been removed
echo "Files removed..."
```
**Step 7: Rename the existing sorted file**
```
#! /usr/bin/bash

# Let users know you are creating files
echo "Creating files..."

# Create 3 files
echo "This is file3." > file3.txt
echo "This is file1." > file1.txt
echo "This is file2." > file2.txt

# Let users know the file has been created. The first echo creates and empty line for aesthetics
echo " "
echo "Files created"

# Display the files in their current order
echo " "
echo "Files in their current order"
ls

# Let users know you are sorting files
echo " "
echo "Now sorting in alphabetical order

# Sort the files into a new file
ls | sort > sorted_files.txt

# Let users know the files have been sorted
echo "Files sorted..."

# Display sorted files
echo " "
echo "Sorted files: "
cat sorted_files.txt

# Let users know you are removing files
echo " "
echo "Now removing files"

# Remove files
rm file1.txt file2.txt file3.txt

# Let users know that the files have been removed
echo "Files removed..."

# Let users know you are renaming the file
echo " "
echo "Renaming files"

# Rename the files
mv sorted_files.txt files_sorted_alphabetically.txt

#Let users know the file has been renamed
echo "File renamed"

# Display the sorted file
echo " "
echo "Final sorted file"
cat files_sorted_alphabetically.txt
```
**Step 8: Run your file**
```
./sorting.sh
```
Viola it is done. Well done

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/sorting.png)

# Working With Numbers And Calculations
Scripts can also be used for aritmethics. Let's take a look at it.

**Step 1: Create a new file**
- In the same directory create a new file
```
touch calculations.sh
```
Remember, you can name your file whatever you want. Run `ls` command to see if your file has been created

**Step 2: Give the file Permission**
- To make your file executable you need to give it the right permission
```
chmod +x calculations.sh
```
**Step 3: Add A Shebang in the file**
- Open the file with your choosen editor
```
vim calculations.sh
```
- For the system to know to run your file as a program, it must have a `shebang`.
```
#! /usr/bin/bash
```
**Step 4: Create your files**
```
#! /usr/bin/bash

# Define two variables
NUM1=10
NUM2=5
```
**Step 5: Perform Arithmetic Operations**
```
#! /usr/bin/bash

# Define two variables
NUM1=10
NUM2=5

# Create variables for arithmetic operations
SUM=$((NUM1 + NUM2))
DIFFERENCE=$((NUM1 - NUM2))
PRODUCT=$((NUM1 * NUM2))
DIVISION=$((NUM1 / NUM2))
REMAINDER=$((NUM1 % NUM2))
```
**Step 6: Display Results**
```
#! /usr/bin/bash

# Define two variables
NUM1=10
NUM2=5

# Create variables for arithmetic operations
SUM=$((NUM1 + NUM2))
DIFFERENCE=$((NUM1 - NUM2))
PRODUCT=$((NUM1 * NUM2))
DIVISION=$((NUM1 / NUM2))
REMAINDER=$((NUM1 % NUM2))

#Display results
echo "Number 1: $NUM1"
echo "Number 2: $NUM2"
echo " "
echo "Sum: $SUM"
echo "Difference = $DIFFERENCE"
echo "Product = $PRODUCT"
echo "Remainder = $REMAINDER"
```
**Step 7: Perform Complex Arithmethic**
```
#! /usr/bin/bash

# Define two variables
NUM1=10
NUM2=5

# Create variables for arithmetic operations
SUM=$((NUM1 + NUM2))
DIFFERENCE=$((NUM1 - NUM2))
PRODUCT=$((NUM1 * NUM2))
DIVISION=$((NUM1 / NUM2))
REMAINDER=$((NUM1 % NUM2))

#Display results
echo "Number 1: $NUM1"
echo "Number 2: $NUM2"
echo " "
echo "Sum: $SUM"
echo "Difference = $DIFFERENCE"
echo "Product = $PRODUCT"
echo "Remainder = $REMAINDER"

# Perform some more complex calculations
power_of_2=$((num1 ** 2))
square_root=$(echo "sqrt($num2)" | bc)

# Display the results
echo " "
echo "Number 1 raised to the power of 2: $power_of_2"
echo "Square root of number 2: $square_root"
```
**Step 8: Run your file**
```
./calculations.sh
```

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/calculations.png)

# File Backup And Time Stamping
As a DevOps engineer, regular file and database backups are a routine and crucial responsibilityHaving a script that does that for you will make life a whole lot easier. Let us take a look at how to do it

**Step 1: Create a new file**
- In the same directory create a new file
```
touch backup.sh
```
Remember, you can name your file whatever you want. Run `ls` command to see if your file has been created

**Step 2: Give the file Permission**
- To make your file executable you need to give it the right permission
```
chmod +x backup.sh
```
**Step 3: Add A Shebang in the file**
- Open the file with your choosen editor
```
vim backup.sh
```
- For the system to know to run your file as a program, it must have a `shebang`.
```
#! /usr/bin/bash
```
**Step 4: Define the source directory**
```
#!/bin/bash

# Define the source directory and backup directory
source_dir="/home/bunmi/study/shell-scripting"
backup_dir="/home/bunmi/study/shell-scripting/backup_dir"
```
**Step 5: Create a timestamp**
```
#!/bin/bash

# Define the source directory and backup directory
source_dir="/home/bunmi/study/shell-scripting"
backup_dir="/home/bunmi/study/shell-scripting_backup"

# Create a timestamp with the current date and time
timestamp=$(date +"%Y%m%d%H%M%S")
```
**Step 6: Create a backup directory**
```
#!/bin/bash

# Define the source directory and backup directory
source_dir="/home/bunmi/study/shell-scripting"
backup_dir="/home/bunmi/study/shell-scripting_backup"

# Create a timestamp with the current date and time
timestamp=$(date +"%Y%m%d%H%M%S")

# Create a backup directory with the timestamp
backup_dir_with_timestamp="$backup_dir/backup_$timestamp"

# Create the backup directory
mkdir -p "$backup_dir_with_timestamp"
```
**Step 7: Copy Files**
```
#!/bin/bash

# Define the source directory and backup directory
source_dir="/home/bunmi/study/shell-scripting"
backup_dir="/home/bunmi/study/shell-scripting_backup"

# Create a timestamp with the current date and time
timestamp=$(date +"%Y%m%d%H%M%S")

# Create a backup directory with the timestamp
backup_dir_with_timestamp="$backup_dir/backup_$timestamp"

# Create the backup directory
mkdir -p "$backup_dir_with_timestamp"

# Copy all files from the source directory to the backup directory
cp -r "$source_dir"/* "$backup_dir_with_timestamp"

# Display a message indicating the backup process is complete
echo "Backup completed. Files copied to: $backup_dir_with_timestamp"
```
**Step 8: Run your file**
```
./backup.sh
```
Your file should now be backed up 

![Al text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/backup.png)

Let's quickly check. Run `ls` in your source directory and see the list of your file. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/source.png)

Now `cd` to you source directory and run `ls` to see the exact files. 

![Alt text](https://github.com/B-Akapo/Darey.io/blob/main/project5-shell-scripting/images/copy.png)



















