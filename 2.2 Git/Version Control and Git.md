#Git 
## What is a Version Control System?
- Keep track of file changes (or a set of files)

### When to use one?
- Any time projects with many files and changes over a long period of time
- Other functionality to help organise your team

### Benefits
- Rollback/Revert changes
- Who made what changes

### Types of Version Control

#### What is manual Version Control?
- you name it v1, you make changes, you save an extra file as v2

#### How did early version control systems work?
- some just tracked changes to one file
- base file -> delta (changes) -> delta (changes)

### Centralised VCS vs Distributed VCS (like Git)

![[Pasted image 20250508174423.png]]


### Local Version Control with Git
- What is stored in each version of a file that changes

### Does Git need to be used as a distributed VCS?
- No. It can be used as a centralised/localised VCS on your own machine if you want your own backups of your files or if you want local collaboration.

### What does Git store in a "commit"?
- If a file hasn't changed, references previous commit

### The three states in Git
Working Directory --(Stage fixes)--> Staging Area --(Commit)--> .git directory (Repository)
									|
<--------------(Checkout the project)-----------

### Where does Git store its information
- .git folder

### Common workflow of Git commands



