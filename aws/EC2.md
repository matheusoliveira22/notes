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
- Spot Instances (can lose instances)
- Dedicated Hosts (Entire Fisical Server)
- Dedicated Instances (Not sharing hardware with other costumers)
- Capacity Reservation (Reserve)