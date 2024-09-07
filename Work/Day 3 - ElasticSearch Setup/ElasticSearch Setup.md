## VPC Setup
Before we can deploy an ElasticSearch instance within AWS, we will need to configure a VPC for this lab:
![VPCconfiguration](https://github.com/user-attachments/assets/8a2f2641-a0b0-4930-9596-e8063a55fdaa)

## Creating EC2 Instance

Next, we will need to create the actual Ubuntu instance to host Elasticsearch

Instance Configurations:
- Ubuntu Server 22.04 LTS
- 4 vCPU, 16GB
- 80GiB 
- Added to VPC
- Added to subnet-public1
- New security group (allow SSH from your IP)
## ElasticSearch Installation 

Upon initial ssh to server, update repos to prevent future issues. 

```shell 
sudo apt-get update && sudo apt-get upgrade -y
```

Once completed, install ElasticSearch
- Check Elastic site if updated version exists: https://www.elastic.co/downloads/elasticsearch
```shell
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.15.1-amd64.deb
```

Install the downloaded file using

```shell 
sudo dpkg -i elasticsearch-8.15.1-amd64.deb
```

**NOTE: COPY DOWN THE SUPERUSER PASSWORD AND RESET LOCATIONS ONCE INSTALLED**

We will need to change a few things on Elasticsearch config file:
- network.host (uncomment and change IP)
- http.port (uncomment)
```shell
sudo vim /etc/elasticsearch/elasticsearch.yml
```

Save then restart the service
```shell
sudo systemctl daemon-reload
sudo systemctl enable elasticsearch.service
sudo systemctl start elasticsearch.service

## check status of elasticserch using ##
sudo systemctl status elasticsearch.service
```
