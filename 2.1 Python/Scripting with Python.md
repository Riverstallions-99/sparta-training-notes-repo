#python [[Python]]

immutable data type
ints and strings are immutable

math_operations is a module  
collection of modules is a library  
a package is an installable library/module (using PIP)

## Intro to Scripting

### What is scripting?
- Code written to automate tasks (quick task, manipulate data)
### What are the characteristics of scripting?
- Procedural
- Interpreted not compiled
### Why is python good for scripting?
- Readability
- Many libraries available
- Portable
- Interpreted language - Not a compiled language, code is usually executed in order written 
### Example of python script:
```python
import os  
  
directory = "/path/to/files"for filename in os.listdir(directory):  
    if filename.endswith(".txt"):  
        new_name = f"renamed_{filename}"
```

### Main differences between programming and scripting
![[Pasted image 20250422135855.png]]
### Is python better for scripting or programming?
- Flexible enough to excel at either but imo better for scripting
### Do cloud/DevOps engineers usually do programming or scripting? Why?
- Scripting more than programming
- Automating tasks if its worth it
### Examples of ways we use scripts as Cloud/DevOps Engineers
To set up VMs with the settings and packages we would like to run, and to run them automatically. 