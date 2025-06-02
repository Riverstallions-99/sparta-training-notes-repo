## Deploying Database VM using image (example)
1. Click "Create instance"
![[Pasted image 20250515115818.png]]

2. Name the VM something sensible, as I am going to be deploying this VM with an image, I am naming it "tech504-becky-db-from-image-vm"
3. Select the "Region" and "Zone", for this case I have been using "europe-west9(Paris)" and zone "europe-west9-c" so as to not interfere with others' regions due to limitations on the amount of VMs that can be deployed in one region and I chose zone C because zones A and B aren't able to deploy the machine type I want to use.
4. Leave the Machine type as "E2" and further down, use the drop down box to select "e2-small"
![[Pasted image 20250515125824.png]]
5. Select "OS and storage" from the left-side menu, and then select "Change" below the "Operating system and storage" details.
![[Pasted image 20250515121100.png]]
6. This will bring up a side menu. Select "Custom image" as I am going to be using a custom image. 
![[Pasted image 20250515121123.png]]
7. Under "Image", filter for your name to find your image. Then select the image you wish to use, in this case I am going to be using my database image called "tech504-becky-db-vm-image". Leave everything else as it is and click "Select".
![[Pasted image 20250515121400.png]]
8. Move on by selecting "Data protection" from the left side menu, and select "No backups".
![[Pasted image 20250515121545.png]]
9. Under "Networking" in the left side menu, we need to add a network tag called "db-server" this is a firewall rule which allows communications from and to the database server. 
![[Pasted image 20250515122008.png]]
10. Clicking on the drop down under "Network interfaces" called "default" we need to change the "Network Service Tier" to "Standard" and click "Done"
![[Pasted image 20250515122132.png]]
11.  Select "Create" to begin the provisioning process.


App VM
Same steps as above except:
Name: tech504-becky-app-from-image-vm
Custom image: tceh504-becky-app-vm-image
Firewall: Allow HTTP traffic
Network tags: sparta-app
Start-up script: 
```bash
#!/bin/bash  
# Tested: 2025-05-07  
# Tested by: Becky  
# Tested on: GCP, Ubuntu 20.04 LTS  
# Result:  
  
cd /sparta-test-app-repo/app  
echo ------ Running npm install... ------  
npm install  
echo  
  
echo ------ Changing Adding DB_HOST variable... ------  
export DB_HOST=mongodb://10.200.0.27:27017/posts  
echo  
  
echo ------ Starting Sparta App in background with pm2... ------  
pm2 start app.js  
echo
```

#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]