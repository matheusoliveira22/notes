- EC2 stands for Elastic Compute Cloud (Virtual Machines)
- Bootstrap script - User data - Rubs with root account
- Firewall rules - [[Security Groups]]
- SSH Keypair must be set at creation

### EC2 Instance Types
Name convention:
- m5.2xlarge
	- m: instance class
	- 5: Generation (AWS improves over time)
	- 2xlarge: Size withing instance class
- Intance classes
	- General Purpose: Great for a diversity of workloads such as web servers
	- Balance Between: compute, memory and networking
- Compute Optimized (C)
	- Great for computr-intensive tasks that require high performance processors
	- Workloads examples: Batch processing, Media transcoding, HP (high performance) web servers, HP Computing, Scientific Modeling & Machine Learning, Dedicated Game Servers
- Memory Optimized (R, X, High Memory, z)
	- Fast performance for workloads that process large datasets in memory
	- Use cases: Relational/Non-relational databases, Distributrd web scale cache, In-memory databases for BI, Applications performing real-time processing of big unstructured data
- Storage Optimized (I, D, H)
	- Great for storage-intensive tasks
	- Examples: Cache for in-memory caches, Data warehousing applications, Distributed File Systems

### EC2 Purchasing Options
- On-Demand Instances
- Reserved (1 & 3 years) -> Convertible Reserved Instances (flexible instances)
- Savings Plan (1 & 3 years)
	- Locked to specific instance family and AWS region
- Spot Instances - most agressive discount (can lose instances)
	- Spot Fleet - Spot Instances + (optional) Dedicated Hosts - Will try to meet capacity requirements with price constraints. It allow us to automatically request spot instances with the lowest price
	- Strategies:
		- lowestPrice
		- diversified
		- capacityOptimized
		- priceCapacityOptimized (recommended)
- Dedicated Hosts (Entire Fisical Server)
	- Use Cases: Compliance Requirements, server-bound software licenses
- Dedicated Instances (Not sharing hardware with other costumers)
- Capacity Reservation (Reserve capacity in an specific AZ for any duration)
	- No billing discount
	- Charged by On-Demand rate even if you not run the instances
### EC2 Public IP
- The common way EC2 handle public IP, is that every time it reboots, a new IP is assigned to it
- A way to change that is to use **Elastic IPs** (public IPv4). You can have up to 5 Elastic IPs in an account, and it can be assigned to only one instance at a time.
- Note that the usage of Elastic IPs for that purporse is disregarded, since there are better ways of architecturing it, like using random public IPs and assign an DNS name, or not use public IP and use a load balancer

### Placement Groups
- Sometimes you may want to control the EC2 placement strategy. That can be achieve through **Placement Groups**
- Strategies:
	- Cluster: Cluster instances in a Low-latency group in an single AZ
	- Spread: 
	- Partition: 