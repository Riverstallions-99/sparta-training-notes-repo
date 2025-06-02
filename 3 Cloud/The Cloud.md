 #cloud #GCP 
### Questions  
- [[#Factors to decide whether something is in the cloud]]
- [[#4 Types of Cloud]]
- [[#Types of Services]]
- [[#Is cloud more secure than on-prem?]]
- [[#Advantages and Disadvantages]]
- [[#Market Share]]
- [[#Which cloud provider is best?]]
  
### Factors to decide whether something is in the cloud  
- Are the resources/services delivered as a service over the internet?  
- Are the resources available on demand?  
- Are the resources/services centrally managed?   
  
SRE - Site Reliability Engineer  
  
### 4 Types of Cloud  
- Public:  
  - "Multi-tenant cloud": multiple occupants/residents on the cloud  
  - use by/shared with the public  
  - Gov't often have their own cloud separate  
- Private:  
  - "Single-tenant cloud": one occupant/resident on the cloud  
  - cloud infrastructure that is dedicated to a private company (owned or rented from 3rd party)  
  - used in situations where there is no internet (e.g. cruise ship)  
- Hybrid:  
  - Mix of on-prem and on public/private cloud  
  - May be required to meet security compliance standards (e.g. store data on-prem)  
- Multi-cloud:  
  - A mix of cloud providers ( eg. Azure + AWS, GCP + Azure)  
  
### Types of Services  

![[Pasted image 20250508190454.png]]


  
### Is cloud more secure than on-prem?  
- Depends on which services you intend to use, depends on how much responsibility you're giving to the provider.  
  
### Advantages and Disadvantages  
- If hybrid or multi-cloud arrangement:  
  - Dis:  
    - Complicated  
    - Level of expertise also increased  
  - Adv:  
    - .  
  
### Market Share  
- Amazon biggest  
  
### Which cloud provider is best?  
Depends on your use case
## What is GCP?  
GCP - Google Cloud Platform  
This is what we will be using to learn about cloud services.  
Google Cloud is not the same as GCP, Google cloud is a little more extensive and includes GCP  
  
- [GCP History](#gcp-history)  
- [Regions](#regions)  
- [Why use GCP](#why-use-gcp)  
- [Structure of GCP](#structure-of-gcp)  
- [Ways to access GCP](#ways-to-access-gcp)  
  
### GCP History 
Started 2008 (2 years after AWS), more in dev until 2011  
first service - app engine  
  
### Regions  
24 regions  
  
### Why use GCP?  
- VM pricing is very competitive  
- Big Data  
  
### Structure of GCP  
- 4 levels with GCP for organisation of resources + help set permissions/roles  
  1. Organisation (eg. Company)  
  2. Folders (eg. Department X, Team A, Product 1)  
  3. Projects (eg. Development Project)  
  4. Resources (eg. IAM, )  
  
### Ways to access GCP  
- GUI called cloud console  
- CLI called gcloud  
- Other tools (eg. Ansible, Terraform)