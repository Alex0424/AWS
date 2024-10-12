# CloudWatch AWS

### What is CloudWatch?

Monitor performance of AWS enviroments - standard infrastructure metrics.

### Metrics

AWS cloud watch allows you to record metrics for services such as EBS, EC2, ELB, Route53 Health checks, RDS, Amazon S3, cloudfront etc...

### Events

AWS Events delivers a near real-time stream of system events that describe changes in Amazon Web Services(AWS) resources.

### Logs

You can use Amazon CloudWatch logs to monitor, store, and access your log fiels from Amazon Elastic Compute Cloud(Amazon EC2) instances, AWS CloudTrain, Route53, and other resources.

## Alarm

Alarm monitors CloudWatch metrics for instances.

- Simple Notification Service (Amazon SNS)
  - is a web service that coordinates and manages the delivery of sending of messages to subscribing endpoints or clients.
  - alarm will trigger email notification(SNS)


## Monitoring

Monitoring shows statistics every 5 minutes 

but you can change that to every 1 minute e.g.: EC2 > Instances > Your Instance > Monitoring -> `Manage detailed monitoring`

## Stress Testing

When running this stress then make sure you are not running on a shared VM otherwise you wont get same CPU% in us(cpu user space e.g.: 100.0us).
```
#STRESS Installation

# Centos
sudo yum install epel-release -y
sudo yum install stress -y

#Amazon Linux 2
sudo amazon-linux-extras install epel -y
sudo yum install stress -y

# Ubuntu
sudo apt update
sudo apt install stress -y

# stress command
nohup stress -c 4 -t 300 &
top

stress -c 4 -t 60 && sleep 60 && stress -c 4 -t 60 && sleep 60 && stress -c 4 -t 360 && sleep 60 && stress -c 4 -t 460 && sleep 30 && stress -c 4 -t 360 && sleep 60
```

## Cloud Watch

Create an alarm for an instance:

Cloud Watch -> Alarms -> All alarms -> Create alarm -> Select metric -> `EC2 > Per-Instance Metrics > Metric name: CPUUtilization`

Chose `Whenever CPUUtilization is >= Greater/Equal than 60`. Chose `In Alarm` and find `select an existing SNS topic`



