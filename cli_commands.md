# AWS CLI

### Creat/Delete Key-Pair
```
aws ec2 create-key-pair --key-name <keypair name> --query 'KeyMaterial' --output text > <keypair name>.pem
aws ec2 delete-key-pair --key-name <keypair-Name>
```
### Security Group | Create | add inbound rules | describe | add tag | delete
```
aws ec2 create-security-group --group-name <security grp Name> --description "<Description>"
aws ec2 authorize-security-group-ingress --group-id <security group Id> --protocol tcp --port <port Number> --cidr <ip address>/32
aws ec2 authorize-security-group-ingress --group-id <security grp Id>--protocol tcp --port 22-8000 --cidr 0.0.0.0/0
aws ec2 describe-security-groups --group-names <security grp Name>
aws ec2 create-tags --resources <Instance-Id> --tags Key=Name,Value=<value>
aws ec2 delete-security-group --group-name <security grp Name>
```

### Instance Launch/Terminate
```
aws ec2 run-instances --image-id <ami-Id> --count 1 --instance-type <type> --key-name <keypair-Name> --security-groups <security grp Name>
aws ec2 terminate-instances --instance-ids 
```

### Other
```
curl https://checkip.amazonaws.com
aws sts get-caller-identity   #user id etc.
aws ec2 describe-instances
```

# All commands

https://docs.aws.amazon.com/cli/latest/reference/

