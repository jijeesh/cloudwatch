#AWC EC2 custom metrics for CloudWatch

Send memory and cpu usage metrics to Amazon CloudWatch

##Required:
https://github.com/giampaolo/psutil

##Usage:
##### 1. Clone cloudwatch.py to EC2 linux server

##### 2. Create a boto credentials file `/etc/boto.cfg`
```
[Credentials]
aws_access_key_id = <aws access key>
aws_secret_access_key = <aws access secret>
```
##### 3. confugure crontab `$ crontab -e`
```
* * * * * /usr/bin/python /path/to/cloudwatch.py
```

##Real CPU usage for t2 instances
Standard "CPU Utilization" metrics shows maximum 20% for **t2.medium** instance on full load and empty "CPU Credit"
![cpu](https://cloud.githubusercontent.com/assets/11991783/7495397/f2a3bd14-f40d-11e4-9440-cdd3a9f41636.png)

"Real CPU Usage" shows real maximum, so you can use it for autoscaling
![real-cpu](https://cloud.githubusercontent.com/assets/11991783/7495399/f4d3f5b8-f40d-11e4-9f5a-e2d09f0d1a53.png)

Print the number of containers on the Docker instance.

containerMonitor.py

A script inspired from a nice article about metric. It enables you to get several metrics from a running container:

the user or system cpu used by the container
the memory used by the container
the ip address of the container
the container status: running, stopped, crashed or paused
the container's network activity
Usage

containerHelper.py [-h] container {cpu,ip,memory,network,status} ...

positional arguments:
  container             Container name

optional arguments:
  -h, --help            show this help message and exit

Counters:
  Available counters

  {cpu,ip,memory,network,status}
    cpu                 Display CPU usage
    ip                  Display IP Address
    memory              Display memory usage
    network             Display network usage
    status              Display the container status