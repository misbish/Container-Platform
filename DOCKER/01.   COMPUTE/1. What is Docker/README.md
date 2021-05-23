**What is Docker**

    Docker is a container platform that allows you to separate your application from the underlying infrastructure 
    by bundling up your code and all of its dependencies into a self-contained entity that will run the same on any 
    supported system.
    
`Images and containers`

    An image is an executable package that includes everything needed to run an application--the code,
    a runtime, libraries, environment variables, and configuration files.

    A container is launched by running an image. 
    
    A container is a runtime instance of an image--what the image becomes in memory when executed .
 
    Images are stored in /var/lib/docker
    
`Containers and virtual machines`

    A container runs natively on Linux and shares the kernel of the host machine . 
    It runs a discrete process, taking no more memory than any other executable, making it lightweight.
    
    By contrast, a virtual machine (VM) runs a full-blown “guest” operating system with virtual access 
    to host resources through a hypervisor. 
    
`Prepare your Docker environment`

    $docker --version
    $docker info
