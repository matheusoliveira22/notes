- Firewall rules that are the fundamental of network security in AWS
- They control how traffic is allowed into or out of an instance
- They only contain allow rules
- Can reference by IP or by Security Group
- The security group can regulate:
	- Authorized IPs ranges - IPv4 and IPv6
	- Access to Ports
- Can be attached to multiple instances
- They are locked down to a refion / VPC combination
- The SG lives outside the EC2, like this, if an request is blocked, the insance will not notice it
- It's good to maintain one separated SG for ssh connection
- Error handling:
	- If the application is not accessible (time out), then it problably means that is an SG issue
- By default all **inbound traffic** is **blocked** an all **outbound traffic** is **authorized**

### Classic Ports to know
- 22 - SSH (Secure Shell)
- 21 - FTP (File Transfer Protocol)
- 22 - SFTP (Secure File Transfer Protocol) - via SSH
- 