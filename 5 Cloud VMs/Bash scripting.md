All bash scripts MUST start with a shbang.
`$ #!/bin/bash`

In order to make sure our script will run as intended we first must try each command manually. This also makes sure we know that no user input is needed, and if there is we can adjust our commands to ensure there is no user input needed. 

For example, if we ran:
`$ sudo apt update`

 this runs fine with no user input and pulls down which packages on our machine need to be upgraded. We can then go ahead and run:
 `$ sudo apt upgrade`
 
 and we realise that the user needs to input a Y/n option to finish the process. This obviously isn't very automated and so we can add a flag at the end:
 `$ sudo apt upgrade -y`
 
 which will automatically agree to the Y/n question.


NB: As an aside, apt is used in the command line and apt-get is used in scripting, apt is more user friendly and verbose, apt-get is more lightweight and therefore just slightly better for scripting, but it doesn't matter too much. 


### Idempotency
script can be run anywhere, multiple times with no issues/same outcome