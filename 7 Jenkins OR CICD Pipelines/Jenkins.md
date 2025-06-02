- [[#What is CI? Benefits?|What is CI? Benefits?]]
- [[#What is CD? Benefits?|What is CD? Benefits?]]
- [[#TODO Difference between CD and CDE|TODO Difference between CD and CDE]]
- [[#Why use Jenkins? Benefits of using Jenkins? Disadvantages?|Why use Jenkins? Benefits of using Jenkins? Disadvantages?]]
- [[#Stages of Jenkins?|Stages of Jenkins?]]
- [[#What alternatives are there for Jenkins?|What alternatives are there for Jenkins?]]
- [[#Why build a pipeline? Business value?|Why build a pipeline? Business value?]]
- [[#CI/CD diagram|CI/CD diagram]]
- [[#Understand SDLC workflow: plan, design, develop, deploy|Understand SDLC workflow: plan, design, develop, deploy]]
- [[#Set up a job on Jenkins:|Set up a job on Jenkins:]]
- [[#Authentication for using GitHub via Jenkins|Authentication for using GitHub via Jenkins]]
- [[#Set up a webhook between Jenkins and GitHub|Set up a webhook between Jenkins and GitHub]]
		- [[#On Jenkins Project, to webhook:|On Jenkins Project, to webhook:]]
		- [[#On GitHub repo, to webhook:|On GitHub repo, to webhook:]]
- [[#Set up a pipeline which tests, merges and deploys your code changes.|Set up a pipeline which tests, merges and deploys your code changes.]]
	- [[#Set up a pipeline which tests, merges and deploys your code changes.#Test|Test]]
	- [[#Set up a pipeline which tests, merges and deploys your code changes.#Merge|Merge]]
	- [[#Set up a pipeline which tests, merges and deploys your code changes.#Deploy|Deploy]]

# CI/CD Pipelines
## What is CI? Benefits?
- **Continuous Integration**, constantly pushing to the code in small iterations and integrating them into the existing codebase.
- Where the code is pushed depends on the git workflow for that business. Developers work on a dev branch, features/bugfixes/etc are branches off the development branch.
	- CI is pushed from the dev branch to the main branch, where the main branch is the live code-base.
- Code needs testing, if it passes the test, it gets merged/integrated into main.
- Benefits:
	- Quality checked code (automated testing)
	- Quick integration of new features
	- Quick finding of bugs/issues leads to quick fixes
	- Maintain stable software/build

## What is CD? Benefits?
- **Continuous Deployment**
	- Deploy the application, often straight to production
	- **Benefit**: End users benefit from quick code updates
- **Continuous Delivery**
	- Build the software, turn to an artifact, artifact is delivered/saved ready for deployment
	- (Usually) Deployment of the artifact depends on manual approval

## TODO Difference between CD and CDE


# What is Jenkins?
- An open source, automation server
- primarily used for CI/CD pipelines

## Why use Jenkins? Benefits of using Jenkins? Disadvantages?
-  Advantages:
	- automation
	- extensibility: more than 1800+ plugins
	- scalability: can distribute the workload across agent nodes
	- agentless? does not need to be installed on dev machines
	- huge community, lots of support
	- multi platform
- Disadvantages:
	- Complex? (Can get complex)


## Stages of Jenkins?
Test, Merge, Deploy?

## What alternatives are there for Jenkins?
- GitLab
- CircleCI
- Travis CI
- Bamboo
- GoCD
- TeamCity
- GitHub Actions
- Azure DevOps Pipelines

## Why build a pipeline? Business value?
- Consistent code (value for business and devs)
- Same standard of code
- Same testing on all code
- Frequent code updates (value for customer)

## CI/CD diagram

![[IMG_2285.jpeg]]

## Understand SDLC workflow: plan, design, develop, deploy
TODO

# Jobs on Jenkins:
## Set up a job on Jenkins:
- New Item:
	1. Name: tech504-becky-first-job
	2. Freestyle project
	3. Select: Discard old builds, we want to keep a maximum of 5 old builds
	4. Build Step -> Execute Shell:
		`uname -a`
	5. Click Save
#### Check build jobs:
1. Navigate to Dashboard, select job drop-down, select "build now"
2. Click on the job name -> select build # from left side menu -> Console output

## Authentication for using GitHub via Jenkins
We want to give the Jenkins server a private key.
We want to give the GitHub Repo a public key, we also want to enable the user of the key to write to the repo.

- **GitHub** repo -> Settings -> Security -> Deploy keys -> Add deploy key
- **Jenkins** server -> Manage Jenkins -> Security -> Credentials -> Select domain: (global) -> Add Credentials:
	- Domain: global
	- Kind: SSH Username with private key
	- ID: Use key file name
	- Desc: Short description
	- Username: Use key file name again
	- Private Key: All the private key file contents


## Set up a webhook between Jenkins and GitHub
#### On Jenkins Project, to webhook:
- Configuration -> Build Triggers -> Check: GitHub hook trigger for GITScm polling
#### On GitHub repo, to webhook:
- Settings -> Code and automation -> Webhooks -> Add webhook
- Payload URL: `http://<Jenkins-server-IP>:8080/github-webhook/`
- Click: Add webhook.


## Set up a pipeline which tests, merges and deploys your code changes.
1. [[#Test]]
2. [[#Merge]]
3. [[#Deploy]]

### Test
New Item:
- Project name: tech504-becky-job1-ci-test
- Select: Freestyle project
- Description: Test github webhook
- Check: Discard old builds -> Max # of builds to keep: 5
- Check: GitHub project -> Project url: `https://github.com/Riverstallions-99/sparta-app-for-jenkins-testing/`
- Select Git from Source Code Management
	- Repository URL: `git@github.com:Riverstallions-99/sparta-app-for-jenkins-testing.git`
	- Credentials: tech504-becky-jenkins-to-github
	- Branches to build -> Branch Specifier: `*/develop`
- Build Triggers -> Check: GitHub hook trigger for GITScm polling (See: [[#On GitHub repo to webhook]])
- Build Environment -> Check: Provide Node & npm bin/ folder to PATH: NodeJS Installation: NodeJS version 20
- Build Steps -> Execute shell: 
```bash
cd app
npm install
npm test
```

#### To change when Job 2 is written:
	- Post-build Actions:
		- Build other projects:
			- Projects to build: `tech504-becky-job2-ci-merge`
### Merge
New Item:
- Project name: tech504-becky-job2-ci-merge
- Select: Freestyle project
- Description: Merges the develop branch in my repo with the main branch
- Check: Discard old builds
	- Max # of builds to keep: 5
- Check: GitHub project:
	- Project url: `https://github.com/Riverstallions-99/sparta-app-for-jenkins-testing/`
- Select Git from Source Code Management
	- Repositories:
		- Repository URL: `git@github.com:Riverstallions-99/sparta-app-for-jenkins-testing.git`
		- Credentials: tech504-becky-jenkins-to-github
	- Branches to build:
		- Branch Specifier: `*/develop`
	- Additional Behaviours -> Merge before build:
		- Name of Repository: origin
		- Branch to merge to: main
		- Merge strategy: default
- Build Environment:
	- Check: SSH Agent: `tech504-becky-jenkins-to-github`
- Post-build Actions:
	- Git Publisher:
		- Check: Push Only If Build Succeeds
		- Check: Merge Results

**NB: Don't forget to update Job 1!**
#### To change when Job 3 is written:
	- Post-build Actions:
		- Build other projects:
			- Projects to build: tech504-becky-job3-ci-deploy
### Deploy
New Item:
- Project name: tech504-becky-job3-ci-deploy
- Select: Freestyle project
- Description: Deploys updated app code to EC2 instance
- Check: Discard old builds
	- Max # of builds to keep: 5
- Check: GitHub project:
	- Project url: `https://github.com/Riverstallions-99/sparta-app-for-jenkins-testing/`
- Select Git from Source Code Management
	- Repositories:
		- Repository URL: `git@github.com:Riverstallions-99/sparta-app-for-jenkins-testing.git`
		- Credentials: tech504-becky-jenkins-to-github
	- Branches to build:
		- Branch Specifier: `*/main`
- Build Environment:
	- Check: SSH Agent: `tech504-becky-jenkins-to-github` AND `tech504-becky-aws-key`
- Build Steps:
	- Execute shell:
```bash
echo "SSH-ing into EC2 instance to run first script..."
ssh -o StrictHostKeyChecking=no ubuntu@172.31.45.25 << EOF
    echo "removing old app..."
    sudo rm -r /home/ubuntu/app/
EOF

# SCP packaged code to hardcoded EC2 instance IP address
echo "SCP-ing packaged app to EC2 instance"
scp -rvo StrictHostKeyChecking=no app/ ubuntu@172.31.45.25:/home/ubuntu/
echo "SSH-ing into EC2 instance to run script..."
ssh -o StrictHostKeyChecking=no ubuntu@172.31.45.25 << EOF
    echo "moving into app/..."
    cd /home/ubuntu/app/
    echo "installing packages with npm install..."
    npm install
    echo "stopping old pm2 instances..."
    pm2 stop all
    echo "starting app with pm2..."
	pm2 start app.js
EOF
```
**NB: Don't forget to update Job 1!**


# Setting up own Jenkins Server
- Jenkins Server running on t3.small, as t3.micro was unusable.
- NodeJS: Available as a plugin but can also be manually installed using:
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```