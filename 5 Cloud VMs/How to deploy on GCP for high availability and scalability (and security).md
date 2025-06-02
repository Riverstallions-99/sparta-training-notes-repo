- VMs minimum of two, so always have a backup in place.
- VMs spread out over zones.
- Instance groups handle the horizontal auto-scaling for you. 
- By monitoring the app's performance with alert policies you can construct a load balancer that will direct the traffic/activity of the app equally between your VMs. If one of the VMs is overwhelmed, the instance group can generate another for you, at which point the load balancer will distribute the activity evenly.
- Securing Database: No external IP address, not exposed to external network traffic and not able to access using SSH via external IP address. 
- 


IAP Identity Aware Proxy


Why are subnets and firewalls important?
Firewall allows access to app VM, restricts access to DB VM.  

with own VPC: Set up own unique firewall rules which are tailored to your app and how it needs to communicate, blocking off and restricting everything else that is not needed, which just adds to the security. 

## VPCs and Subnets

Europe West 8 b 
tech504-becky-in-custom-vpc-db-vm
![[Pasted image 20250515112512.png]]![[Pasted image 20250515112533.png]]
![[Pasted image 20250515112553.png]]![[Pasted image 20250515112627.png]]



#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]