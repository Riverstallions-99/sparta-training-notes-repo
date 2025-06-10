Contents:
- [[#What is Kubernetes used for?|What is Kubernetes used for?]]
- [[#Benefits of Kubernetes|Benefits of Kubernetes]]
- [[#Success stories|Success stories]]
- [[#Kubernetes architecture (include a diagram)|Kubernetes architecture (include a diagram)]]
- [[#Master vs worker nodes|Master vs worker nodes]]
	- [[#Master vs worker nodes#Master node|Master node]]
	- [[#Master vs worker nodes#Worker node|Worker node]]
- [[#Pros and cons of using managed service vs launching your own|Pros and cons of using managed service vs launching your own]]
- [[#How to mitigate security concerns with live containers|How to mitigate security concerns with live containers]]
- [[#Control plane vs data plane|Control plane vs data plane]]
- [[#Kubernetes objects|Kubernetes objects]]
	- [[#Kubernetes objects#What is a container?|What is a container?]]
	- [[#Kubernetes objects#What is a pod?|What is a pod?]]
	- [[#Kubernetes objects#The most common objects in k8s, e.g. Deployments, ReplicaSets|The most common objects in k8s, e.g. Deployments, ReplicaSets]]
- [[#Maintained images|Maintained images]]
	- [[#Maintained images#What are maintained images?|What are maintained images?]]
	- [[#Maintained images#Pros and cons of using maintained images for your base container images|Pros and cons of using maintained images for your base container images]]
- [[#Provisioning the Sparta app using Kubernetes|Provisioning the Sparta app using Kubernetes]]
	- [[#Provisioning the Sparta app using Kubernetes#Making app deployment .yaml file|Making app deployment .yaml file]]
		- [[#Making app deployment .yaml file#sparta-nodejs-app-deploy.yaml|sparta-nodejs-app-deploy.yaml]]
	- [[#Provisioning the Sparta app using Kubernetes#Making app service .yaml file|Making app service .yaml file]]
		- [[#Making app service .yaml file#sparta-app-service.yaml|sparta-app-service.yaml]]
	- [[#Provisioning the Sparta app using Kubernetes#Making database and service deployment .yaml files (and PVC .yaml file)|Making database and service deployment .yaml files (and PVC .yaml file)]]
		- [[#Making database and service deployment .yaml files (and PVC .yaml file)#db-deploy.yaml|db-deploy.yaml]]
		- [[#Making database and service deployment .yaml files (and PVC .yaml file)#db-service.yaml|db-service.yaml]]
		- [[#Making database and service deployment .yaml files (and PVC .yaml file)#db-pvc.yaml|db-pvc.yaml]]
	- [[#Provisioning the Sparta app using Kubernetes#Scaling our app deployment pods|Scaling our app deployment pods]]
- [[#Other useful Kubernetes commands|Other useful Kubernetes commands]]

## What is Kubernetes used for?  
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
- Using your own:
	- More control but more responsibility
	- More experts needed

## How to mitigate security concerns with live containers 
- use official/maintained images or trusted images only (eg ones your devs have built
- use automated vulnerability scanning on container registries
- use own tools to do security scanning on your container images (can be included in your CI/CD pipeline)
- secrets (base64 encoded)
- NEVER run a container with root privileges 
- Monitor and/or log container activity 

## Control plane vs data plane  
![[Pasted image 20250605111959.png]]
## Kubernetes objects  
### What is a container?
- It is not an object!
- Used within a pod 
### What is a pod?
- A group of one or more containers (also specifies how to run them)
- Shares resources to containers in pods (storage, network)
- Runs on a worker node
- The smallest deployable object in k8s
- Have internal IP addresses
- Are ephemeral (could lose data when pod is terminated)

![[Pasted image 20250605114916.png]]


### The most common objects in k8s, e.g. Deployments, ReplicaSets
**Volume**: persistent data
**ConfigMap**: key-value database to store config
**Secrets**: base64 encoded, **not** encrypted
**Namespace**: defines all containers in a pod?
**Label**: defines a container in a pod?
**ReplicaSet**: made by the deployment, holds the pods
**Deployment**:
- used to deploy the ReplicaSet
- doesn’t deal with the pods directly
## Maintained images
### What are maintained images?
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
## Provisioning the Sparta app using Kubernetes

Firstly, you need to enable Kubernetes via Docker Desktop. 
1. Go to the Settings and navigate to the "Kubernetes" tab on the left
2. Toggle "Enable Kubernetes"
3. Ensure the "Cluster" is running, this might require clicking, in the bottom right of the window, "Apply & restart"
Now we need to set up our directory structure, create a directory called "k8s-yaml-definitions" and then a directory inside called "local-nodeJS-app-and-db-deploy". This will be where we make our .yaml files. 
### Making app deployment .yaml file
This will be where we define how we want Kubernetes to deploy our app on pods.

#### sparta-nodejs-app-deploy.yaml
```yaml
# YAML is case sensitive
apiVersion: apps/v1  # specify api to use for deployment
kind: Deployment  # kind of service/object you want to create
metadata:
  name: sparta-nodejs-app-deployment # name the deployment
spec:
  selector:
    matchLabels:
      app: sparta-nodejs-app  # look for this label/tag to match with k8 service
  # create a replica set of this with instances/pods
  replicas: 3 # create 3 replicas of pods (to add as backups if one pod crashes)
  template: # using this template
    metadata:
      labels:
        app: sparta-nodejs-app # this label connects the deployment to the service, so must match the app: above
    spec:
      containers:
      - name: sparta-nodejs-app-container # what to call the container itself, when multiple are made, it adds on a string of numbers and letters at the end
        image: riverstallions/sparta-app-image-for-k8s-use:1.0 # the image I created, using Docker, to run the app
        ports:
        - containerPort: 3000 # port to expose in the container
```

Once you've got your app deployment file ready, you can run:
`kubectl create -f sparta-nodejs-app-deploy.yaml` where the -f flag will tell kubectl that we want it to create the deployment defined in the file

And to see if it's been successfully deployed we can run:
`kubectl get pods`
Some other helpful commands here are:
`kubectl get pods -w` will list the pods but also "watch" them and update the screen if anything changes, such as the pods crashing.
`kubectl get all` will show all the info for the current kubernetes objects (deployments, replicasets, pods etc.)
### Making app service .yaml file
Now we've got our app deployment running, we want to be able to access the app running on the pods via our web browser, to do this we need to define a service deployment. We can do this in another yaml file or in the same yaml file as before but just be aware that you need to seperate the "sections" with three dashes like this: \---
#### sparta-app-service.yaml
``` yaml
apiVersion: v1
kind: Service
metadata:
  name: sparta-nodejs-app-svc
  namespace: default
spec:
  ports: # access the service on port 31704
  - nodePort: 31704 # range is 30000-32768
    port: 3000
    targetPort: 3000
  selector:
    app: sparta-nodejs-app  # this label connect this service to the deployment
  type: NodePort  
```

1. Once we have this file set up we need to stop the app deployment if we haven't already:
`kubectl delete -f sparta-nodejs-app-deploy.yaml` where the -f flag will tell kubectl that we want it to delete the deployment defined in the file
2. Then we can deploy the app service using:
`kubectl create -f sparta-app-service.yaml`
3. We can check this is running using the `kubectl get all` command
4. Then we need to deploy the app itself again:
`kubectl create -f sparta-nodejs-app-deploy.yaml`
5. Again, we can check this is running using the above command
6. If everything is running, we can check the app is working by going to `http://localhost:31704` which is the port number I defined for the NodePort to use as the external port for the app service.
7. Congratulations, we've made our first kubernetes deployment!
8. Delete the deployments (service first, then app)for the next step using: 
`kubectl delete -f sparta-nodejs-app-deploy.yaml`
`kubectl delete -f sparta-app-service.yaml`

### Making database and service deployment .yaml files (and PVC .yaml file)

1. Now that we have our app and service deployments running, we can add in the database and connect them all up. We need three more .yaml files now in our directory:
	- db-deploy.yaml this will define our database deployment
	- db-service.yaml this will define our database service
	- db-pvc.yaml this will define a PersistentVolumeClaim which will make sure we don't lose our database data between the creation and deletion of deployments and pods. 

#### db-deploy.yaml
``` yaml
# YAML is case sensitive
apiVersion: apps/v1  # specify api to use for deployment
kind: Deployment  # kind of service/object you want to create
metadata:
  name: db-deployment # name the deployment
spec:
  selector:
    matchLabels:
      app: db  # look for this label/tag to match with k8 service
  # create a replica set of this with instances/pods
  replicas: 1 # we only need one replica of the database pod as it will confuse the app and database services otherwise
  template:
    metadata:
      labels:
        app: db # this label connects the deployment to the service
    spec:
      containers:
      - name: db-container
        image: mongodb/mongodb-community-server:7.0.6-ubuntu2204 # the image you created to run nginx in a container
        ports:
        - containerPort: 27017 # port to expose in the container - needs to match targetPort in the service yml file
        volumeMounts:
        - name: db-storage
          mountPath: /data/db # path inside the container where the volume will be mounted
      volumes:
      - name: db-storage
        persistentVolumeClaim:
          claimName: db-pvc # this should match the name of the PVC defined in the PVC yaml file
```
#### db-service.yaml
``` yaml
apiVersion: v1
kind: Service
metadata:
  name: db-svc
  namespace: default
spec:
  selector:
    app: db  # this label connects this service to the deployment
  ports:
  - protocol: TCP
    port: 27017 # service's own internal port
    targetPort: 27017 # port that db listens on inside the db deployment pod - needs to match containerPort in the deployment yml file
```
#### db-pvc.yaml

``` yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: db-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
  storageClassName: hostpath # use hostPath for local development; for production, use a cloud provider's storage class
```

2. Once we have these files set up we can deploy everything in this order:
	1. db-pvc.yaml
	2. db-deploy.yaml
	3. db-service.yaml
	4. sparta-nodeJS-app-deploy.yaml
	5. sparta-app-service.yaml
NB: When we destroy these deployments, it's best to follow the list in reverse.

3. We want to seed our database, we can do that using:
`kubectl exec --it <pod name reference> -- sh` this will tell kubectl to send a command to the pod, using `--it` to make it interactive, `--` to separate the command to send and `sh` is the command we want to run so in this case it's telling it to run a shell session. This will open a prompt where you can run: 
`node seeds/seed.js`
4. We can now go to `http://localhost:31704/posts` to make sure the database has been seeded. 

### Scaling our app deployment pods
If we wanted to reduce or increase the number of replica pods that k8s deploys, there are 3 ways we could do this:
- `kubectl scale --current-replicas=3 --replicas=4 deployment.apps/sparta-nodejs-app-deployment` This command tells kubectl that we want to scale the deployment defined, from 3 replicas to 4 replicas. 
- `KUBE_EDITOR="nano" kubectl edit deploy sparta-nodejs-app-deployment` This command tells kubectl that we want to edit the file that it is currently using to handle the deployment. This will open the file in nano and once you exit out of it (saving changes) it will apply the changes automatically. I have specified the editor to use as by default it uses vim and I am not good at vim...
- We can also change the sparta-nodeJS-app-deploy.yaml directly and then run: `kubectl apply -f sparta-nodeJS-app-deploy.yaml`
## Other useful Kubernetes commands
- `kubectl get pods -w` lists the pods and watches for changes (Ctrl+C to escape out of this)
- `kubectl get all` lists all the kubernetes objects
- `kubectl get srv` lists the services 
- `kubectl logs <container-ref>` gets the logs for the container referenced

---
#Kubernetes [[BeckyWhiteObsidian/Job-And-Career/Tech Stack Index/Kubernetes|KubernetesBeckyWhiteObsidian/Job & Career/Tech Stack Index/Kubernetes|Kubernetes]]
