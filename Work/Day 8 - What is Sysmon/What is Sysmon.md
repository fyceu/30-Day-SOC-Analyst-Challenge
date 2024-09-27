Sysmon (System Monitor) is a Windows service that logs system activity and forwards it to the Windows Event Log
- apart of Window's Sysinternal Suite
- Commonly used for threat detection and analysis

Examples of activity that it can monitor: 
- Process Creations
- Network Connections
- File Creations
- Command Line usage
- etc. 

Can record hashes for processes which can be combined with OSINT for Threat Intelligence

Common Event ID:
- Event ID 1: Process Creation
- Event ID 3: Network Connection
	- disabled by default, must be changed in configuration
- Event ID: 6: Driver Loaded
- Event ID 7: Image Loaded
- Event ID 8: CreateRemoteThread
- Evemt ID 10: ProcessAccess
- Event ID 22: DNS Query

You can learn more about Sysmon here:
- https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon