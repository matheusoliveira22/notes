### EBS - Elastic Block Store
- An EBS is an network drive
- It allows data to be persisted even after the instance is terminated
	- Root volumes have the delete on termination atrribute set by default
- Can be assigned to only one instance at a time (except multi-attach feature)
- They have a provisioned capacity
- They are locked in an specific AZ
	- To move an EBS volume from an AZ to another AZ or Region, first you must take an snapshot of it, and then create a new volume in the desired location
- EBS Snapshots features:
- 