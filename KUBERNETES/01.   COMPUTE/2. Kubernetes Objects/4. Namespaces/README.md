#Namespaces 

    - Kubernetes support multiple virtual cluster backed by same physical cluster .
      There virtual clusters are called Namespaces .

    - Useful with Large team 
    
    - Names  within a Namespace must be unique , not across namespaces 
    
Command Line 

    - $kubectl get namespaces                    # View Namespaces
    NAME          STATUS    AGE
    default       Active    1d    ----  For Objects with no namespace
    kube-system   Active    1d    ----  For objects created by kubernetes system
    kube-public   Active    1d    ----  Created automatically & readable by all users
    
    Note : Status can be Active or Terminating 
    
    - $kubectl get namespaces <name>             # View specific namespace
    
    - $kubectl describe namespaces <name>        # View specific namesoace in detail
    
    - $kubectl config view                       # View config 
     
    - $kubectl config current-context            # View current context
    
    - $kubectl config set-context dev --namespace=<namespacename>--cluster=<> --user=<>  # Set alias context for a namespace
    
    - $kubectl config use-context <context name> # Switch to contect 

    - $kubectl --namespace=<namespace> get pods  # Temporary setting namespace for a request
    
    - $kubectl api-resources --namespaced=true   # View resources within namespace
    
    - $kubectl api-resources --namespaced=false  # View resources not in namespace
    
    NOTE : Most resources are in some namespaces., but not all 
           For example , namespace itself is not in any namespaces
           Also nodes, volumes are not in namespaces
           
Namespace and DNS 

    When you create a Service, it creates a corresponding DNS entry.
    This entry is of the form <service-name>.<namespace-name>.svc.cluster.local
    That means that if a container just uses <service-name>, it will resolve to the service which is local to a namespace. 
    
    