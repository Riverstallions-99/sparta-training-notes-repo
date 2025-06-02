## Contents
- [[#Defining a VM|Defining a VM]]
	- [[#Defining a VM#Variables|Variables]]

TO-DO Git Repo set up, what to include in .gitignore

NB: HCL format uses key-value pairs
## Defining a VM

Create file `main.tf`
```HCL
# Creating an ec2 instance:

# where to create - provide cloud provider name
provider "aws" {
  # which region to create the resource/service
  region = "eu-west-1"
}

# which resource to create,
# "aws_instance" is the type of instance we want to create
# "app_instance" is the referal name that terraform will use
resource "aws_instance" "app_instance" {

    # which AMI ID to use (ami-0c1c30571d2dae5c9) for Ubuntu 22.04 LTS
    ami = "ami-0c1c30571d2dae5c9"
    
    # which instance type t3.micro
    instance_type = "t3.micro"

    # add a public IP address to this instance
    associate_public_ip_address = true

    # name the instance
    tags = {
	    # AWS will call the instance this name tag
        Name = "tech504-becky-terraform-test-app" 
    }
}
```
In git bash: 
`$ terraform init` will initialise terraform in that directory, creating the .terraform directory, if ran after main.tf exists, it will get the most recent version of the provider or the version written in the '.terraform.tfstate.lock.info'
`$ terraform plan` will set terraform to making the plan for how to deploy the VM
`$ terraform apply` will tell terraform to make the VM (it will also plan before applying)
`$ terraform destroy` will tell terraform to destroy the VM

To be able to have multiple VMs we need to create directories to hold the information within our repository directory.

1. Create directory 'tf-create-basic-ec2' to hold 'main.tf', '.terraform.lock.hcl', 'terraform.tfstate', 'terraform.tfstate.backup' and '.terraform'
2. Run `terraform plan` again to ensure it still works

### Variables
If we want to add a variable so we can obscure any info we don't need to share, for example we don't want people to know the version of OS we're using as if this version has anything exploitable, this will give people the info that we are using that version, it's just not necessary to share this information. 
Create 'variable.tf' file:
```hcl
# create variable for ami id called "app-ami-id"

variable "app-ami-id" {
  description = ""
  type = string
  default = "ami-0c1c30571d2dae5c9"
}
```
In 'main.tf' we can refer to the variable instead of hardcoding the value:
```hcl 
ami = var.app-ami-id
```

### Security Groups and Rules
Define the Security group

Define the Inbound rules

Define the Outbound rules

#### Tags and Links 
#GCP 
#cloud 
#terraform

[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]