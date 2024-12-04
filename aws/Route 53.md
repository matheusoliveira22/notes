### Record Types
- A – maps a hostname to IPv4
- AAAA – maps a hostname to IPv6
- CNAME – maps a hostname to another hostname
	- The target is a domain name which must have an A or AAAA record
	- Can’t create a CNAME record for the top node of a DNS namespace (Zone
Apex)
	- Example: you can’t create for example.com, but you can create for
www.example.com
- NS – Name Servers for the Hosted Zone
	- Control how traffic is routed for a domain

### Hosted Zones
- A container for records that define how to route traffic to a domain and
its subdomains
	- Public Hosted Zones – contains records that specify how to route
traffic on the Internet (public domain names).
		 Example: application1.mypublicdomain.com
	- Private Hosted Zones – contain records that specify how you route
traffic within one or more VPCs (private domain names)
		Example: application1.company.internal

### CNAME vs Alias
- AWS Resources (Load Balancer, CloudFront...) expose an AWS hostname:
	- lb1-1234.us-east-2.elb.amazonaws.com and you want myapp.mydomain.com
- CNAME:
	- Points a hostname to any other hostname. (app.mydomain.com => blabla.anything.com)
	- ONLY FOR NON ROOT DOMAIN (aka. something.mydomain.com)
- Alias:
	- Points a hostname to an AWS Resource (app.mydomain.com => blabla.amazonaws.com)
	- Works for ROOT DOMAIN and NON ROOT DOMAIN (aka mydomain.com)
	- Free of charge
	- Native health check
	- Can't set TTL
	- Alias Record is always of type A/AAAA
	- Targets:
		- Elastic Load Balancers
		- CloudFront Distributions
		- API Gateway
		- Elastic Beanstalk environments
		- S3 Websites
		- VPC Interface Endpoints
		- Global Accelerator
		- Route 53 record in the same hosted zone
		- You cannot set an ALIAS record for an EC2 DNS name

### Routing Policies
- Simple (One or more values per record - Except when using alias - Can't use health checks)
- Weighted (Control % of the requests that go to each resource)
	- 1 record with 0 weight - No traffic to that record
	- All records with 0 weight - Distributed equally
- Failover - Automatically changes the traffic to the Secondary instance if the Primary doesn't pass on Health Check
- Latency - Based on traffic between users and AWS Regions
- Geolocation - Based on user location
- Multi-Value Answer - Similar to Simple with multiple values, but enable health checks
- IP based
- Geoproximity
	- Must use Route 53 Traffic Flow feature
	- Enable the ability to shift more traffic to resources based on the defined bias


### Health Checks
- HTTP Health Checks are only for public resources
- Health Check == Automated DNS Failover. Types:
	- Monitor an endpoint (app, server)
	- Monitor other health checks (Calculated Health Checks)
		- Combine results of multiple Health Checks into one
		- Can use OR, AND or NOT
		- Can monitor up to 256 Child Health Checks
		- Specify how many of the health checks need to pass to make the parent pass
	- Monitor CloudWatch Alarms (Useful for Private Hosted Zones since global  health checks can't reach them)
- Are integrated with CW metrics
- About 15 global health checkers will check the endpoint health
- Pass only when the endpoint responds with 2xx and 3xx status code
- Can be setup to pass/fail based on the text in the first 5120 bytes of the response
