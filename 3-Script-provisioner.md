
## 1. Instead of inline, provide script and script name in provisioner
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
      "ami_name": "ubuntu-nginx2"
    }
  ],
  "provisioners": [
    {
      "type": "shell",
      "script": "setup.sh"
    }

  ]

}
```
## 2. Have the inline commands in  setup.sh file 
Installs nginx and enables it.
Set up firewall rules for ssh, http & enables it.
```
sleep 30
sudo apt update
sudo apt install nginx -y
systemctl enable nginx
sudo ufw allow ssh
sudo ufw allow http
sudo ufw enable
```

## 3. Build & wait for the AMI to be created
```
packer build scriptprovisioner.json
```

## 4. Create an instance with this AMI 
Test with the public ip of the ec2 instance & check for nginx welcome page
