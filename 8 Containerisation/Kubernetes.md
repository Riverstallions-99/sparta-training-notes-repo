# Kubernetes Notes  
## Why is Kubernetes needed  
- manage containers workloads
- For container orchestration
## Benefits of Kubernetes  
- open source
- Can run anywhere (on prem, cloud, hardware etc)
- Self healing
- Auto scaling
- Load balancing
- Rolling updates and rollbacks
- define desired state of application and it will then automatically deploy/manage in order to meet the desired state
- Over a monolith:
	- Designed for no single point of failure
## Success stories  
Pokemon Go:
- was run on GKE (google kubernetes engine)
- Launched app in 2016, 50x expected traffic but GKE kept up
## Kubernetes architecture (include a diagram)  
![[Pasted image 20250605105805.png]]

Cluster?
- made up of at least 1 master node and 1 worker node
- Minikube - example of single work node - good for testing or dev env
	- Both master and worker nodes are run on a single VM
	- Simple version of K8s arch for learning/experimenting 
- AKS (Azure Kubernetes Service) - managed service
	- Azure takes care of the master node - you can’t change it, happens automatically, or see it
	- not charged for master node (on aws or gcp it costs about 10p/hr)
## Master vs worker nodes  
### Master node
- runs control plane 
- “Controller” to manage everything, controls worker nodes
- For production, how many do you need?
	- If setting up own cluster: set up 3 control plane nodes
	- If using a managed service: you don’t manage the master nodes directly

### Worker node
- where your containers are run by K8s
- they work on the “data plane” - because they run your applications/dbs/etc
## Pros and cons of using managed service vs launching your own  
- Using managed:
	- Less experts needed
	- Security updated automatically
	- Save time dealing with issues
	- Focus on delivering value to customers
- using your own:
	- More control but more responsibility
	- More experts needed

## Control plane vs data plane  
![[Pasted image 20250605111959.png]]
## Kubernetes objects  
### What is a container?
- not an object!
- Used with a pod (that is a k8s object)
### What is a pod?
- a group of one or more containers (also specifies how to run them)
- Share resources to containers in pods (storage, network)
- Run on a worker node
- smallest deployable object in k8s
- Have internal ip addresses
- are ephemeral (could lose data when pod is terminated)

![[Pasted image 20250605114916.png]]


### The most common objects, e.g. Deployments, ReplicaSets, Pods  
Volume
- persistent data

ConfigMap
- key-value database to store config

Secrets
- base64 encoded, **not** encrypted

Namespace
- defines all containers in a pod?

Label
- defines a container in a pod?

ReplicaSet
- made by the deployment

Deployment 
- used to deploy the ReplicaSet
- Doesn’t deal with the pods directly


### How to mitigate security concerns with live containers 
- use official/maintained images or trusted images only (eg ones your devs have built
- Use automated vulnerability scanning on container registries
- use own tools to do security scanning on your container images (can be included in your CI/CD pipeline)
- secrets (base64 encoded)
- NEVER run a container with root privileges 
- Monitor and/or log container activity 

## Maintained images  
### What are they  
- Regularly maintained, and updated by a trusted source, images (Eg. Canonical maintain Ubuntu images)
### Pros and cons of using maintained images for your base container images
Pros:
- safer/more secure
- Stable builds
- more documentation and support
- More likely to adhere to industry standards and practices. 
- Maybe streamlined for speed/image size
Cons:
- Relying on them doing the updating/patching (usually on a schedule)
---


#Kubernetes [[BeckyWhiteObsidian/Job & Career/Tech Stack Index/Kubernetes|Kubernetes]]


![[Pasted image 20250605134518.png]]