- EC2 stands for Elastic Compute Cloud (Virtual Machines)
- Bootstrap script - User data - Rubs with root account
- Firewall rules - security groups
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
- Memory Optimized
	- Fast performance for workloads that process large datasets in memory
	- Use cases: Relational/Non-relational databases, Distributrd web scale cache