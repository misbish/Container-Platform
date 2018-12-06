#Docker for Linux (Centos) for AWS

**Install Docker using Yum Package Manager**

    1) Install yum-utils pakcage     # With this you can add package repositories
    
         $sudo yum install -y yum-utils
    
    2) Add the Docker CE package repositories
    
         $sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    
    3) Update the yum cache with the Docker repositories
    
         $sudo yum makecache fast 
    
    4) Install Docker CE
    
         $sudo yum  install -y docker-ce
         
    5) Start Docker as a service
        
         $sudo systemctl start docker 
         
    6) Verify Docker 
    
         $sudo docker info 
         
         
**Remove Root Permission**

    1) Verify Docker group 
    
         $grep docker /etc/group
    
    2) Add Docker group
    
         $sudo groupadd docker
         
    3) Add the user to dockeer group 
    
         $sudo gpasswd -a $USER docker 
         
    4) Login again & verify 
    
         $newgrp docker
         
 Now you can run docker commands 