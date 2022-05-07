

## 1. Add this to the provisioners to copy custom index to tmp folder
Then add an inline command to copy that to /var/www/html folder so that nginx will have the custom html.
If we directly copy from source to destination, there is root permission issue.
```
 {
      "type": "file",
      "source": "index.html",
      "destination": "/tmp/"
    },
    {
      "type": "shell",
      "inline": ["sudo cp /tmp/index.html /var/www/html"]
    }
```

## 2. Build & wait for the AMI to be created
```
packer build fileprovisioner.json
```

## 4. Create an instance with this AMI 
Test with the public ip of the ec2 instance & test the public ip for the custom nginx welcome page
<img width="549" alt="image" src="https://user-images.githubusercontent.com/49971693/167237023-6fdfebec-e92e-4cd4-bec9-9f8560b499d1.png">
