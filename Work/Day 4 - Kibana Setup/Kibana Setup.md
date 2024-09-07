Download Kibana: https://www.elastic.co/downloads/kibana
```shell
wget https://artifacts.elastic.co/downloads/kibana/kibana-8.15.1-amd64.deb
```

Install Kibana
```shell
sudo dkpg -i [kibana.deb file you just downloaded]
```

Before we start the service, we need to edit the Kibana configuration file
- Server Port (uncomment)
- Server Host (set to private IP)
```shell
sudo vim /etc/kibana/kibana.yml
```

Save your configurations, then run the following commands consecutively.
```shell
sudo systemctl daemon-reload
sudo systemctl enable kibana.service
sudo systemctl start kibana.service

## check the status of Kibana
sudo systemctl status kibana.service
```

Generate ElasticSearch enrollment token
```shell
cd /usr/share/elasticsearch/bin

./elasticsearch-create-enrollment-token --scope kibana
```
Copy and paste this token somewhere safe lol 

Generate a verification code using the code below
```shell
cd /usr/share/kibana/bin

sudo ./kibana-verification-verification code
```

If you did everything correctly, you should be able to log into Elastic
![KibanaLogin](https://github.com/user-attachments/assets/1b4d66e4-5668-44d8-85ab-97119885c29c)

## Create persistent Key 
If we go to Security > Alerts, we will be greeted with the following message:

![API-Key-Integration](https://github.com/user-attachments/assets/1304e4d0-7690-46f0-b8cd-03274637e9da)

So let's create a persistent key.

```shell
cd /usr/share/kibana/bin

sudo ./kibana-encryption-keys generate
```

Copy the generated encrypted keys (the last three lines) somewhere safe. 

Now we need to add them to the Kibana keystore individually:
```shell
sudo ./kibana-keystore add xpack.encryptedSavedObjects.encryptionKey
## copy and paste the actual encryptedSavedObjects key value ##
 
sudo ./kibana-keystore addxpack.reporting.encryptionKey
## copy and paste the actual reporting key value ##

sudo ./kibana-keystore addxpack.security.encryptionKey
## copy and paste the actual security key value ##
```

Now restart the kibana service
```shell 
sudo systemctl restart kibana.service
```

Log into Kibana again from the web GUI and the error message should be gone!