# MCOnDemand

## What is MCOnDemand

At its core, **MCOnDemand is a system for managing and deploying ephemeral Minecraft servers.**

Let's break that down...

### What is an "ephemeral Minecraft server"?

Simply put, an ephemeral server is a temporary server.
The server exists while it is running a certain process--like a web server, database, or web crawler--, and once the process it is running is no longer needed, the server shuts down, releasing its resources.
Ephemeral servers provide on-demand compute resources, helping service providers scale when there is high demand for their service, then quickly scale back when demand is reduced.
In the context of Minecraft, this means providing servers which can be started quickly, but also easily shut down depending on player demand.
All together, **an ephemeral Minecraft server is a type of server which can be easily started to meet player demand, but then shut down to reduce cost when nobody is playing.**

### What does it mean to deploy ephemeral Minecraft servers?

Deployment is the process of starting a server with everything necessary for it to run properly.
After the deploy process is triggered, the first step is starting a virtual machine for the server to run on.
In this step, MCOD requests a new virtual machine from whatever system is being used to manage compute resources (DigitalOcean, k8s, GCloud, etc.).
This virtual machine is loaded with an image containing up-to-date copies of the MCOD server-side software which allows the server to communicate with MCOD core servers and save data, among other features.
At this point, the software installed on the virtual machine contacts MCOD servers, retrieving all of the configuration information and files necessary for it to run the Minecraft server.
This includes server configs, world files, and the Minecraft binary.
Finally, the Minecraft server is started and players are able to join the server and play.

### What does it mean to manage ephemeral Minecraft servers?

After a server is deployed, MCOD manages the server, monitoring its status and shutting down the virtual machine when the server is no longer in use.
To monitor the status of servers, MCOD servers expect regular messages from MCOD daemons (possibly HTTP messages, otherwise long-term connection like Websockets w/ regular heart beats).
If a server does not send status updates, the management process will consider a server dead, marking it for shut-down.
On a regular interval, another thread in the management process checks for servers that have been marked for shut-down, then shuts down the virtual machine, releasing its resources.


## MCOnDemand Internal Pages

### Systems

- [Bedrock](/bedrock) -- This is the "monolithic backend service" which forms the foundation of all of MCOD's functionality.
This system was designed before Feb 2021, so it may now be outdated.
The documents contain some ideas which may be helpful even if other ideas are outdated.
