#Git 
Why do we use a .gitignore file?
- Simply, to ignore the files we don't want to be version controlled (eg sensitive info that has to be included - but try not to do that)
If we do need to use sensitive information in our repositories but not sent to the repo:
- Sensitive info: Needs to be included in .gitignore
- Credentials: 
	- Needs to be a private repo
	- Needs to be encrypted with your 

**.ssh should NEVER be part of a git repo**

If something confidential is pushed to a public git repo, quickest way to address is:
1. remove the GitHub or other remote repo
2. disable/remove confidential info wherever it's used (eg GCP credentials; change password)
3. To remove the traces of the credentials, either:
	- git reset (to keep some commit history)
	- delete .git (will lose all commit history)

