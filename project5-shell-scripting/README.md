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

![Alt text](create-directory.png)

**Step 2: Create An Empty File**
- To create and empty file run the command
```
touch user-input.sh
```
Shell script files always have an `.sh` extention. 
- To be sure your file has been created, you can run the `ls` command

![Alt text](ls-command.png)

**Step 3: Change Permisiion**
- For your script to run, it needs executable permission. Use the `chmod` command to grant this permission. This command allows the file to be executed as a program.
```
chmod +x user-input.sh
```

![Alt text](chmod.png)

**Step 4: Writing Your Script**
- Open your file in your choosen editor. I will be using vim
```
vim user-input.sh
```
- Add a `shebang` at the top of your file. The `shebang`, also known as a hashbang, is a special sequence of characters `(#!)` at the beginning of a script followed by the path to the interpreter that should execute the script. This line tells the system which interpreter should be used to execute the script—in this case, the Bash shell. Note that the shebang syntax is `#! <pathway/to/bash>`. To know where your bash is located simply rn `which bash` in your terminal

![Alt text](bash.png)

![Alt text](shebang.png)

- Let's write a script that allows the user to input an answer
```
# Prompt user for their name
read -p "Enter your name: " NAME

# Greet user using their name
echo "Hello $NAME. Nice to meet you"
```

![Alt text](user-input.png)

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

![Alt text](first.png)







