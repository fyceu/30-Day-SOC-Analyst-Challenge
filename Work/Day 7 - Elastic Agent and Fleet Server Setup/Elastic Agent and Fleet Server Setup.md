
## EC2 Instance Setup
Fleet Server Instance Configurations:
- Ubuntu Server 22.04 LTS
- 2 vCPU, 4GB Memory
- 30GiB 
- Added to VPC
- Added to subnet-public1
- Add to security group that Elastic Server is in 

Once we provision this instance, we will need to assign an Elastic IP to it. 
- Allows a static IP to our instance even upon instance restart
- Elastic IP > Allocate Elastic IP > Allocate > Choose EC2 Instance
## Network 

The Fleet Server and the Windows Server are in two different VPCs. Therefore, they are unable to communicate directly with one another. However, we can allow communication between servers by adjusting our Security Groups.

Fleet Server security group:
- Allow WindowsWorkstationElasticIP via port 8220 
- Allow WindowsWorkstationElaticIP All ICMP - IPv4 (**optional, used for ping testing**)

Windows Workstation:
- Allow FleetServerElasticIP via port 8220

Below are my INBOUND security groups for my Fleet Server and Windows Server respectively:
![Fleet-Elastic-SecurityGroup](https://github.com/user-attachments/assets/43c71684-2352-4c2d-a932-3b6a96304b39)


![WindowsServer-SecurityGroup](https://github.com/user-attachments/assets/b2dd2348-6f4d-4d80-a9e7-0285212f102f)

## Installing Fleet

Head to Elastic web GUI
- Open left-side menu > Management > Fleet > Add Fleet Server
	- Add a name and the Elastic IP of  the Fleet Server
	- Copy and paste the installation code onto Fleet Server's command line
		- Once finished Installing you should be able to move onto the next section in the GUI
- Keep this tab open
- Open another tab and go to Elastic > Management > Fleet > Settings
	- We need to change port of Fleet Server from 443 to 8220

![changeIP](https://github.com/user-attachments/assets/c37547ce-6229-4ba9-bd91-5ed6847fd240)

Once changed, click on Agents > Add agent 
- Create Agent Name
- Enroll in Fleet 
- Copy the Elastic Agent installation for Windows machine  
	- Ensure last line has FleetServerElasticIP:8220
- Boot up Windows server and open up PowerShell with administrator privileges
	- Paste the code and append ```--insecure``` at the end
	- Run code

![successfullyEnrolled](https://github.com/user-attachments/assets/b24387e5-5936-4623-9b49-e16e85402834)

If you successfully installed the Elastic Agent, after a few minutes logs should begin to ingest onto Elastic!
![logs](https://github.com/user-attachments/assets/8c8cf8e4-7569-4301-98e1-280c644fd240)

## Troubleshooting

If you are still having trouble refer to Elastic's documentation: 
https://www.elastic.co/guide/en/fleet/current/add-fleet-server-on-prem.html