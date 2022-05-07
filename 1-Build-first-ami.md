## 1. Install Packer and create the first ami
```
{

  "builders": [
    {
      "type": "amazon-ebs",
      "access_key": "******",
      "secret_key": "******",
      "region": "us-east-1",
      "source_ami": "ami-0022f774911c1d690",
      "instance_type": "t2.micro",
      "ssh_username": "ec2-user",
      "ami_name": "packer_AWS {{timestamp}}"
    }
  ]
}

```
## 2. Build the code
```
packer build ami.json
```
## 3. The EC2 instance gets created: it goes from pending to running and then to stopped.

![image](https://user-images.githubusercontent.com/49971693/167227482-ff9746b4-83c6-49b1-9f2e-28462d4335e8.png)
![image](https://user-images.githubusercontent.com/49971693/167227487-bf929e96-9ff2-4301-a6b9-bd14a0d0e1ea.png)
![image](https://user-images.githubusercontent.com/49971693/167227498-a4fdb949-691f-464d-b895-92e99719be7a.png)

## 4. The output on the terminal shows the AMI was created
<img width="468" alt="image" src="https://user-images.githubusercontent.com/49971693/167227505-706eedd0-ff10-4814-8e5d-49d57e102d53.png">

## 5. The AWS console also shows the AMI
![image](https://user-images.githubusercontent.com/49971693/167227596-34d831d8-5841-402c-b6d7-7ddce4d576f0.png)

## 6. Create an EC2 instance with this AMI, ssh into it and verfiy that nginx is installed.
<img width="479" alt="image" src="https://user-images.githubusercontent.com/49971693/167230449-560c7537-9e7a-4d20-bc7b-1b1e5e737f68.png">


## 7. Delete the AMI from the console to avoid getting recurring charges
