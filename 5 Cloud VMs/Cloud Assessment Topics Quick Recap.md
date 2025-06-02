5 Qs on consultancy/DevOps

First week on site as Junior DevOps engineer, what would you like to focus on?
- Learning tech stack
- Reading documentation
- Getting set up with their processes
- Getting familiar with the system/project
- Security induction
- Installing software (IDEs etc)
- Asking questions about their set up, their expectations for you


process to incrementally, automatically deploy app on VM
- manually deploying using OS disk, using commands on the CLI
- create script, test with new VM with same OS
- start up script on VM with same OS
- create image with baby start up script from our VM
- Create VM using image and baby script
- Idempotent 

running Sparta app in background
- & at end of command to run process in background

App VM start up script with image/OS
- need to stop app, find pm2 process started by root

if I need to ssh in to one of my VMs, created by my instance group, but the instances do not have an external IP, what are two ways I could SSH in?
- Bastion server/jumpbox
- IAP TCP forwarding (allows you to use the SSH button on google cloud console) just a GCP firewall rule which allows Google to connect and you allow SSH port 80, IAP permissions per user

restart instances
- start up script does run on GCP when you restart the VMs/instance group
- azure uses re-image (replaces the disk with image)

Most important things to set up for security on VMs
- Firewall rules
- shutting it off from external network traffic
- strict controls on subnet
- VPC then subnets
- IAP
- http-server 

quick and easy security under time pressure
- make DB only accept traffic from app VM (bindIP)
- remove external IP from DB VM
- if using default VPC:
	- lockdown firewall rules, only allow specific network traffic into specific ports
	- 
---

## Answers I think I missed
Check DB provisioned correctly:
Status of DB
Print mongod.conf to screen

Firewall rules:
Action on match: allow
Allow TCP traffic on port 3000
Source IPv4 ranges: 0.0.0.0/0 (just means all)
Target tag 'http-server'

/posts page working:
install MongoDB, restart MongoDB

run nodejs in background:
nohup npm start &
pm2 start app.js

stop app:
use kill command to stop pm2 process

security:
firewall rules, network tags

ssh only via console:
add network tag (matching target tag in firewall rule), custom VPC, Control VM access using IAM permissions, No external IP address

deploy db on secure subnet:
db virtual machine image ready

important firewall rules to secure db:
allow ingress from IAP,
Allow ingress from app to db
allow http traffic to app vm

#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
