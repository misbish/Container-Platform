
`Deploy an App`

    1.  Make your Kubernetes cluster up 
    
    2.  Ready with your containerized applications 
    
    3.  Create a Kubernetes Deployment configuration. 
    
    The Deployment instructs Kubernetes how to create and update instances of your application.
    
    Once you've created a Deployment, the Kubernetes master schedules mentioned application instances onto individual Nodes in the cluster.
    
    Once the application instances are created, a Kubernetes Deployment Controller continuously monitors those instances. 
    
    If the Node hosting an instance goes down or is deleted, the Deployment controller replaces it.
    This provides a self-healing mechanism to address machine failure or maintenance.
    
    Command:
    
        $kubectl run <deployment_name> --image=<app_image_name_with_full_repository_url> --port=<Port>  #Creates the deployment 
        $kubectl run kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1 --port=8080
        $kubectl get deployments       # List your deployments
        $kubectl proxy
        $curl http://localhost:8001/version

    kubectl run command creates the deployment .
    Kubernetes create a Pod to host you application instance .
    This performed a few things for you:
        search for a suitable node where an instance of the application could be run 
        schedule the application to run on that Node
        configure the cluster to reschedule the instance on a new Node when needed
        
    $ kubectl get deployments
    NAME                  DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
    kubernetes-bootcamp   1         1         1            1           2m
    
    The DESIRED state is showing the configured number of replicas
    
    The CURRENT state show how many replicas are running now
    
    The UP-TO-DATE is the number of replicas that were updated to match the desired (configured) state
    
    The AVAILABLE state shows how many replicas are actually AVAILABLE to the users
    
At this point the application is running in docker container , inside a pod .
How to access the app / View the app ? 
    
    $kubectl proxy      
    
    Pods that are running inside Kubernetes are running on a private, isolated network.
    By default they are visible from other pods and services within the same kubernetes cluster, but not outside that network.
    
    The kubectl command can create a proxy that will forward communications into the cluster-wide, private network.
    The proxy can be terminated by pressing control-C and won't show any output while its running.
    We will open a second terminal window to run the proxy.
    
    
    We now have a connection between our host (the online terminal) and the Kubernetes cluster.
    The proxy enables direct access to the API from these terminals.
    
    $export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadataname}}{{"\n"}}{{end}}')
    
    $ echo Name of the Pod: $POD_NAME
    Name of the Pod: kubernetes-bootcamp-5c69669756-ffhvv
    
    $ curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/
    Hello Kubernetes bootcamp! | Running on: kubernetes-bootcamp-5c69669756-ffhvv | v=1
    $