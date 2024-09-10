## EC2 Instance Setup

Instance Configurations:
- Windows Server 2022 Base
- 1 vCPU, 2GiB Memory
- 55 GB Storage
- Added to default VPC 
- Added to default subnet (public)
- Create new security group
	- RDP open to ALL sources

Once provision, we will need to associate an Elastic IP to this instance so it can have a static IP throughout this lab. 
- Allows a static IP to our instance even upon instance restart
- Elastic IP > Allocate Elastic IP > Allocate > Choose EC2 Instance
- We will use this IP to RDP into server and collect 

VERY low resources allocated to this instance, so don't expect it to run smoothly. That's okay though since we are only utilizing this instance to collect logs from external sources.

Make sure to save the private key/password (if you create your own make sure it is strong, we don't want external sources to access this machine, which is also why it is sitting on the default VPC and not the SOCLabVPC)