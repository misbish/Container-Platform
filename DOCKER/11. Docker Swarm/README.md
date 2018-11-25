#Docker SWARM


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


