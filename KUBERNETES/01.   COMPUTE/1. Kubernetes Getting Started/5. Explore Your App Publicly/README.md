`Expose your app publicly i.e. via service`


   Why the need of service ?
   
    Kubernetes pods are mortal , die with the node .In that case replication controller dynamically create the new pods .
    Each pod has unique IP Address,so there needs to be a way of automatically reconciling changes among Pods so that your applications continue to function.
    That is where service play its role .
   
    A Service in Kubernetes is an abstraction which defines a logical set of Pods and a policy by which to access them and
    enables external traffic exposure, load balancing and service discovery for those Pods.
   
    Service is defined using YAML 
   
   TODO : Service YAML reference
    
        type :  ClusterIP  - Exposes the Service on an internal IP in the cluster. 
                             This type makes the Service only reachable from within the cluster.
                             This is Default one.
           
                NodePort   - Exposes the Service on the same port of each selected Node in the cluster using NAT. 
                             Makes a Service accessible from outside the cluster using <NodeIP>:<NodePort>
                
                LoadBalancer - Creates an external load balancer in the current cloud (if supported) and 
                               assigns a fixed, external IP to the Service. Superset of NodePort.
                               
                ExternalName - Exposes the Service using an arbitrary name (specified by externalName in the spec)
                               by returning a CNAME record with the name.
                               No proxy is used. This type requires v1.7 or higher of kube-dns.
                
    
    Command:
       $kubectl get services     # List services (by default service called kubernetes runs when minikube starts)
       $kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080   #Create & exposes a service via nodeport
                                 #NOTE : Minikube does not support LoadBalancer option
                                 
       $ kubectl get services
       NAME                  TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
       kubernetes            ClusterIP   10.96.0.1      <none>        443/TCP          3m
       kubernetes-bootcamp   NodePort    10.107.28.56   <none>        8080:30571/TCP   1m
       
       The service kubernetes-bootcamp received a unique cluster ip, an internal & external port .
       
       export NODE_PORT=$(kubectl get services/kubernetes-bootcamp -o go-template='{{(index .spec.ports 0).nodePort}}')
       echo NODE_PORT=$NODE_PORT
       curl $(minikube ip):$NODE_PORT
       
       
     Using Label ( A Label is automatically created during deployment creation)
       $kubectl label pod $POD_NAME app=v1    # Apply new Label 
       $kubectl get servies -l app=v1         # Find service using Label
       
       $kubectl delete service -l app=v1      # Delete Service 
       
     