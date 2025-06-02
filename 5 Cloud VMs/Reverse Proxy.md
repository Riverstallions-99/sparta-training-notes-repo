A reverse proxy intercepts and redirects network traffic to back-end servers. 
We have been using nginx to do this, nginx can also handle load balancing. 

Benefits of using a reverse proxy include:
- Security - Abstracts the back-end servers so they're not exposed to all network traffic, this is a common practice in DevOps and development generally where we only expose the data that is absolutely needed (Another example would be abstraction and encapsulation in Object Oriented Programming)
- Scalability - Allows for the easy adjustment of the back-end servers to get up and running if traffic increases past a point that a server can't handle anymore. 
- Availability (up time performance) - By effectively managing the network traffic for the back-end server/s you mitigate the risk of overloading and crashing the server/s, this decreases down-time and therefore increases availability. Additionally if you had two back-end servers in different regions, the reverse proxy can handle sending requests to the functional server if one goes down, thus increasing availability, even when something goes wrong. 

#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]