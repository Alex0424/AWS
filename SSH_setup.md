# SSH

EC2 --> Network & Security --> Key Pairs --> Create a pem key-pair and download it


```
sudo chmod 400 key.pem
sudo chown your_user:your_user key.pem
ssh -i "key.pem" ec2-user@ec2-18-321-123-123.compute-1.amazonaws.com
```
