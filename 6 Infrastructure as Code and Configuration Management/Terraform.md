## What is Terraform? What is it used for?
- Sees infrastructure as immutable and therefore disposable
- Code used: HCL (Hashicorp Configuration Language)

## Why use Terraform? The benefits?
- Easy to use
- Free and open source
- Declarative
- Cloud-agnostic (you can deploy to any cloud providers)
	- To do this it uses "providers" which acts as an interface with the API of the cloud provider
	- Each cloud provider maintains their own "provider"
- Expressive language
- Extensive (eg. hundreds of plugins to expand on functionality)

## Who is using Terraform in the industry?
- Tech Companies and Startups:
    - Uber, Spotify, Airbnb, Coinbase
- Financial Institutions (regulated industry):
    - JPMorgan Chase, Goldman Sachs, Capital One
3. Cloud Providers and SaaS Platforms:
    - AWS, Google Cloud, Salesforce
4. Media and Entertainment:
    - The New York Times, Netflix
5. Healthcare (regulated industry) and Life Sciences:
    - Philips, Cerner
6. Telecommunications:
    - Verizon, T-Mobile
7. Retail and E-Commerce:
    - Walmart, Target
8. Gaming Industry:
    - Electronic Arts (EA), Riot Games (they make/run League of Legends)
9. Government and Public Sector:
    - UK Government Digital Service (GDS), NASA
10. Consulting and Cloud Services:
    - Accenture, Deloitte
11. Education and Research Institutions:
    - Harvard University, MIT

## In IaC, what is orchestration? How does terraform act as "orchestrator"?
- Takes care of how and the order in which to do things

## Best practice when supplying AWS credentials to Terraform


## Order it looks for credentials:
1. Env variables: AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY
2. Terraform variables - as values set in your code (best practice is to not hard code credentials in code)
3. AWS CLI, then you run command: `aws configure`
4. On AWS, your EC2 instance, if you give the instance IAM permissions (best & most secure)

## Why use terraform for different environments? (eg production, testing etc.)
- Often very similar to other environments such as dev, testing, QA, staging:
	- Very easy to modify and scale

Development + Testing environment
- Very easy to create and destroy

For Disaster Recovery
- Versioning is easier
- Easy to re-create in another region or even cloud provider

## How do we use Terraform?
Write, Plan, Apply.
- Apply will generate the state file where Terraform can track the all the resources it's created.

We can use different workspaces for different services, for example, one for our Monitoring service and one for our shared databases. 



## .gitignore:
.terraform.lock.hcl
After selecting a specific version of each dependency, Terraform remembers the decisions it made in a dependency
Lock the file so it can (by default) make the same decisions again in future.
One team needs to be using the same dependencies and provider version across a project, else there will be problems. The versions can change but the team needs to all be using the same versions. 



## Configuration Drift

Where the configuration of resources change over time and diverge
to check for configuration drift that has been done using, say, an extra tag rather than an in-place modification, use `terraform plan` to check for "changes", terraform will tell us if the plan is different from the state of the resource. In this case, we can run `terraform apply` to put the resources back to how the code defines. 

If a change has been made in-place, we can use configuration management tools such as Ansible to check for configuration drift for us.

---
#### Tags and Links 
#Git 
#terraform

[[BeckyWhiteObsidian/Job & Career/Tech Stack Index/Terraform|Terraform]]