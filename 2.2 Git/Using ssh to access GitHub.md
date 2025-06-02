#ssh #Git 
1. Create SSH key
Move into the .ssh directory on your device and run the ssh-keygen command to generate the ssh key-pair:
```
$ cd .ssh
$ ssh-keygen -t rsa -b 4096 -C "white.rebecca2012@gmail.com" 
```
`-t rsa` : type RSA
`-b 4096` : byte length 
`-C "<value>"` : owner of the key

Name the key-pair with a sensible name, I went for "becky-atlas-github-key"

![[Pasted image 20250508204520.png]]

2. Register public key with GitHub
Print the public key to the command line and then copy and paste the whole key into GitHub. It's very important that you only share the public key. The private key is for your eyes only!
```
$ cat becky-atlas-github-key.pub
```

Then I went to the "SSH and GPG keys" section in my GitHub settings and clicked "New SSH key"
![[Pasted image 20250508203052.png]]
After that I pasted in the key and named it something sensible (becky-atlas-github-key) which made sure I knew which key was being referred to in my .ssh directory. 

![[Pasted image 20250508204634.png]]

2. Add the private key to your local SSH register
```
$ eval `ssh-agent -s`
$ ssh-add becky-atlas-github-key
```
If you get a PID back after the `eval` command, it has started the ssh-agent.
You should also get back "Identity added \[...]" after running the `ssh-add` command, this means it has been successful. 
![[Pasted image 20250508204850.png]]
Test success by authenticating with GitHub:
```
ssh -T git@github.com
```
This should return your GitHub username with a success message (It might ask if you want to add the host to the known hosts, just say yes for this but if you did want to check the key fingerprint, Git do have it publicly available here: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints) 
![[Pasted image 20250508204921.png]]

2. Create Repo

3. Push changes using SSH
