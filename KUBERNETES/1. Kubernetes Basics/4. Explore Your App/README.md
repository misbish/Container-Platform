`Explore Your App`

    Kubernetes Pods: 
    
    - A Pod is a kubernetes abstraction that represent a group of one or more application containers
     (such as Docker or rkt) and some shared resources for those containers.
    
      Shared resources includes
         - Shared storage, as Volumes
         - Networking, as a unique cluster IP address
         - Information about how to run each container, such as the container image version or specific ports to use
             
    - Pods are the atomic unit on the Kubernetes platform.
    - When we create a Deployment on Kubernetes, that Deployment creates Pods with containers inside them (as opposed to creating containers directly).
    - Each Pod is tied to the Node where it is scheduled, and remains there until termination (according to restart policy) or deletion.
    - In case of a Node failure, identical Pods are scheduled on other available Nodes in the cluster.
    

    Kubernetes Nodes:
    
    - A Pod always runs on a Node.
    - A Node is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster.
    - Each Node is managed by the Master. 
    - A Node can have multiple pods, and the Kubernetes master automatically handles scheduling the pods across the Nodes in the cluster.
    - Every Kubernetes Node runs at least:
         -  Kubelet, a process responsible for communication between the Kubernetes Master and the Node; it manages the Pods and the containers running on a machine.
         -  A container runtime (like Docker, rkt) responsible for pulling the container image from a registry, unpacking the container, and running the application.
            
            
    The most common operations can be done with the following kubectl commands:
    
    kubectl get - list resources
    kubectl describe - show detailed information about a resource
    kubectl logs - print the logs from a container in a pod
    kubectl exec - execute a command on a container in a pod
   
    Command:
       kubectl get pods       # List the Pods
       kubectl describe pods  # More info about pod 
       kubectl proxy
       export POD_NAME=$(kubectl get pods -o go-template --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}')
       echo Name of the Pod: $POD_NAME
       curl http://localhost:8001/api/v1/namespaces/default/pods/$POD_NAME/proxy/
       kubectl logs $POD_NAME   # View Pod Logs 
       kubectl exec $POD_NAME env  #List environment variable inside pod
       kubectl exec -ti $POD_NAME bash  # Open a bash session in the Pod's Container
