# Networking-on-google-cloud


1. Creating a subnet with a address range, the first command creates the name of the subnet and uses custom subnet creation. GCP does allow automatic subnet creation as an option and Creates the subnets for you (optional).



  
   ``` gcloud compute --your-project-id networks create subnet-east-1 --mode=custom
    
     gcloud compute --your-project-id networks subnets create subnet-east-vpn --network=subnet-east-1 --region=us-west1 --range=10.128.0.0/20 ```
 



2. this firewall rule creates the subnet name “subnet-west-secure” the direction is ingress meaning the traffic that is allowed in. as you can see we created a firewall rule specifying the network as subnet-demo-gcp, followed by the allowed ports ssh, http


   ```gcloud compute --your-project-id firewall-rules create subnet-west-secure --direction=INGRESS --priority=1000 --network=subnet-demo-gcp --action=ALLOW --rules=tcp:22,tcp80 --source-ranges=10.138.0.0/20```



3. you probably noticed in the first part of the demonstration there’s a network `subnet-east-1`, the firewall was created for a different subnet, which is network `subnet-demo-gcp`


4. When creating firewall rules, you can specify for the firewall rule to be subnet specific, project wide or for specific IP ranges.

this is just a simple tutorial to help you understand how to create subnets using the GCP cloud shell. 
