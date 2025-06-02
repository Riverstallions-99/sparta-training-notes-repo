Contents:
- [[#Why use a VPC?]]
- [[#Creating a VPC on GCP]]
## Why use a VPC?
Allows you to control your firewall rules specifically for your VPC, tighter security than the project wide default VPC

## Creating a VPC on GCP
1. Create VPC network
	1. Name: tech504-becky-2-subnet-vpc
	2. First subnet: 
		1. Name: tech504-becky-public-subnet
		2. Region: usual
		3. IPv4 range: 10.0.2.0/24 
		4. Done
	3. Second subnet:
		1. Name: tech504-becky-private-subnet
		2. Region: usual
		3. IPv4: 10.0.3.0/24
		4. Done
	4. Create

## Deploying a VM on a VPC
- Use db image that you know works
- Make sure Region is the same as the VPC's region
- Network tag: db-server
- Edit network interface:
	- change default to your private subnet
	- External IPv4 address to None
- Security -> VM access -> Manage access: Check "Control VM access through IAM permissions"


### Firewall rules:
- DB needs to connect to the outside somehow (without an external IP address) - Control access using IAM
- Create firewall rules that use network tags, apply network tags to db and app VMs
	- Allow ingress from app to database (source tag: http-server) (target tag: db-server) (tcp:27017)
	- Allow ingress from iap (35.235.240.0/20) (tcp:22)
	- Allow http traffic from/to all (target tag: http-server) (IPv4 ranges: 0.0.0.0/0) (tcp:80)


#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]