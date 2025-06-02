 #linux #cli #bash
  
Contents:  
- [Commands](#commands)  
  - [History Command](#history-command)  
  - [List Directory Command](#list-directory-command)  
  
---  
  
## Commands  
### history command  
`history` gives a list of previously used commands  
`!16` allows you to run a previous command from the history, using the index listed  
`history -c` clears your history   
  
  
### list directory command  
`ls -l` or `ll` gives a verbose list of files and directories  
  
### curl command  
`curl <url>` to fetch a website, if the end point/url is a .jpg, you can save the file using: `curl <url/<filename>.jpg> --output <filename.jpg>` or `curl <url/<filename>.jpg> > <filename.jpg>`  
  
`cp <filename>` copy file  
`rm <filename>` remove file  
`mkdir <directory>` make directory  
`rmdir <directory>` remove directory  
`rm -r <directory>` remove directory recursively  
  
`cd ..` change into parent directory  
`cd ~` change into home directory  
`cd /` change into root directory  
  
`touch <file>` makes empty file if not exists  
`head -<number> <file>` gives the top number of lines of a file  
`tail -<number> <file>` gives the bottom number of lines of a file  
  
`nl <filename>` number lines  
  
`sudo apt update` fetches new versions of stuff on system  
`sudo apt upgrade` installs the new versions of stuff on system  
  
`sudo systemctl status <process>` gives the status of a process  
`sudo systemctl restart <process>` restarts a process  
`sudo systemctl is-enabled <process>` checks if a service is enabled (runs on start up)

### Environment Variables

`$ printenv` prints the environment variables
`$ printenv USER` prints the environment variable with the name "USER"
`$ MYNAME=becky` sets a variable called MYNAME to have the value "becky"
`$ echo $MYNAME` will print the variable "MYNAME" to the CL
`$ export MYNAME` will set the variable as an environment variable

Variables reset after use?
Environment Variables reset in new bash sessions
If you want to make an Environment Variable persistent across sessions you need to add it to the .bashrc file. NB: you need to run `$ source .bashrc` to trigger the session to update the Env Var.

### Processes
`$ ps` shows a list of user processes
`$ ps -a` shows a list of all processes
`$ ps aux` lists more info about all processes
`$ top` lists more info about all processes
`$ htop` fancy processes list which autorefreshes (you have to q or Ctrl+c out of this window)

### Nginx (Web Server)
`$ sudo systemctl status nginx` this will give you the status of the nginx service
`$ sleep 5` makes terminal wait 5 seconds
`$ sleep 5000 &` makes terminal wait 5000 seconds but makes it a background process due to the "&"
`$ jobs` gives a list of user run services in this bash session
`$ jobs -l` also lists the PID
`$ kill -1 <PID>` kills the process with the specified PID, the -1 flag is the level of severity of the killing. -1 is a safe way, -9 is the default way (kills parent process and any child processes), -15 is the most extreme way (kills process, does not kill any child processes so could leave zombie children). 