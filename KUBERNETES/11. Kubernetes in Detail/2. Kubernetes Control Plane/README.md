#KUBERNETES Components

**Master Components**

    Master components can be run on different machine.
    But for simplicity they all start in the same machine by the set up scripts.
    Also You should not run user container in this machine.

      - kube-apiserver
               - This component expose the Kubernetes API .
               - It is the front end of Kubernetes control plance .
               - It is designed to scale horizontally , i.e by deploying more instances
      - kube-scheduler
               - This component watches newly created pods that have no node assigned,
                 and selects a node for them to run on
      - etcd 
               - Consistent and highly-available key value store used as Kubernetes’ backing store 
                 for all cluster data.
               - Always have a backup plan for etcd’s data for your Kubernetes cluster
      - kube-controller-manager 
               - This component runs controllers
               - Each controller is a separate process, but for simplicity they are compiled into single 
                 binary and run as a single process
               - of Below type
                    - Node Controller:         Responsible for noticing and responding when nodes go down.
                    - Replication Controller:  Responsible for maintaining the correct number of pods 
                                               for every replication controller object in the system.
                    - Endpoints Controller:    Populates the Endpoints object (that is, joins Services & Pods).
                    - Service Account & Token Controllers: Create default accounts and API access tokens for new namespaces.
               
               NOTE: cloud-controller-manager runs cloud-provider-specific controller loops only.
                     You must disable these controller loops in the kube-controller-manager.
                     You can disable the controller loops by setting the --cloud-provider flag to external
                     when starting the kube-controller-manager.
                  
            
            
**Node Component**
    
    Node components run on every node
    These maintain running pods and provide the Kubernetes runtime environment.
          
       - kubelet 
              - It is an agent that runs on each node in the cluster. 
              - It makes sure that containers are running in a pod.
              - It works by looking at the PodSpec
       - Kube-proxy 
              - It ennables the Kubernetes service abstraction by maintaining network rules on the 
                and performing connection 
       - Container Runtime
              - It is the software that is responsible for running containers. 
              - Kubernetes supports several runtimes: Docker, rkt, runc and any OCI runtime-spec implementation.
        
**Addons** (TODO)
     
     - DNS
     - Web UI Dashboard 
     - Container Resource Monitoring
     - Cluster-level Logging
     - many more 
         
              