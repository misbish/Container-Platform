**Docker Container**


    Create an empty directory 
    Inside that directory you have these 3 files 
        app.py
        requirements.txt
        Dockerfile

`1. Define a container with Dockerfile`
           
           vi Dockerfile
           
           
           # Use an official Python runtime as a parent image
           FROM python:2.7-slim
           
           # Set the working directory to /app
           WORKDIR /app
           
           # Copy the current directory contents into the container at /app
           COPY . /app
           
           # Install any needed packages specified in requirements.txt
           RUN pip install --trusted-host pypi.python.org -r requirements.txt
           
           # Make port 80 available to the world outside this container
           EXPOSE 80
           
           # Define environment variable
           ENV NAME World
           
           # Run app.py when the container launches
           CMD ["python", "app.py"]

`2. Build the app`

           docker build -t helloflask .        # -t for --tag
           
           NOTE: helloflask must be lowercase
           
           By Default , latest tag will be built. Else supply tag as
                 docker build -t helloflask:1.0.0 .
           
`3. List Image`

           docker image ls 
           
           docker image ls -a                         # List all images on this machine
           docker image rm <image id>                 # Remove specified image from this machine
           docker image rm -f <image id>              # Remove specified image from this machine forcefully 
           docker image rm $(docker image ls -a -q)   # Remove all images from this machine
           
           
`4. Run the app`

           docker run -p 4000:80 helloflask
           
           80  : Container Port 
           4000 : Outside port 
           
           docker run -d -p 4000:80 helloflask        # Run in detached mode 
           
           What happens behind the scene when you run a container : docker run helloworld ls -l
           
               - The Docker client contacts the Docker daemon
               - The Docker daemon checks local store if the image is available locally, and 
                 if not, downloads it from Docker Store. 
               - The Docker daemon creates the container and then runs a command in that container.
               - The Docker daemon streams the output of the command to the Docker client
               
           Terminology
           
               Docker daemon - The background service running on the host that manages building, running and distributing Docker containers.
               Docker client - The command line tool that allows the user to interact with the Docker daemon.
               Docker Store - A registry of Docker images, where you can find trusted and enterprise ready containers, plugins, and Docker editions.

           
`5. List Container`

           docker container ls 
           
`6. Verify`

           http://localhost:4000
           
           NOTE:  If you are running using docker toolbox , then find ip and use that ip instead of localhost
           $docker-machine ip                        # Ip of the machine
          
           
`7. Quit`

           Ctrl + C  then
           
           docker container stop <Container Name or ID>
           
           docker container stop <hash>     # Gracefully stop the specified container
           docker container kill <hash>     # Force shutdown of the specified container
           docker container rm <hash>       # Remove specified container from this machine
           docker container rm $(docker container ls -a -q)   # Remove all containers
           
`8. Share your image`

           Create a Docker account, sign up for one at hub.docker.com.
           
           docker login  (Login)
           
           docker tag <imagename> <username>/<repository>:<tag>    # Create Tag
           
           docker push <username>/<repository>:<tag>               # Publish
           
           
           From now onwards , you can run anywhere using below 
           docker run -p 4000:80 <username>/<repository>:<tag>
           
           
           NOTE : You can set up your own private registry using Docker Trusted Registry.
           
#Dockerfile
   
https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
https://docs.docker.com/engine/reference/builder/#environment-replacement

    - Must start with FROM Keyword
    - There must be only 1 CMD 
    - Unlike RUN , CMD does not create additional layer .
    
DockerFile Execution Process (#TODO)

    Need to know how the layers created