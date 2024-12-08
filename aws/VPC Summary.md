• CIDR – IP Range
• VPC – Virtual Private Cloud => we define a list of IPv4 & IPv6 CIDR
• Subnets – tied to an AZ, we define a CIDR
• Internet Gateway – at the VPC level, provide IPv4 & IPv6 Internet Access
• Route Tables – must be edited to add routes from subnets to the IGW, VPC Peering
Connections, VPC Endpoints, …
• Bastion Host – public EC2 instance to SSH into, that has SSH connectivity to EC2
instances in private subnets
• NAT Instances – gives Internet access to EC2 instances in private subnets. Old, must
be setup in a public subnet, disable Source / Destination check flag
• NAT Gateway – managed by AWS, provides scalable Internet access to private EC2
instances, when the target is an IPv4 address
• NACL – stateless, subnet rules for inbound and outbound, don’t forget Ephemeral
Ports
• Security Groups – stateful, operate at the EC2 instance level
• VPC Peering – connect two VPCs with non overlapping CIDR, non-transitive
• VPC Endpoints – provide private access to AWS Services (S3, DynamoDB,
CloudFormation, SSM) within a VPC
• VPC Flow Logs – can be setup at the VPC / Subnet / ENI Level, for ACCEPT and
REJECT traffic, helps identifying attacks, analyze using Athena or CloudWatch Logs
Insights
• Site-to-Site VPN – setup a Customer Gateway on DC, a Virtual Private Gateway on
VPC, and site-to-site VPN over public Internet
• AWS VPN CloudHub – hub-and-spoke VPN model to connect your sites
• Direct Connect – setup a Virtual Private Gateway on VPC, and establish a
direct private connection to an AWS Direct Connect Location
• Direct Connect Gateway – setup a Direct Connect to many VPCs in different
AWS regions
• AWS PrivateLink / VPC Endpoint Services:
• Connect services privately from your service VPC to customers VPC
• Doesn’t need VPC Peering, public Internet, NAT Gateway, Route Tables
• Must be used with Network Load Balancer & ENI
• ClassicLink – connect EC2-Classic EC2 instances privately to your VPC
• Transit Gateway – transitive peering connections for VPC, VPN & DX
• Traffic Mirroring – copy network traffic from ENIs for further analysis
• Egress-only Internet Gateway – like a NAT Gateway, but for IPv6 targets