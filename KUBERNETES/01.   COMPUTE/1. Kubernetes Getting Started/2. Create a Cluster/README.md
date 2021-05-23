`Create a Cluster`

    A Kubernetes cluster consists of two types of resources:
       - Master -  Manages the cluster
                   The master coordinates all activities in your cluster, such as
                        scheduling applications,
                        maintaining applications' desired state, 
                        scaling applications, and 
                        rolling out new updates.
       
       - Nodes -   workers that host & run applications
                   A node is a VM or a physical computer that serves as a worker machine in a Kubernetes cluster.
                   Each node has a Kubelet, which is an agent for managing the node and communicating with the Kubernetes master.
                   The node should also have tools for handling container operations, such as Docker or rkt.
                   The nodes communicate with the master using the Kubernetes API, which the master exposes.
                   
    End users can also use the Kubernetes API directly to interact with the cluster.     
    A Kubernetes cluster that handles production traffic should have a minimum of three nodes.
    Minikube has 1 node .
    
    Commands :
    
            $ minikube version              # Minikube version 
            $ minikube start                # Start kubernetes cluser
            $ kubectl version               # client version is kubectl version and server version is kubernetes version
            $ kubectl cluster-info          # View cluster details 
            $ kubectl cluster-info dump     # View cluster details for debugging purpose 
            $ kubectl get nodes             # To list the nodes in the cluster
