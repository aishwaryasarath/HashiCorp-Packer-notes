
1. Add provisioners to the earlier AMI script & change the ami to ubuntu
```
{

  "builders": [
    {
      "type": "amazon-ebs",
      "access_key": "****",
      "secret_key": "****",
      "region": "us-east-1",
      "source_ami": "ami-005de95e8ff495156",
      "instance_type": "t2.micro",
      "ssh_username": "ubuntu",
      "ami_name": "ubuntu-nginx"
    }
  ],
  "provisioners": [
    {
      "type": "shell",
      "inline": ["sleep 30", "sudo apt update", "sudo apt install nginx -y"]
    }

  ]

}
```
2. Build 

```
packer build provisioner.json
```
3. Outputs on terminal & AWS Console

![image](https://user-images.githubusercontent.com/49971693/167229506-b91ae526-3e6f-407f-aec2-a722fa3bb205.png)
<img width="706" alt="image" src="https://user-images.githubusercontent.com/49971693/167229524-0845b8da-90c7-43c7-9c6f-685d1f24ae44.png">

