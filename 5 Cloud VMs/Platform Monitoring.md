Contents:
- [[#Creating a Dashboard]]
- [[#Setting up an alert]]
- [[#Steps for deleting VM instances in an instance group]]
## Creating a Dashboard
1. Navigate to VM instance you want to monitor and go to the "Observability" tab: ![[Pasted image 20250509155237.png]]

2. For this example, we're going to be making a dashboard to monitor the CPU Utilization and Network Traffic of our VM. We can either use the kebab menu and select "View in full screen" or just click the graph and search icon just to the left of the kebab menu. ![[Pasted image 20250509160115.png]]

3. This will now take us to the graph for the CPU Utilization. I had to remove the filter and change the filter to "instance_name=tech504-becky\[...]" this will then give us the correct view. Once we have the view we want, we can click "Save to dashboard" ![[Pasted image 20250509160540.png]]

4. Name the chart something sensible, I just added my name and the fact it was my app VM. Select the dropdown for the Dashboard and Select "New Dashboard", it will then ask you to put in a name for the new dashboard, I went with "tech504-becky-app-dashboard" to be clear what it was the dashboard is used for. Click "Save Chart" once done and then click "Cancel" to go back to the Observability page. ![[Pasted image 20250509161510.png]]

5. Follow the same steps as above to add the Network Traffic to the dashboard.

6. To navigate to the dashboard, click the hamburger menu in the top left of the webpage, this will open the navigation, then go to "Monitoring" -> "Dashboards" ![[Pasted image 20250509162109.png]]

7. In the Dashboards page, I find it easier to use the filter as there are lots of dashboards listed by default. Select your dashboard and you will be presented with the graphs you added to your dashboard. ![[Pasted image 20250509162340.png]]

8. Don't forget to click the button to enable auto-refresh! ![[Pasted image 20250509162544.png]]


9. Now we want to try and make a spike in our graphs. We can do this by installing an apache utility which can send requests to our server for us using:
`$ sudo apt-get install apache2-utils`
`$ ab -n 1000 -c 100 http://34.1.1.205/`

1000 requests to that url (number)
blocks of 100 at a time (concurrency)

## Setting up an alert
1. On dashboard, click convert to alert chart which will bring up Create alerting policy ![[Pasted image 20250515153445.png]]

2. Under "Select a metric", "VM Instance - CPU utilization" should be auto filled. Click "Next". ![[Pasted image 20250515153755.png]]

3. Leave the settings as they are except we need to set a threshold value and a name for the Condition. I went with 6% as I want to be able to get an alert without sending too many requests. Under "Advanced Options" we can set a "Condition name" which is helpful to identify the use of the condition, I went with "CPU use for tech504-becky-app-from-image-vm over 6%". Click "Next". ![[Pasted image 20250515154351.png]]

4. Under "Notification channels" find your email, mine is called "Becky email" (Add email if needed by clicking "Manage Notification Channels" -> add new under email) ![[Pasted image 20250515154454.png]]

5. Set the "Notification subject line" to something sensible such as "CPU usage on app VM over 6%" ![[Pasted image 20250515154538.png]]

6. Name the alert policy -> Alert policy name: CPU utilization for tech504-becky-app-from-image-vm (Can also set the severity level) ![[Pasted image 20250515154840.png]]

7. Try to trigger the alert using via SSH console: 
`$ sudo apt-get install apache2-utils`
`$ ab -n 1000 -c 100 http://34.1.1.205/`
8. Check for alert email

## Steps for deleting VM instances in an instance group
1. Delete the load balancer
    - Choose to delete the backend service and health check at the same time
    - If any issues doing this, you will need to clean in this order manually:
        1. Load balancer
        2. Backend service
        3. Instance group
        4. Health check
2. Delete the instance group
3. Important!
    - Backend service must be deleted before the instance group as the backend depends on the instance group
    - The health check is NOT deleted automatically when the instance group is deleted
4. Delete health check if you did not do it earlier
5. Remove the extra subnet made for the load balancer

Alternatively, disable backend from load balancer, delete instance group, delete load balancer (along with backend and health check)

---




#### Tags and Links 
#GCP 
#cloud 
[[The Cloud]] 
[[Cloud]] 
[[Platform Monitoring]] 
[[How to deploy on GCP for high availability and scalability (and security)]]