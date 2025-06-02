Contents:
- [[#Overview]]
- TO-DO [[#What is autoscaling?]]
- [[#Auto Scaling on GCP]]
- TO-DO [[#Identity-Aware Proxy (IAP) TCP forwarding]]
- [[#Instance Groups (and Templates)]]
	- [[#Instance Template]]
	- [[#Instance Group Creation]]
- [[#Health Check]]
- [[#Load Balancing]]

## Overview

### What is autoscaling?

TO-DO Diagram!
### Why use auto scaling?
- Another method of automation, increases availability, therefore providing value for the customer and the business.

### Types of auto scaling
- Horizontal (scaling out or in)
	- Scaling out with extra machines, original VM gets kept, load gets shared over multiple VMs (average over all VMs)
- Vertical (scaling up or down)
	- Scaling up to a bigger machine with more computing power (more RAM etc.). VM gets transferred and the old, smaller VM gets deleted (or adjusted to be bigger).

## Auto Scaling on GCP
We're going to be using an instance group. (Called VM Scaling set on Azure, called Auto Scaling Group on AWS). On Azure, we can use images to redeploy VMs, it also can preserve the start up script that we need to run the app on the VM (not available on AWS in the same format)

## Identity-Aware Proxy (IAP) TCP forwarding
TO-DO

## Instance Groups (and Templates)
The implementation of autoscaling, we can create rules in the instance group which will make sure there are a minimum of 2 VMs running in the group, this means if one VM goes down there will always be a backup while the second VM gets back up and running. 

### Instance Template
1. Navigate to Compute Engine -> Instance templates -> Create instance template.
2. Name the instance template something sensible and select "Regional" for the Location, then select your Region, for me this is "europe-west9"![[Pasted image 20250515162219.png]]
3. Select the Machine type "e2-small" ![[Pasted image 20250515162541.png]]
4. "Change" -> Custom image -> becky-app-vm-image ![[Pasted image 20250515172702.png]]
5. ![[Pasted image 20250515162755.png]]
6. ![[Pasted image 20250515162828.png]]
7. For the instance group, we don't need an external IP address as external network traffic will go through our load balancer, when we get around to making that. ![[Pasted image 20250515173445.png]]
8. For the app to be able to run on start up of the VM, we need to include a start up script which we developed previously. ![[Pasted image 20250515163027.png]]
9. Click "Create"

### Instance Group Creation
1. Once we have made the instance template, it is best practice to check the template works by using it to create a VM, I'm not going to write these steps out as I have in the rest of this documentation but the general jist is: Go to the instance template, click "Create VM", the only thing that needs to be changed is under Networking -> Network interfaces -> default -> change the "External IPv4 address" to be Ephemeral and then change the Network Service Tier to be "Standard".
2. To make the instance group: Navigate to "Compute Engine" -> "Instance groups" ![[Pasted image 20250515161318.png]]

3. Click "Create instance group", leave as default "New managed instance group (stateless)" ![[Pasted image 20250515161705.png]]

4. Name group something sensible and select your previously made Instance template. ![[Pasted image 20250515174219.png]]
5. ![[Pasted image 20250515164112.png]]
6. Helps autoscaling make better decisions, eg if CPU spikes on start-up, it doesn't need to make a new VM yet ![[Pasted image 20250515163403.png]]
7.  Under Autohealing, we can see I don't have a health check yet, so we need to Create a health check: (see [[#Health Check]])
8. Time to wait to check if the VM/app is healthy ![[Pasted image 20250515165800.png]]
9. We need to do as the dialog box explains above and create a firewall rule to allow for the health check to actually connect to our VM instances to see if they're still active. Only one person needs to do this as we're on the same, larger project network. (There are steps on the GCP console.)
10. ![[Pasted image 20250515164403.png]]
11. Create

---
## Health Check
1.  ![[Pasted image 20250515164929.png]]
2. Under Protocol, we can change it to be HTTP and it will ensure that it is only healthy if it responds with a 200 (OK) response, which is the behaviour we want.  ![[Pasted image 20250515165640.png]]
---
## Load Balancing

1. Navigate to Network Services -> Load balancing.
2. Type of load balancer: Application load balancer (as we are using HTTP traffic), click Next.
3. Public facing or internal: Public facing (external), click Next.
4. Global or single-region deployment: regional, click Next.
5. Click configure load balancer.
6. 
	1. Load balancer name: tech504-becky-app-lb
	2. Region: EU-W9 (usual)
	3. Network: default
	4. Proxy-only subnet: Click Reserve to make a new proxy-only subnet
		1. Name: lb-proxy-eu-west-9
		2. IPv4 range: 10.0.9.0/26
	5. Frontend configuration:
		1. Name: tech504-becky-app-lb-ip
		2. Network Service Tier: Standard
		3. IP address: Ephemeral
	6. Backend configuration:
		1. Create backend service
		2. Name: tech504-becky-app-lb-backend
		3. Backends -> Instance group: tech504-becky-app-lb-backend
		4. Port numbers: 80
		5. Health check: tech504-becky-health-check-tcp-port-80 (although this is now an http port health check but I didn't change the name)
	7. Create
	8. Check it works by going to the IP address of the load balancer

#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]