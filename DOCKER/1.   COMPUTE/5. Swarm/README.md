**DOCKER SWARM**

What is Swarm 

    -   Cluster of docker engine is called swarm.
    
    -   “Dockerized” cluster called a swarm.
    
    -   A swarm consists of multiple Docker hosts which run in swarm mode and act as managers 
        (to manage membership and delegation) and workers (which run swarm services).
    
NOTE :

    -   A given Docker host can be a manager, a worker, or perform both roles
    
    -   Docker daemons can participate in a swarm as managers, workers, or both.
    
    -   If you are using a Docker version prior to 1.12.0, you can use standalone swarm
     
    -   Current versions of Docker include swarm mode for managing swarm
    
    -   Use the Docker CLI to create a swarm,
                           to deploy application services to a swarm,
                           and manage swarm behavior.

    - The machines in a swarm can be physical or virtual.
    
    - All docker commands are executed on a cluster by a swarm manager. 
    
    - After joining a swarm, machines are referred to as nodes.
    
    
    Swarm managers can use several strategies to run containers,
         “emptiest node” -- which fills the least utilized machines with containers.
         “global”, which ensures that each machine gets exactly one instance of the specified container.
          You instruct the swarm manager to use these strategies in the Compose file.
          
Benefit of swarm services vs standalone containers

     -  You can modify a service’s configuration, including the networks and volumes it is connected to,
        without the need to manually restart the service. 
        Docker will update the configuration, stop the service tasks, and create new ones matching the desired configuration.
     
     -  Standalone Container can be started on any daemon whereas swarm manager can only manages the swarm
     
NOTE :

    -   When Docker is running in swarm mode, you can still run standalone containers on any of the 
        Docker hosts participating in the swarm.
         
Nodes:
    
    -   A node is an instance of the Docker engine participating in the swarm.
        - manager node
        - worker node
    
    -   To deploy your application to a swarm, you submit a service definition to a manager node.
    
        The manager node dispatches units of work called tasks to worker nodes.
        
        Worker nodes receive and execute tasks dispatched from manager nodes
        
NOTE:

    -   By default manager nodes also run services as worker nodes,
        but you can configure them to run exclusively manager tasks
        
         
`1. Set up Swarm` 

    docker swarm init    #Enable swarm mode and make your current machine a swarm manager 
    docker swarm join    #on other machines to have them join the swarm as workers.
    
    
    docker-machine create --driver virtualbox myvm1   #Create Virtual Machine
    docker-machine create --driver virtualbox myvm2   #Create Virtual Machine
    
    docker-machine ls               #List the VMs   
    
    docker-machine ssh myvm1 "docker swarm init --advertise-addr <myvm1 ip>"
    o/p: Swarm initialized: current node <node ID> is now a manager.
    
    To add a worker to this swarm, run the following command:
    
      docker swarm join \
      --token <token> \
      <myvm ip>:<port>
    
    To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
    
    
    NOTE :  port 2377 (Swarm Manaement Port)  and 2376  (Docker Daemon port)

    docker node ls     #on the manager to view the nodes in this swarm:
    
    docker swarm leave  #To Leave Swarm 
    
    
    
    ALTERNATE OPTION TO CREATE MASTER INSTED OF SSH:
    
    docker-machine env <machinename>  #Run the last command from the output 
                                      #You can use your local docker-compose.yml file .This is the benefit 
                                      
                                      
                                      
    NOTE:
    --with-registry-auth flag (if you use your private registry
    
    docker login registry.example.com
    
    docker stack deploy --with-registry-auth -c docker-compose.yml getstartedlab
    
Services and tasks
 
Load Balancing





Explore swarm mode CLI commands
swarm init
swarm join
service create
service inspect
service ls
service rm
service scale
service ps
service update    
    
Commands :

    docker-machine create --driver virtualbox myvm1 # Create a VM (Mac, Win7, Linux)
    docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1 # Win10
    
    docker-machine env myvm1                # View basic information about your node
    docker-machine ssh myvm1 "docker node ls"         # List the nodes in your swarm
    docker-machine ssh myvm1 "docker node inspect <node ID>"        # Inspect a node
    docker-machine ssh myvm1 "docker swarm join-token -q worker"   # View join token
    docker-machine ssh myvm1   # Open an SSH session with the VM; type "exit" to end
    docker node ls                # View nodes in swarm (while logged on to manager)
    docker-machine ssh myvm2 "docker swarm leave"  # Make the worker leave the swarm
    docker-machine ssh myvm1 "docker swarm leave -f" # Make master leave, kill swarm
    docker-machine ls # list VMs, asterisk shows which VM this shell is talking to
    docker-machine start myvm1            # Start a VM that is currently not running
    docker-machine env myvm1      # show environment variables and command for myvm1
    eval $(docker-machine env myvm1)         # Mac command to connect shell to myvm1
    & "C:\Program Files\Docker\Docker\Resources\bin\docker-machine.exe" env myvm1 | Invoke-Expression   # Windows command to connect shell to myvm1
    docker stack deploy -c <file> <app>  # Deploy an app; command shell must be set to talk to manager (myvm1), uses local Compose file
    docker-machine scp docker-compose.yml myvm1:~ # Copy file to node's home dir (only required if you use ssh to connect to manager and deploy the app)
    docker-machine ssh myvm1 "docker stack deploy -c <file> <app>"   # Deploy an app using ssh (you must have first copied the Compose file to myvm1)
    eval $(docker-machine env -u)     # Disconnect shell from VMs, use native docker
    docker-machine stop $(docker-machine ls -q)               # Stop all running VMs
    docker-machine rm $(docker-machine ls -q) # Delete all VMs and their disk images