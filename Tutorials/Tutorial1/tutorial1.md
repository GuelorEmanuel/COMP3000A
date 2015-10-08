#Note to self :
	Write a problem that pulls the most recent tutorial text from the prof website and places it on txt file.

	In this tutorial you will be learning about 1) the difference between system calls, function calls, and library calls and 2) how processes are created.

#Function calls, library calls, and sytem calls

1.Compile the program prog.c using gcc -O2 prog.c -o prog-dyn and run prog-dyn. What does it do? 

2. Statically compile and optimize prog.c by running gcc -O2 -static prog.c -o prog-static. How does the size compare with prog?  

3.See what system calls prog-static produces by running strace -o syscalls-static.log ./prog-static. Do the same for prog-dyn. Which version generates more system calls?

4.See what library calls prog-static produces by running ltrace -o library-static.log ./prog-static. Do the same for prog-dyn. Which version generates more library calls? (If ltrace "is't" installed, run sudo apt-get install ltrace) 

5.	Using the nm command, see what symbols are defined in prog-static and prog-dyn. 

6.	Run the command gcc -c -O2 prog.c to produce an object file. What file was produced? What symbols does it define?

7.	Look at the assembly code of the program by running gcc -S -O2 prog.c. What file was produced? Identify the following:

    A function call
    A system call (if any)
    A global/static variable (if any)
    A local variable 

8.	Disassemble the object file using objdump -d. How does this disassembly compare with the output from gcc -S? 

9.	Examine the headers of object file, dynamically linked executable, and the statically linked executable using objdump -h

10.	Examine the contents of object file, dynamically linked executable, and the statically linked executable using objdump -s

11.	Re-run all of the previous gcc commands adding the '"-v"' flag. What is all of that output? 

12.	 (optional) Look up the documentation for each of the system calls made by the static versions of the programs. You may need to append a 2 or 3 to the manpage invocation, e.g. '"man 2 write"' gets you the write system call documentation. 


#Creating processes, running executables:

	For this part you will be playing with and modifying csimpleshell.c by Enrico Franchi. The source is also listed below. 

1.	 In csimpleshell, change the prompt to be the current user (e.g., '"student $"'), as reported by the USER environment variable. 

2.	 Make csimpleshell not call wait() on the command if there is an & as the last argument to a command; instead, just return another prompt. Can you see the zombies that are now produced? 

3.	Change the execp() call to execve(). Where do you get the extra argument? (NOTE: When you switch to execve() you will have to specify the full path to commands, e.g. /bin/ls not ls.) 

4.	Add an environment variable called LASTCOMMAND that contains the last command that was executed by csimpleshell. This environment variable should be passed on to each new program that is run. How can you check that your code works? 

5.	Use sigaction() and waitpid() to create a signal handler for SIGCHLD that prevents the creation of zombies for background commands. 

6.	(Advanced) Implement I/O redirection for STDIN (<) and STDOUT (>). Do the same for arbitrary file descriptors (e.g., 2>).

