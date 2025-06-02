What is Ansible?
- Configuration Management Tool
- RedHat leads development of this tool
- Open source
- Written in python
- Started off having a few core modules for managing/configuring Linux servers and it has expanded since then

Main use cases
- Configuration Management (installing software and settings)
- Application deployment
- Can be used as an orchestration tool but not designed for it

Advantages
- Works with almost any system (linux and windows, routers, switches, cloud providers etc. )

How does it work?
- "recipes" for what you want, written in yaml, called playbooks
- inventory used to specify the machines/devices that it needs to configure
- machines/devices it configures are called target nodes, not agents
- agent-less architecture
- accesses the target nodes through SSH
- ansible machine that's doing the configuring, where you store the playbooks and inventory is called the controller
- requires a python interpreter on target nodes and controller
- 

Who's using Ansible?