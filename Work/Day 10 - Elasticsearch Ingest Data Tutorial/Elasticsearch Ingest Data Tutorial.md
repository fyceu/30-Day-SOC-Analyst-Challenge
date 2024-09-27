
## Integrations

First we need to access our Elastic dashboard
- Navigate to the left-side menu > Management > Integrations
- Find the "Custom Windows Event Logs" Integration and add it

Below are the configurations for my integration
- Ensure the channel name is set to Sysmon's FullName: ```Microsoft-Windows-Sysmon/Operational```
- Add the integration to the Windows Policy we created in Day 7

![winEventLogConfig](https://github.com/user-attachments/assets/8daa6559-1972-49ef-b148-e20ed72343df)


We will do the process again using the same integration, creating an integration for Windows Defender Logs: 

By default, Windows Defender generates a lot of logs, some of which are just informational. This can create a lot of noise and utilize a lot of storage over a long period of time.
In this lab, we will focus on logs with the following Event IDs:
- Event ID 1116
- Event ID 1117
- Event ID 5001 

Below are the configurations for Wind-Defender
- Channel Name: ```Microsoft-Windows-Windows Defender/Operational```
- Open advanced and add the three Event ID's
- Set the policy host to the Windows Policy we created in Day 7 

![winDefenderIntegration](https://github.com/user-attachments/assets/c8cc38d2-0236-41a1-ae5b-2bc931dbce88)
