Contents

- [[#How to add your key pair to AWS|How to add your key pair to AWS]]
- [[#Firewall Rules/Security Groups|Firewall Rules/Security Groups]]
- [[#Provisioning and deploying App VM|Provisioning and deploying App VM]]
- [[#Provisioning and deploying DB VM|Provisioning and deploying DB VM]]


It's helpful to change region permanently when you log on:
![[Pasted image 20250520111422.png]]

## Firewall Rules/Security Groups

1. Navigate to EC2 -> Network & Security -> Security Groups then click 'Create security group'
2. 
	- Security group name: tech504-becky-allow-ssh-http-for-app
	- Description: Allows ssh and http for app
3. Click 'Add rule'
![[Pasted image 20250521121401.png]]
4. First Inbound rule:
	- Type: SSH
	- Source: My IP
	- Description: Allow traffic via SSH to app VM for admin purposes
5. Second Inbound rule:
	- Type: HTTP
	- Source: Anywhere-IPv4
	- Allow HTTP traffic from anywhere to access app on web
![[Pasted image 20250521122321.png]]
NB: You can leave the Outbound traffic as it is. 
6. Click 'Create security group'
## How to add your key pair to AWS
1.  Navigate to Compute -> EC2 -> Key pairs -> Actions -> Import key pair
2. Set the name as something sensible and paste in your public key into the 'Public key contents' text box. ![[Pasted image 20250520112537.png]]
## Provisioning and deploying App VM
### Prerequisites
You need to have set up the key pair for authentication ([[#How to add your key pair to AWS]]).
### Steps
1. Change region in the top right to: Europe (Ireland) which is eu-west-1
2. Navigate to Compute -> EC2 -> Launch instance
3. Name: tech504-becky-app-vm
4. OS Image: Ubuntu 22.04 LTS![[Pasted image 20250520113547.png]]
5. Instance type: t3.micro ![[Pasted image 20250520114454.png]]
6. Key pair: Should've already added key pair to project above so use drop down menu: ![[Pasted image 20250520114537.png]]
7. #TODO Network settings: 
8. Advanced details -> User data: input your app provision script ![[Pasted image 20250520113246.png]]
9. Launch instance

To send provision script to app VM:
` $ scp -i ~/.ssh/tech504-becky-aws-key.pem sparta-app-prov-script-aws.sh ubuntu@63.33.42.62` 

Blockers/Issues: 
- NB: Check region constantly!
- When choosing an OS image, had to switch to Ubuntu 22.04 for both VMs as unable to use Ubuntu 20.04
- When connecting via SSH on CLI, username when connecting needs to be "ubuntu"

## Provisioning and deploying DB VM

### Prerequisites
You need to have set up the key pair for authentication ([[#How to add your key pair to AWS]]).
### Steps
TO-DO