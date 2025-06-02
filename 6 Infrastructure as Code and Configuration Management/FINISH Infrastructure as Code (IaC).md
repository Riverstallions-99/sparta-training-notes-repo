
Why do we want to use IaC/What's the problem?
- We're still manually provisioning servers (deploying servers with resources)

What have we automated so far?
- VMs
	- Creating VMs? No
	- Create the infrastructure they live in? No
	- Setup and configuring of the software? Yes

Automating all of it
Codify all of it
	We don't want to define the steps (that's imperative, like our bash scripts)
	We want it to be declarative (you define the end goal)

How to solve the problem?

IaC can provision:
- infrastructure (the servers)
- configuring of the server (the software and settings)

What is IaC?
- manage and provision computers through code that is both human readable and machine readable
- define what you want

benefits?
- speed and simplicity
- consistency and accuracy
- version control
- scalability (horizontal scaling/scaling out)

2 types of tools available for IaC:
Orchestration tools:
- CloudFormation (AWS)
- Terraform
- ARM/Bicep templates (azure)
- Ansible - can do it but wasn't designed for this purpose
Configuration Management tools:
- Ansible
- Chef
- Puppet


![[Pasted image 20250520144250.png]]