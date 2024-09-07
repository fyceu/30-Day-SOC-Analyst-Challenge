## ElasticSearch
- Database used to store a multitude of log types
	- Formats logs in JSON format
- ES|QL
	- ElasticSearch Piped Query Language
- Restful-API
	- Can be used to integrate with other applications 
## Logstash
- Data processing pipeline used to ingest data from different sources, normalize it, then output it to specific "stashes" (ex: Kibana)
- Agents
	- Data shippers, used to collect telemetry on the data
	- Beats
		- File Beat - Sends Log files
		- Metric Beat - Collects system and service metrics
		- Packet Beat - Captures network traffic
		- Winlog Beat - Captures Windows events
		- Audit Beat - Monitors file integrity and audit data
	- Elastic Agent
		- Unified agent that can collect and send different forms of data from a single source
- Allows parsing of fields from data
## Kibana
- Web GUI for data visualization and data exploration
	- create dashboards or visualizations 
		- (bar charts, line graphs, heatmaps, etc)
	- Search, filter, and locate specific data stored in ElasticSearch indices
## Comparison to Splunk
- ElasticSearch = Indexer / Search Head
- Logstash = Heavy Forwarder
- Kibana = WebGUI
- Beats/Agents = Universal Forwarder
## Benefits of ELK Stack
- Centralized logging
	- meet compliance requirements and search data
- Flexibility
	- Customized ingestion
- Visualizations
	- Observe information at-a-glance
- Scalability
	- Easy to configure to handle larger environments
- Ecosystem
	- Many integrations and rich community
- Knowledge Transfer
	- Many SIEMs are built on ELK stack
	- Learning ELK could transfer over to other SIEM platforms