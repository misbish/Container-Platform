#Docker  Architecture

**Docker Engine**

    Docker Engine is a client-server application with these major components:
        Docker Daemon  - ( dockerd command)
        REST API   - An Interface between docker CLI and Docker Daemon .
        Docker CLI - ( docker command ) 
    
    The CLI uses the Docker REST API to control or interact with the Docker daemon.    
    The daemon creates and manages Docker objects, such as images, containers, networks, and volumes.
    The Docker client and daemon can run on the same system or different .
    
    A Docker registry stores Docker images. 
    Docker Hub and Docker Cloud are public registries that anyone can use.
    Docker is configured to look for images on Docker Hub by default.
    You can even run your own private registry
      
      
TODO 
  
    Docker Hub
    Docker Store
    Docker Cloud 
        
  