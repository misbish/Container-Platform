`Scale Your App`

    Scaling is accomplished by changing the number of replicas in a Deployment
    
    Scale Up - Increase Replica
    Scae Down - Decrease Replica

    Scaling to zero is also possible, and it will terminate all Pods of the specified Deployment.

    Kubernetes also supports autoscaling of Pods, TODO 
    
    Command
        $kubectl scale deployments/kubernetes-bootcamp --replicas=4  $Scaling up  
        $kubectl scale deployments/kubernetes-bootcamp --replicas=2  $Scaling down
        
    