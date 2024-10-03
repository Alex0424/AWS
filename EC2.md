# EC2

## EC2 Features

EC2 provides a web services API for provisioning, managing and deprovisioning virtual servers inside amazon cloud.

Ease In Scaling Up/Down

Pay only for what you are using

Can be integrated into several other services

## EC2 Pricing

On Demand: Pay per hour or seconds

Reserved: Reserve Capacity(1 or 3 years) for discounts.

Spot: Bid your price for unused EC2 capacity.

Dedicated Hosts: Physical Server dedicated for you. (not VM)

## EC2 Components

Instances: Virtual servers.

AMI: Preconfigured templates for your instances that package the components you need for your server (including the operating system and additional software).

Instance Type: Various configurations of CPU, memory, storage, networking capacity, and graphics hardware for your instances.

EBS volume: Persistent storage volumes for your data using Amazon Elastic Block Store. 

Instance store volumes: Storage volumes for temporary data that is deleted when you stop, hibernate, or terminate your instance.

Security groups: A virtual firewall tspecify the protocols, ports, and source IP ranges that can reach your instances, and the destination IP ranges to which your instances can connect.

Key pairs: Secure login information for your instances. AWS stores the public key and you store the private key in a secure place.

Tags: tagging components to make it easier to manage, search and filter.

## Creation of EC2 Instance

Chose an AMI --> Chose an instance type --> configure the instance --> adding storage --> adding tags --> configure security group --> REVIEW & PUBLISH

## EC2 instance creation order

1. **Requirements Gathering**
   1. OS
   2. Size => Ram, CPU, Network etc: https://aws.amazon.com/ec2/instance-types/
   3. Storage size
   4. Firewall & Security Group Rules
   5. Project (Services/Apps Running: SSH, HTTP, Mysql etc)
   6. Enviroment(Dev,QA,Staging,Prod)
   7. Login User/Owner
2. **Create Key-Pairs**
3. **Setup Security Groups**
4. **Instance Launch**

## Security Group

A security group acta as a virtual firewall that controls the traffic for one or more instances.

Security groups are "stateful". if inbound rule is updated, then same rule will be updated for outbund.

Inbound rules: Trafic coming from outside in to the instance.

Outbound rules: Trafic going from Instance to outside.

## Elastic IP

this is a permanent IP that you can assosiate for your Instance or Network Interface

 
