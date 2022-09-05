# This is a README with the description of this project

Group project - 0x16. C - simple_shell

//this project is about a Unix shell which is a command-line interpreter or shell that provides a command line user interface for Unix-like operating systems. The shell is both an interactive command language and a scripting language, and is used by the operating system to control the execution of the system using shell scripts.

# Background Context

A simple UNIX command interpreter.

#GENERAL context
* How a shell works
* What is a pid and a ppid
* How to manipulate the environment of the current process
* What is the difference between a function and a system call
* How to create processes
* The three prototypes of main
* How the shell uses the PATH to find the programs
* How to execute another program with the execve system call
* How to suspend the execution of a process until one of its children terminates
* Shows What EOF / “end-of-file” is

#Requirement satisfied
* Editors used: vi, vim, emacs
* All files are compiled on Ubuntu 20.04 LTS using gcc, using the options -Wall -Werror -Wextra -pedantic -std=gnu89
* All files end with a new line
* A README.md file, at the root of the folder of the project as mandatory
* All codes use the Betty style. It is checked using betty-style.pl and betty-doc.pl
* Shell does not have any memory leaks
* No more than 5 functions per file
* All header files are include guarded
* The use of system calls only when needed
* An AUTHORS file at the root of this repository, listing all individuals having contributed content to the repository.

# Output

	Unless specified otherwise, the program has the exact same output as sh (/bin/sh) as well as the exact same error output.
The only difference is when printing an error, the name of the program is equivalent to the argv[0]

# Example of error with sh:

	$ echo "qwerty" | /bin/sh
	/bin/sh: 1: qwerty: not found
	$ echo "qwerty" | /bin/../bin/sh
	/bin/../bin/sh: 1: qwerty: not found
	$

//Same error with your program hsh:

	$ echo "qwerty" | ./hsh
	./hsh: 1: qwerty: not found
	$ echo "qwerty" | ./././hsh
	./././hsh: 1: qwerty: not found
	$

# List of allowed functions and system calls

* access (man 2 access)
* chdir (man 2 chdir)
* close (man 2 close)
* closedir (man 3 closedir)
* execve (man 2 execve)
* exit (man 3 exit)
* _exit (man 2 _exit)
* fflush (man 3 fflush)
* fork (man 2 fork)
* free (man 3 free)
* getcwd (man 3 getcwd)
* getline (man 3 getline)
* getpid (man 2 getpid)
* isatty (man 3 isatty)
* kill (man 2 kill)
* malloc (man 3 malloc)
* open (man 2 open)
* opendir (man 3 opendir)
* perror (man 3 perror)
* read (man 2 read)
* readdir (man 3 readdir)
* signal (man 2 signal)
* stat (__xstat) (man 2 stat)
* lstat (__lxstat) (man 2 lstat)
* fstat (__fxstat) (man 2 fstat)
* strtok (man 3 strtok)
* wait (man 2 wait)
* waitpid (man 2 waitpid)
* wait3 (man 2 wait3)
* wait4 (man 2 wait4)
* write (man 2 write)
* #Compilation

//The shell is compiled this way:

	gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh

# Testing

//The shell works like this in interactive mode:

	$ ./hsh
	($) /bin/ls
	hsh main.c shell.c
	($)
	($) exit
	$

//But also in non-interactive mode:
	
	$ echo "/bin/ls" | ./hsh
	hsh main.c shell.c test_ls_2
	$
	$ cat test_ls_2
	/bin/ls
	/bin/ls
	$
	$ cat test_ls_2 | ./hsh
	hsh main.c shell.c test_ls_2
	hsh main.c shell.c test_ls_2
	$
