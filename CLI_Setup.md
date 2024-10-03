# IAM - Identity and Acess Management

## Create User for AWS-CLI

### IAM -> Access management/users -> create users -> attach policies directly

Chose: `AdministratorAccess` & create user

### IAM -> Users -> your user

Security Credentials -> Access keys -> Create access key -> chose: `Command Line Interface (CLI)` -> next & create -> chose: `Download .csv file` (Access keys)

## Install CLI

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

### Open your terminal

```
aws configure
```
output example:
```
AWS Access Key ID [None]: FISHBFAUIGFOW8
AWS Secret Access Key [None]: fw98u282342b
Default region name [None]: us-east-1
Default output format [None]: json
```

to verify that you have configured `aws configure` correctly do:
```
aws sts get-caller-identity
```


### AWS-CLI Configuration
```
cat ~/.aws/credentials
cat ~/.aws/config
```
