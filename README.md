# Custom Shell Implementation

This project is a basic implementation of a custom shell in C. The shell allows users to execute built-in commands, run external programs, and utilize input/output redirection. It also includes support for running a custom program called `fact`.

## Features
- **Built-in Commands**:
  - `cd <directory>`: Change the current working directory.
  - `exit`: Exit the shell.
  - `help`: Display usage instructions for the shell.
  - `tree`: Display the process tree.
- **External Command Execution**:
  - Execute external commands such as `ls`, `pwd`, and custom programs like `fact`.
- **I/O Redirection**:
  - Redirect input using `< input_file`.
  - Redirect output using `> output_file`.
- **Support for `fact` Command**:
  - A custom program (`fact`) can be executed to calculate the factorial of a given number.

---

## File Descriptions
- **`shell.c`**: Contains the implementation of the custom shell.
- **`fact.c`**: A program that calculates the factorial of a number.

---

## How to Use

### Compilation
Compile the programs using the following commands:
```bash
gcc -o output shell.c
gcc -o output2 fact.c
```

## Running the Shell
Run the make executable:
```bash
make
```

## Commands and Functionalities
### 1. Built-in Commands
```bash
cd <directory>
```
Changes the current working directory to the specified path.
If no directory is provided, the shell changes to the home directory.
exit
Terminates the shell.
```bash
help
```
Displays a help message explaining the shell's capabilities.
```bash
tree
```
Displays the process tree using the pstree command.

### 2. External Commands
The shell can execute external commands like ls, pwd, and more.
Commands are executed by forking a child process and using execvp().

### 3. I/O Redirection
Redirect input or output using:
< input_file: Redirects standard input to a file.
> output_file: Redirects standard output to a file.
Example:
```bash
$ ls > output.txt
```

### 4. Custom Commands
```bash
fact
```
Calculates the factorial of a given number.
Example:
```bash
$ fact 10
```

## Code Explanation
1. input_parser
Parses the user's input into arguments for command execution.

2. IO_redirection
Handles input and output redirection by manipulating file descriptors using dup2().

3. exec_command
Executes external commands or the fact program using fork() and execvp().

4. builtin_handler
Handles built-in commands like cd, exit, help, and tree.

5. process_tree
Executes the pstree command to display the process tree.
Open new terminal and follow this command
```bash
watch -n 1 "pstree -p | grep output"
```

![Screenshot 2025-01-27 002944](https://github.com/user-attachments/assets/3edfbd01-9e0b-4452-be76-a1b729e28bdd)
![Screenshot 2025-01-27 003001](https://github.com/user-attachments/assets/eb1be658-a8eb-43e7-8fab-c64d43790a36)


7. main
The main loop of the shell:

Prompts the user for input.
Parses the input and determines whether to handle it as a built-in or external command.
