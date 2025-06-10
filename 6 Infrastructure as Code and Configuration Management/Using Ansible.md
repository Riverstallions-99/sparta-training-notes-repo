## Steps to install dependencies on Controller and set up for using Ansible.
- Once we have our Controller and Target node VMs set up (as blank Ubuntu 22.04 VMs) we can SSH in, provided we have used the correct security groups and the rules are set up correctly.
- We can also at this point, move the private SSH key, that the controller will need to use, into the controller VM using SCP: `$ scp -i tech504-becky-aws-key.pem tech504-becky-aws-key.pem ubuntu@34.248.133.123:~/.ssh` 
	- We can check the SSH key has worked by SSH-ing into the target node from the controller node, this is essentially a tunnel we have made (SSH into the Controller, SSH from Controller into Target)
	1. `$ cd ~/.ssh`
	2. `$ ssh -i <keypair-file>.pem ubuntu@<target-node-internal-IP>`

1. We need to run: `$ sudo apt update && sudo apt upgrade`
2. Then we need to add the repo for Ansible: `$ sudo apt-add-repository ppa:ansible/ansible`
3. Then do another update to refresh: `$ sudo apt update`
4. Install Ansible: `$ sudo apt install ansible -y`
5. Check it's been installed: `$ ansible --version` should give an output of 2.17.12 or similar
6. Move into our Ansible workspace: `$ cd /etc/ansible`
7. We can see if our Ansible controller is functioning by running: `$ ansible all -m ping` where -m is a module flag, by default this is 'ansible.builtin.command'.
8. `$ sudo nano hosts` will take us to the hosts file, there we can put in our hosts.
	1. Add lines:
		- `[web]`
		- `ec2-instance ansible_host=<target-node-internal-ip> ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/becky-aws-keypair.pem`
	2. Save and exit
9. We can now check the inventory of hosts by running: `$ ansible-inventory --graph`
NB: If you aren't able to ssh in from your controller node, you may need to adjust your security group rule to allow SSH from all traffic.

We can have a play around with Ansible now using some ad-hoc commands (-a is for arguments):
- `$ ansible web -a "uname -a"` this will run the command in quotes on the target nodes in our inventory that matches "web". 
- To do an update and upgrade on a target node from your controller:
	- `$ ansible web -m ansible.builtin.apt -a "update_cache=yes" --become`
	- `$ ansible web -m ansible.buildin.apt -a "upgrade=dist" --become`
- To move a file from the controller node to the target node: `$ ansible web -m ansible.builtin.copy -a "src=/home/ubuntu/.ssh/becky-aws-keypair.pem dest=~/.ssh/"` if you need to change the permissions when you copy the file you can use `mode=400` in the arguments. 




#ansible #cloud #AWS [[BeckyWhiteObsidian/Job-And-Career/Tech Stack Index/Ansible|Ansible]] [[Cloud]] 