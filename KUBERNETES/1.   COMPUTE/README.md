#KUBERNETES CONCEPTS

    1. Overview 
           ( In K8S , we use kubectl commandline , which call the K8S API  to interact with cluster.
             We can also use with K8S Api directly to interact with cluster.
             Once we have set the desired state , K8S Control Plane works to make cluste's current state match the desired state.
             
    2. Kubernetes Objects 
           
           ( Kubernetes contains a number of abstractions that represent the state of your system.
             Each abstraction is represented by Objects in K8s API)
    
          - Basic Objects
             - Pod
             - Service 
             - Volume
             - Namespace
             
          - Controller Object (Kubernetes contains a number of higher-level abstractions called Controllers.
                               Controllers build upon the basic objects)
             - ReplicaSet
             - Deployment
             - StatefulSet
             - DaemonSet
             - Job
          
    3. Kubernetes Control Plane 
          - Kubernetes master 
              (Responsible for maintaining the desired state for your cluster.
               The “master” refers to a collection of processes managing the cluster state.
               Typically these processes are all run on a single node in the cluster, and this node is also referred to as the master.
               The master can also be replicated for availability and redundancy.
               With kubectl command-line interface, you communiate with your cluster’s Kubernetes master)
               
                - kube-apiserver
                - kube-controller-manager 
                - kube-scheduler.
          
          - Kubernetes node 
               (The nodes in a cluster are the machines (VMs, physical servers, etc) that run your applications .
                The Kubernetes master controls each node; you’ll rarely interact with nodes directly.)
          
                - kubelet
                - kube-proxy

