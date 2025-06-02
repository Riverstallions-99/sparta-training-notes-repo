#linux #cli #bash 
  
Contents  
- [[#Piping]]
- [[#Redirection and appending]]
- [[#Streams]]
- [[#Create and run Python Script]]
  
---  
  
## Piping
  
What is piping?  
- Piping is when you take the output of a previous command and give it to the following command, a way of lining up commands for automation.  
- Piping is unidirectional, they move from left to right  
  
How is piping different to redirection using > or >>?  
- Piping takes output (stdout) from one command into another, redirection takes the output and gives it to a file/script  
  
What character is used for piping?  
- `|`  
  
Give an example of a command that using piping once  
- `ls -l | more`  
  
Give an example of a command that using piping twice  
- `ll | grep .txt | wc -l`  
  
Give an example of a command that using piping twice, then sends the output to a file  
Hint: The grep, sort, head, tail commands could be useful  
For piping twice, you could:  
use ls as the input, search for string in more than folder/file, then sort the files/folders that match in reverse order.  
use ls as the input, get the bottom 2 rows of the first 3 rows  
- `ll | grep -r text | wc -l > output.txt`  
  
## Redirection and appending  
  
What does > do?  
- Redirects an output of a command to a file  
  
How is appending different?  
- Appending with >> adds the contents onto the end of the file, the > overwrites the file  
  
Give an example of a command where it appends to a file  
- `grep -r text >> appending-file.txt`  
  
  
## Streams  
  
What is a stream in Linux?  
- A flow of information/data between software and the machine (e.g. the screen)  
  
What are the 3 data streams?  
- `stdin 0` Standard Input  
- `stdout 1` Standard Output  
- `stderr 2` Standard Error  
  
Create a new file new.txt and run the command ls missing_directory new.txt - this should give output to two different streams.  
- stderr and stdout  
  
How can we direct each stream to a file (one at a time)?  
- `| tee <file>` stdout goes to a file (but also outputs to the command line)
- `2>&1` redirects channel 2 (stderr) to channel 1 (stdout)  
- `echo <value> | tee <file>` inputted value goes to file  
  
How can we direct both 2 output streams to a file?  
- `echo <value> 2>&1 | tee <file>` takes the errors (if any) and directs them to the stdout stream and then saves that to a file  
  
Which stream is directed to a file by default?  
- `stdin`  
  
How can we direct both output streams to a file in one command?  
- `echo <value> 2>&1 | tee <file>` takes the errors (if any) and directs them to the stdout stream and then saves that to a file  
- `find /etc -type f > ~/results.txt 2> ~/errors.txt` find all instances of a file in /etc (should give a few errors and lots of standard output) direct the stdout to results.txt in our home directory and direct the stderr to a file called errors.txt, also in the home directory  
- two `>>` appends rather than overwrites the file.
- 
  