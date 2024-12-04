### Read replicas
- Up to 15 Read replicas
- Within AZ, Cross AZ or Cross Region
- Replication is async
- Replicas can be promoted to their own DB
- There aren't network cost for RDS read replicas within the same region

### Backups
- Automated backups:
	- Daily full backup of database
	- Ability to restore to any point in time 
		- RDS: from oldest backup to 5 min ago
		- Aurora: point-in-time recovery in in the retention window set
	- Retention: 1 to 35 day of retention
	- RDS - Can be enabled or disabled
	- Aurora - Cannot be disabled
- Manual DB Snapshots:
	- Manually triggered by the user
	- Retention: As long as the user wants

### Multi AZ (Disaster Recovery)
- Sync Replication
- One DNS name - Automatic app failover to standby
- **Not used for scaling - Standby database only waits until main database are unavailable**
- The read replicas can be setup as Multi AZ for Disaster Recovery
- To modify a RDS database from Single-AZ to Multi-AZ, there's no downtime in the database. Internally, that'll happen
	- A snapshot is taken
	- A new DB is restored from the snapshot in a new AZ
	- Synchronization is established between the two databases

### Amazon RDS Proxy
- Fully managed database proxy for RDS
- Allows apps to pool and share DB connections established with the database
- Improve database efficiency by reducing the stress on database resources (e.g. CPU, RAM) and minimize open connections (and timeouts)
- Serveless, autoscaling, highly available (Multi-AZ)
- Reduced Failover time
- Supports RDS (MySQL, PostgreSQL, MariaDB, MS SQL Server) and Aurora
- Enforce IAM Authentication for DB
- RDS Proxy is never publicly accessible

### Aurora Advanced
- Aurora Replicas - Auto Scaling:
	- Aurora could be setup to auto scale the number of reader instances to match the current needs
- Aurora - Custom Endpoints:
	- Aurora Read Replicas can be of different instances sizes, so, you can setup a custom endpoint to point direcly to a specific subset of this instances (Example: A Custom Endpoint only to perform analytics jobs in a powerful instance)
- Aurora Serverless:
	- Automated database instantiation and auto-scaling
	- No capacity planning needed
- Global Aurora:
	- Aurora Cross Region Read Replicas:
		- Useful for disaster recovery
		- Simple setup
	- Aurora Global Database (recommended):
		- 1 Primary Region (read / write)
		- Up to 5 secondary (read-only) regions, replication lag less than 1 sec
		- Up to 16 Read Replicas per secondary region
		- Promoting another region (for DR) with RTO of < 1 minute
		- Typical cross-region replication time < 1 second
	- Aurora Machine Learning
		- Enable ML-based preditions to the applications via SQL
		- Simple, optimized and secure integration between Aurora and AWS ML services
		- Supported Services:
			- Amazon SageMaker (any ML model)
			- Amazon Comprehend (sentiment analysis)
	- Aurora Database Cloning
		- Create a new Aurora DB Cluster from an existing one
		- Faster tha snapshot & restore because it uses the copy-on-write protocol