Linux Shell
Most Linux distributions use Bash (Bourne Again Shell) as their default shell. However, the default shell displayed when you open the terminal depends on your Linux distribution.

pwd - print working directory
  - shows whatever directory you're currently in
ls - just like dir, displays contents in current directory
cat - used to read contents of a file.
  - cat filename.txt
grep - command used to search for any word or pattern inside a file
  grep THM dictionary.txt- use the grep command to search for the word "THM" inside a big text file. The output displays the specific line of that text file containing this word.
  grep thm-flag01-script /var/log/*.log - will search for the "flag" within all log files inside the /var/log directory... by using the "*"

echo $SHELL - in order to see which shell you're currently running
  cat /etc/shells - to list all available shells

  ### Bourne Again Shell (BASH)
    
   - Bash is a widely used shell with scripting capabilities.  
   - It offers a tab completion feature, which means if you are in the middle of completing a command, you can press the tab key on your keyboard. It will automatically complete the command           based on a possible match or give you multiple suggestions for completing it.  
   - Bash keeps a history file and logs all of your commands. You can use the up and down arrow keys to use the previous commands without typing them again. You can also type history to               display all your previous commands.

   ### Friendly Interactive Shell

Friendly Interactive Shell (Fish) is also not default in most Linux distributions. As its name suggests, it focuses more on user-friendliness than other shells. Some of the key features provided by fish are listed below:

   - It offers a very simple syntax, which is feasible for beginner users.
   - Unlike bash, it has auto spell correction for the commands you write.
   - You can customize the command prompt with some cool themes using fish.
   - The syntax highlighting feature of fish colors different parts of a command based on their roles, which can improve the readability of commands. It also helps us to spot errors with their unique colors.
   - Fish also provides scripting, tab completion, and command history functionality like the shells mentioned in this task.

### Z Shell

Z Shell (Zsh) is not installed by default in most Linux distributions. It is considered a modern shell that combines the functionalities of some previous shells. Some of the key features provided by zsh are listed below:

  -  Zsh provides advanced tab completion and is also capable of writing scripts.
  - Just like fish, it also provides auto spell correction for the commands.
  -  It offers extensive customization that may make it slower than other shells.
  -  It also provides tab completion, command history functionality, and several other features.

### Shell Script - set of commands that preform repetitive tasks
* Create a script - nano first_script.sh
- Every script should start from shebang. Shebang is a combination of some characters that are added at the beginning of a script, starting with #! followed by the name of the interpreter to use while executing the script. As we are writing our script in bash, let’s define it as the interpreter in the shebang.

* The script below displays a string on the screen: "Hey, what’s your name?” This is done by echo command. The second line of the script contains the code read name. read is used to take input from the user, and name is the variable in which the input would be stored. The last line uses echo to display the welcome line for the user, along with its name stored in the variable.

- # Defining the Interpreter 
#!/bin/bash
echo "Hey, what’s your name?"
read name
echo "Welcome, $name"

chmod +x first_script.sh - gives execution permissions to the script

### Loops

#Defining the Interpreter 
#!/bin/bash
for i in {1..10};
do
echo $i
done

The first line has the variable i that will iterate from 1 to 10 and execute the below code every time. do indicates the start of the loop code, and done indicates the end. In between them, the code we want to execute in the loop is to be written. The for loop will take each number in the brackets and assign it to the variable i in each iteration. The echo $i will display this variable’s value every iteration.
  - will display 1 through 10 in descending order, when running the script

### Conditional Statements

#Defining the Interpreter 
#!/bin/bash
echo "Please enter your name first:"
read name
if [ "$name" = "Stewart" ]; then
        echo "Welcome Stewart! Here is the secret: THM_Script"
else
        echo "Sorry! You are not authorized to access the secret."
fi

The above script takes the user’s name as input and stores it into a variable (studied in the Variables section). The conditional statement starts with if and compares the value of that variable with the string Stewart; if it’s a match, it will display the secret to the user, or else it will not. The fi is used to end the condition.

### Creating a "locker script"

# Defining the Interpreter 
#!/bin/bash 

# Defining the variables
username=""
companyname=""
pin=""

# Defining the loop
for i in {1..3}; do
# Defining the conditional statements
        if [ "$i" -eq 1 ]; then
                echo "Enter your Username:"
                read username
        elif [ "$i" -eq 2 ]; then
                echo "Enter your Company name:"
                read companyname
        else
                echo "Enter your PIN:"
                read pin
        fi
done

# Checking if the user entered the correct details
if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
        echo "Authentication Successful. You can now access your locker, John."
else
        echo "Authentication Denied!!"
fi

