# Welcome in step3

## 1. Tooling for ELK

So see with a user friendly interface the status of your elasticsearch instance, please, install in your computer the elasticsearch web-plugin named elasticsearch-head. Fill in the form and connect to your elasticsearch instance with the appropriate IP adress. The portname is by default 9200. You should be able to see something simillar to the following:
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99e%CC%81cran%202018-06-20%20a%CC%80%20170639%20(2).png)


## 2. Seting-up crypto data collection
Please, correct the default ESserverIP adress with your @IP adress according to your environment.
Let's start with the script in charge to collect data from the icastats command:
```
sudo vi icastats.sh
#!/bin/bash
ESserverIP="18.197.196.0" <--- Change with your IP address here
```

It is now time to feed your elastic search with collected data and to create an index on elasticsearch database. Please issue the following command:
```
sudo chmod +x icastats.sh
sudo ./icastats.sh
{"_index":"monitor-icastats","_type":"icastats","_id":"RD8FkmMBF84PFKnZKoVW","_version":1,"result":"created","_shards":{"total":2,"successful":1,"failed":0},"_seq_no":0,"_primary_term":1}
{"_index":"monitor-icastats","_type":"icastats","_id":"RD8FkmMBF84PFKnZKoVW","_version":1,"result":"created","_shards":{"total":2,"successful":1,"failed":0},"_seq_no":0,"_primary_term":1}
[...truncated...]
```

Ervery 5 seconds, a record will be sent to the elasticsearch db. 

To assess that it works properly, with web interface there are new records added in the elasticsearch db.
Your elasticsearh web interface should look like the foolowing:
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%20140351%20(2).png)

You are now good for the [step 4](https://github.com/IBM/protect-data-on-linuxone-with-pervasive-encryption/edit/master/part4.md) about creating a dashboard to magnify live captured crypto information.
