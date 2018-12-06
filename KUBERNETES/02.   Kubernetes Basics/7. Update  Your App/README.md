`Update Your App`

    Rolling updates allow Deployments' update to take place with zero downtime by incrementally updating
    Pods instances with new ones

    By default, the maximum number of Pods that can be unavailable during the update is One 
            and the maximum number of new Pods that can be created, is one.
    Both options can be configured to either numbers or percentages (of Pods).
     
     
    In Kubernetes, updates are versioned and 
                   any Deployment update can be reverted to previous (stable) version.
                   
    
    
    Command
    
        $kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2 #Perform Rollout
        $kubectl rollout status deployments/kubernetes-bootcamp          # Check Rollout Status
        $kubectl rollout undo deployments/kubernetes-bootcamp            # Undo Rollout
    


Here i have one doubt ..4 Replicas i have running , when i update to new version during that time how the transaction happens
