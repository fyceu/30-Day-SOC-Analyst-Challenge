## Installing Sysmon
Within the Windows Server, navigate to the following link to download Sysmon:
- https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
	- Extract the downloaded folder

We also want to download the Olaf Sysmon Configuration File:
- https://raw.githubusercontent.com/olafhartong/sysmon-modular/master/sysmonconfig.xml
	- download the .xml file into the Sysmon folder we just extracted

Next, open up PowerShell with admin privileges
- cd to the Sysmon directory
- Run the following command to install Sysmon
```PowerShell 
.\Sysmon64.exe -i sysmonconfig.xml
```

You should see the following if installed correctly:
![Installed](https://github.com/user-attachments/assets/a778f3fb-dc45-4241-b0f6-d5f4bddc2610)

You can also verify proper installation by checking Windows Services and Event Viewer

In Event Viewer: Application and Services Logs > Microsoft > Windows > Sysmon

![eventViewer](https://github.com/user-attachments/assets/3f91141e-0c43-42e6-8d00-1b46b3fd47a9)


![Services](https://github.com/user-attachments/assets/b90b00bb-afe3-453d-85d7-77f00e478dad)
