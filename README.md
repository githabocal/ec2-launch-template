# ec2 instance - launch-template

# <h3>Installing some tools (_Docker, Git, Tree, Terraform, Kubernetes CLI, AWS CLI_) onto Ubuntu VM</h3>

- Connect to Ubuntu VM via terminal
- Create a folder where we can implement **`#!bin/bash`**
- Add the following commands into **`#!bin/bash`**
    ```
        #!/bin/bash
        apt update -y
        apt install docker.io -y
        apt install git -y
        snap install tree -y
        snap install terraform --classic -y
        apt-get update 
        apt-get install -y apt-transport-https 
        apt-get install -y virtualbox virtualbox-ext-pack
        curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - 
        touch /etc/apt/sources.list.d/kubernetes.list 
        echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list 
        apt-get update 
        apt-get install -y kubectl 
        curl -Lo minikuybe https://storage.googleapis.com/minikube/releases/v0.28.2/minikube-linux-amd64 
        chmod +x minikube && mv minikube /usr/local/bin/
        minikube start 
        kubectl api-versions
        apt-get install awscli
    ```
- Verify the tools installed successfully with following commands
    ```
        docker --version
        git --version
        snap info tree
        terraform -version
        kubectl version --short
        aws --version
    ```
    
    ![Screen Shot 2022-10-06 at 6 59 01 AM](https://user-images.githubusercontent.com/86754468/194418071-b9d9563b-2caf-4013-aabd-069fd3a5b440.png)


# <h3>Web Application Setup - Arcana html5</h3>

- Create a launch template with as follows;
    - Select Ubuntu as Amazon Machine image
    - Select t2.micro as instance type
    - Create Key pair
    - Network Settings
    - Update storage(volumes) if needed
    - In advanced details, user data must be implemented as follows;
        ```
            #!/bin/bash
            apt update -y
            apt install nginx -y
            cd /var/www/html
            git clone https://github.com/zce/html5up.git
            cp -r html5up/arcana/* .
            service nginx start
        ```
        
<img width="1359" alt="Screen Shot 2022-10-06 at 5 22 25 AM" src="https://user-images.githubusercontent.com/86754468/194423885-94c3a758-536d-4e64-9900-484557aa5ec9.png">

        
- Set up Auto Scaling Groups
  - Select desired capacity
  - if needed, head to security groups and edit inbound rules for SSH(22) and HTTP(80)

- Then head to the created the ec2 instance and open the address for Public IPv4 address
    
<img width="1792" alt="Screen Shot 2022-10-06 at 5 19 37 AM" src="https://user-images.githubusercontent.com/86754468/194423866-82c97ea9-317c-47b5-a8d6-afed1b03fc23.png">

