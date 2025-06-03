## What is a Traditional Architecture?

DIAGRAM

## What is Virtualisation?

![[IMG_2293.jpeg]]

- The Virtualisation layer handles how much of the hardware resources the VMs can use.
- Always running when not in use.
- Usually runs out of processing power.

## What is Containerisation?

![[IMG_2293 1.jpeg]]

- Containerisation software will identify all the things needed to run the application, such as dependencies etc, build it into the application, run whole container.
- Containers only run when they have something to do.

**Benefits**:
- Portability - No need to rewrite code for different systems, runs same on any OS
- Scalability - Lightweight and efficient compared to VMs
- Fault Tolerance - You can isolate individual parts of software. One faulty container will not be a big problem and it'll be obvious where the issue is
- Agility - Changes can be made without interfering with OS or hardware
- It's simple and easy to use
- Abstracts you away from a lot of issues and allows you to do more important work, more efficiently (You don't have to spend time making VMs all day, every day)

