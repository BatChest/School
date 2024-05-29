 # Example 
- Business model: rent time on each machine
	- Problems?
	- Wasteful
![[Pasted image 20240525144928.png]]

# Example
- Developers have different compute needs 
- NeoPets2024 dev environments probably doesn't need a whole server
- NeoPets2024 prod environment probably needs more than one!
- How do you scale out as NeoPets becomes more popular?
- Multiple customers will want environment separation

# Business Model 2
'fine, since you want isolation, just send me the source code and I'll run it for you'
Problems?
- Environment control
	- We don't know that it is going to run on the hardware 
- Privacy
	- We don't want to send the source code 
- Automation
	- The service should be automated which is not done by just sending the source code
- Trust
- Complexity
- Security

We need something that can:
- Isolate environments 
- Scale flexibly 
Some kinds of abstractions layer between the metal and the software


Sounds like an operating system!
One operating system is not enough
The base OS is 1:1 with the physical machine - doesn't allow fractional allocation of resources
Not enough isolation between tenants, either

# Virtualization
- Two popular forms of virtualization
	- Virtual Machines
	- Containers 

# Virtual Machines
- Hypervisor runs on the physical machine 
- Hypervisor create multiple virtual machines
- Each virtual machine runs its own operating system
- Each virtual machine has its own resources
Virtualization of the hardware and operating system

# Downsides to VM
- Heavyweight 
- Slow to start

# Benefits of VMs
- String isolation
- Can run different operating system
- Can run legacy software
- Can run software that requires specific kernel versions

# Containers
- Shared OS kernel, separate user space and virtualized filesystem 
![[Pasted image 20240527142332.png]]

![[Pasted image 20240527142623.png]]

# Benefits of Containers
- Lightweight
- Fast to start

# Downsides to Containers
- Weaker isolation 
- Can't run different operating systems

# Container-based Architectures
- Microservices
- Serverless

![[Pasted image 20240527143541.png]]


# Software Architecture

## Monolithic Architecture 
- One big object
- Everything is running in one process
- Pencil analogy, Pencil Factory

## Service-Oriented Architecture
- Pencil making analogy
![[Pasted image 20240527161203.png]]
- We split each of these tasks into separate groups 
- One groups just makes the pencil cases while another just makes the lead 
- They need to communicate with each other with interfaces

# SOA
- Each service does one thing
	- Depends on granularity
- Services communicate with light-weight protocols 
	- Each service must advertise the functionality 
	- Each service must communicate with each other and advertise it's capabilities 

# Which architecture makes more sense to containerize
- A service 
- We could contain all these different services into a monolithic group/container and just deploy it like that
- Dockerfile 
	- ubuntu 
	- node.js
	- Renis
	- MySQL
- As long as the interface is maintained then you don't have to worry
- It's more modular 
- More isolation so dependency management easier
- Monolithic is timely coupled 
- Scalability

# Downsides to SOA
- Too many services
	- Discoverability issues
	- How do you know who does what
- complexity problems
- Learning curve
- Cost

- Sphere analogy
![[Pasted image 20240527162723.png]]


# Microservices
- Even more granular than service-oriented


# So we split the application up, now what?
Monolith to Containerized Service-Oriented 
- Step 1: decouple the major system components 
- Step 2: Containerize each component 
- Step 3: ??
- Step 4: Profit 
![[Pasted image 20240527163048.png]]

# Container Orchestration
Container Orchestration software manages:
- Provisioning resources
- Spinning up containers 
- Scaling up containers 
- Networking containers together 


# Simple Container Orchestration - Docker Compose
- Single YAML file defines the application
- Y-et
- A-nother
- M-arkup
- L-anguage
- Kinda similar to JSON 

# Complex Orchestration - Kubernetes
- Manages multiple containers across multiple machines
- Scales containers up and down
- Load balances traffic 

## Single Node
- Single machine
- Single server

## Clusters 
- Bunch of machines that are networked together
- Multiple nodes/machines

