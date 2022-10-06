# ec2 instance - launch-template

# <h3>Installing some tools onto Ubuntu VM</h3>

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