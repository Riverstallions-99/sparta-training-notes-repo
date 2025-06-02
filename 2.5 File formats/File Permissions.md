#bash  
  
Overview of Tasks:  
- [[#Task Linux - Research managing file ownership]]] 
- [[#Levels of ownership]]
- [[#Permissions]]
- [[#Task Linux - Research managing file permissions]]
- [[#Task Linux - Research managing file permissions using numeric values]]
- [[#Task Linux - Research changing file permissions]]
  
---  
  
## Task: Linux - Research managing file ownership  
Research:  
Why is managing file ownership important?  
- Need-to-know security basics  
  
What is the command to view file ownership?  
- `ls -l` or `ll`  
- `stat`  
  
What permissions are set when a user creates a file or directory? Who does file or directory belong to?  
- `-rw-rw-r--` default permissions, Read, Write permissions for the User and Group, Read-only permission for others  
- File/Directory belongs to the user  
  
### Levels of ownership:  
- User owner (u) The owner of the file or directory  
- Group owner (g) The group to which the file or directory belongs  
- Others (o) All other users who are not the owner or in the group  
  
### Permissions:  
- Read(r) The ability to read the contents of a file or view the contents of a directory  
- Write(w) The ability to modify the contents of a file or create, rename or delete files in a directory  
- Execute(x) The ability to execute a file or enter a directory  
  
Why does the owner, by default, not receive X permissions when they create a file?  
- It's not necessary and could be harmful to the system if used incorrectly.   
What command is used to change the owner of a file or directory?  
- `chown <user> <file>`  
  
---  
  
## Task: Linux - Research managing file permissions  
Research:  
  
Does being the owner of a file mean you have full permissions on that file? Explain.  
- Not automatically, you need to change the permissions yourself  
  
If you give permissions to the User entity, what does this mean?  
- You've given permissions to the owner of the file/directory  
  
If you give permissions to the Group entity, what does this mean?  
- You've given permissions to the group of users for which the file/directory belongs  
  
If you give permissions to the Other entity, what does this mean?  
- You've given permissions to anyone who is not the owner of the file/directory, or in the group for which the file/directory belongs.  
  
You give the following permissions to a file: User permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute. You are logged in as the user which is owner of the file. What permissions will you have on this file? Explain.  
- `-r--rw-rwx`  
- You, as the user and owner of the file, will only be able to read the contents of the file but if you are also a member of the group, you should also be able to write to the file, but not execute  
  
Here is one line from the ls -l. Work everything you can about permissions on this file or directory.  
`-rwxr-xr-- 1 tcboony staff  123 Nov 25 18:36 keeprunning.sh`  
- From this output, we can see that the Owner has Read, Write and Execute permissions, the Group has Read and Execute permissions, the Group has Read-Only permissions.  
- The `1` tells us it is one file, if it were a directory with 3 files inside, it would read `4` instead (hard links)  
- `tcboony` is the Owner of the file  
- `staff` is the Group the file is in  
- `123` is the size of the file in mb  
- `Nov 25 18:36` is the date of last modification  
- `keeprunning.sh` is the name of the file  
  
---  
  
## Task: Linux - Research managing file permissions using numeric values  
Research:  
  
What numeric values are assigned to each permission?  
- Binarily, 1 for each, seperated into 3 sections for each level of user.   
- E.g.  
  
| d | rwx | r-x | r-- |  
|---|-----|-----|-----|  
| d | 111 | 101 | 100 |  
| d | 7   | 5   | 4   |  
  
  
What can you do with the values assign read + write permissions?  
- 6? Unsure what the question is...  
  
What value would assign read, write and execute permissions?  
- 7  
  
What value would assign read and execute permissions?  
- 5  
  
Often, a file or directory's mode/permissions are represented by 3 numbers. What do you think 644 would mean?  
- **Owner**: Read, Write  
- **Group**: Read-Only  
- **Others**: Read-Only  
  
---  
  
## Task: Linux - Research changing file permissions  
Research:  
  
What command...  
- changes file permissions?  
    - `chmod +x  <file>` or `chmod u+x  <file>`or `chmod 755  <file>`  
    - `755` Set permissions to read/write/execute for the owner, and read/execute for others.  
    - `u+x` Set permissions to include execute for the owner  
    - `+x` Set permissions to include execute for all levels of ownership  
- To change permissions on a file what must the end user be? (2 answers)  
  - Owner  
  - Root  
- Give examples of some different ways/syntaxes to set permissions on a new file (named testfile.txt) to:  
  - Set User to read, Group to read + write + execute, and Other to read and write only  
        - `chmod a=r,g=wx,o=w <file>`  
        - `chmod 476 <file>`  
    - Add execute permissions (to all entities)  
        - `chmod a+x <file>`  
        - `chmod +x <file`  
    - Take write permissions away from Group  
        - `chmod g-w <file>`  
    - Use numeric values to give read + write access to User, read access to Group, and no access to Other.  
        - `chmod 640 <file>`