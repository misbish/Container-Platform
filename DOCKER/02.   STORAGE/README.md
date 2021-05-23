#Docker Storage 

    1. By default , All files are stored on a writable layer of container .( Default Storage Option )
    
    2. Use Storage Driver with Default Storage Option 
    
    3. Volume - Recommended Storage option for container 
                Stores data on Host machine  (Docker Managed Area /var/lib/docker)
                Docker managed 
              
    4. Bind Mount - Same as Volume but stores data anywhere in Host Machine 
                    User Managed 
                    
    5. Tmpfs Mount - Data Stored in Memory 
                     Beeter than Default Option 
                     
    6. Volume Driver - Use with Volume for external Storage 