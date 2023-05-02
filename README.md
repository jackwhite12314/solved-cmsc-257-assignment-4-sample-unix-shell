Download Link: https://assignmentchef.com/product/solved-cmsc-257-assignment-4-sample-unix-shell
<br>






<strong>What is a shell? </strong>

<ul>

 <li>Command line interpreter – You type “ls /etc”

  <ul>

   <li>The shell invokes the first parameter as a command, with the remainder as the parameters – eg: exec(ls,”/etc”)</li>

  </ul></li>

 <li>Built-in commands

  <ul>

   <li>Most commands are separate executable programs</li>

  </ul></li>

 <li>ls, rm, mv, make, gcc

  <ul>

   <li>Some commands are interpreted by the shell • cd, exit, pid, ppid.</li>

  </ul></li>

</ul>




<h1>Interactive vs Batch</h1>

<ul>

 <li>Interactive

  <ul>

   <li>User types commands in, hits return to invoke them</li>

  </ul></li>

 <li>Batch

  <ul>

   <li>shell reads from an input file</li>

  </ul></li>

 <li>What is the difference?

  <ul>

   <li>where the commands come from</li>

  </ul></li>

 <li>You need to implement the Interactive shell model.</li>

</ul>




<h1>Input/Output</h1>

<ul>

 <li>C has 3 standard files prepared for you

  <ul>

   <li>stdin = input</li>

   <li>stdout = output</li>

   <li>stderr = error output</li>

  </ul></li>

 <li>printf(“foo”) == fprintf(stdout,”foo”)</li>

 <li>scanf(“%s”,str) == fscanf(stdin,”%s”, str)</li>

 <li>fprintf(stderr,”Panic!”) prints an error message separately</li>

</ul>




<h1>Process Control</h1>

<ul>

 <li>Your shell should execute the next command line <strong>after </strong>the previous one terminates – you must wait for any programs that you launch to finish</li>

 <li>You don’t have to provide the functionality of launching multiple simultaneous commands with “;” separating them</li>

</ul>




<h1>Hints</h1>

<ul>

 <li>A shell is a loop

  <ul>

   <li>read input</li>

   <li>execute program</li>

   <li>wait program</li>

   <li>repeat</li>

  </ul></li>

</ul>




<ul>

 <li>Useful routines

  <ul>

   <li>fgets() for string input</li>

   <li>strtok() for parsing</li>

   <li>exit() for exiting the shell</li>

   <li>getpid() for finding the current process ID</li>

   <li>getppid() for finding the parent process ID</li>

   <li>getcwd() for getting the current working directory</li>

   <li>getenv()/setenv()</li>

   <li>chdir() for changing directories</li>

  </ul></li>

</ul>




<ul>

 <li>Executing commands

  <ul>

   <li>fork() creates a new process</li>

   <li>execvp() runs a new program and does path processing</li>

   <li>wait(), waitpid() waits for a child process to terminate</li>

  </ul></li>

</ul>




<strong>Requirements: </strong>

<ul>

 <li>&lt;executable&gt; -p &lt;prompt&gt; should allow the user to select an user-defined prompt. Otherwise, the default should be “my257sh&gt; ”.

  <ul>

   <li>Shell functions to be implemented separately: exit, pid, ppid, cd. o For implementing “exit” from the shell, use the raise() signal handler.</li>

   <li>“cd” prints the current working directory; whereas “cd &lt;path&gt;” will change the current working directory.</li>

   <li>All other shell commands will need a child process using fork() and then calling execvp().</li>

  </ul></li>

 <li>No input will be greater than 50 characters.</li>

 <li>Only the interactive system needs to be implemented (batch system is not needed)</li>

 <li>Background process execution (using &amp;) is NOT required.</li>

 <li>Each time a child process is created, evaluate its exit status and print it out.</li>

 <li>^C should not take us out of the shell; use a signal handler. Hint: you can use the same signal handler code from the slides.</li>

</ul>














