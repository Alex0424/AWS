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

## Elastic Block Storage

Block based storage

Runs ec2 OS, store data from db, file data, etc

Placed in specific AZ. Automatically replicated within the AZ to protect from failure.

Snapshot is a backup of a volume

### EBS Types

SSD, IOPS, HDD, COLD HDD, etc...

https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html

### Snapshot Backup & Restore

- Unmount partition
- Detach volume
- Create new volume from snapshot
- Attach the volume created from snapshot
- Mount it back

### Create EBS Volume and mounte to Instance

EC2 > Volumes > Create Volume > Create

select `Action` on your newly created volume and select `Attach volume`

select your instance and then type `attach`

SSH into the VM
```
sudo -i
fdisk -l
df -h

fdisk /dev/xvdb
Command (m for help): n
Command (m for help): p
Command (m for help): 1
First sector (2048-10485759, default 2048): `Hit enter`
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-10485759, default 10485759): `Hit enter to use all space` or specify how much GB should be allocated to disk e.g. `+3G`
Command (m for help): p
Command (m for help): w

#format partition
mkfs.ext4 /dev/xvdb1

#move files
mkdir /tmp/img-backups
mv /var/www/html/images/* /tmp/img-backups/

mount /dev/xvdb1 /var/www/html/images/
df -h
umount /var/www/html/images
lsof /var/www/html/images #if the command above dosent work | this lists what processes uses the directory so kill those and try again with command above


################################### steps below: will make make the mount persistent, so it will survive reboots

vi /etc/fstab
/dev/xvdb1    /var/www/html/images    ext4 defaults    0 0 #add this line to the file
mount -a
df -h
mv /tmp/img-backups/* /var/www/html/images/
systemctl restart httpd
```

### Create Snapshots in AWS

volumes > Actions > Create Snapshot

SSH in VM:
```
# make sure to stop any services that are on that volume-directory before umount e.g.:
lsof /var/lib/mysql/
systemctl stop mariadb
umount /var/lib/mysql/
umount -l /var/lib/mysql #remove with force (use with caution)
df -h
```

detach volume in AWS + rename to corrupted if it is so.

chose your snapshot `Action` select `create volume from snapshot` # create image from snapshot is possible if it has a snapshot of "/" root directory

go to volumes and find your newly created volume. click `Actions` and then `Attach volume`

SSH in VM:
```
mount -a
df -h
systemctl start mariadb
```


