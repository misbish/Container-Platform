#Kubernetes Objects


- What are Kubernetes Object     
- Types of Kubernetes Object
- How they are represented in Kubernetes API
- How you specify them in .yaml format


    - Kubernetes Objects are persistent entities in the Kubernetes system.
    - Kubernetes uses these entities to represent the state of your cluster.
    - Each object has 2 fields
         - spec 
             - You provide this , describing your desired state
         - status 
             - This is the actual state of object , provided by kubernetes system
             
    - In the .yaml file for the Kubernetes object you want to create, specify below fields
      
      apiVersion: apps/v1  # Which version of the Kubernetes API you’re using to create this object
      kind: Deployment     # What kind of object you want to create
      metadata:            # Data that helps uniquely identify the object, including a name string, UID, and optional namespace
        name: nginx-deployment
      spec: 
      
     NOTE:  spec for each object is different 
            
            https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.12/   - Spec Reference
             
             

             
NOTE : Volume and service you will find outside this module , in specific module 