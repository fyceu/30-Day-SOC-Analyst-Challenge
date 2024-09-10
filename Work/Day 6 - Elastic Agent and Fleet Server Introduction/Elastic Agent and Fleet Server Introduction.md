## Elastic Agent

Elastic Agent provides a unified method of collecting and ingesting various logs and data 
- Unlike FileBeat that has different types depending on data source
	- may require installation of multiple Beat 
	- Read more from [Day 2: ELK Stack Introduction](https://github.com/fyceu/30-Day-SOC-Analyst-Challenge/blob/main/Work/Day%202%20-%20ELK%20Stack%20Introduction/ELK%20Stack.md)

Two ways to manage Elastic Agent:
- Standalone
- Fleet Server:
	- Allows management of agent(s) from centralized location
	- easily update policies of agents, upgrades, etc.