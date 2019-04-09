# Networking-on-google-cloud


You can use these commands for playground purposes on the google cloud platform. This should be considered a reference and by no means should you use this as a guide for production purposes.  


Creating a subnet with a address range, the first command creates the name of the subnet and uses custom subnet creation. GCP does allow automatic subnet creation as an option and Creates the subnets for you (optional).


```
# creates the name of the network and the subnet mode to custom 
gcloud compute --your-project-id networks create subnet-east-1 --mode=custom
    
```

```
# creates the subnet-east-vpn subnet with a region us west 1 with a subnet address range specified
gcloud compute --your-project-id networks subnets create subnet-east-vpn --network=subnet-east-1 --region=us-west1 --range=10.128.0.0/20

```
 

firewall rule creates the subnet name “subnet-west-secure” the direction is ingress meaning the traffic that is allowed in. as you can see we created a firewall rule specifying the network as subnet-demo-gcp, followed by the allowed ports ssh, http


```
gcloud compute --your-project-id firewall-rules create subnet-west-secure --direction=INGRESS --priority=1000 --network=subnet-demo-gcp --action=ALLOW --rules=tcp:22,tcp80 --source-ranges=10.138.0.0/20
   
```



3. you probably noticed in the first part of the demonstration there’s a network `subnet-east-1`, the firewall was created for a different subnet, which is network `subnet-demo-gcp`


4. When creating firewall rules, you can specify for the firewall rule to be subnet specific, project wide or for specific IP ranges.

```
 gcloud config set project <PROJECT_ID_GOES_HERE> #sets the specified project 
 
 ```

```
 gcloud compute instances list #output list of instances 
    
 ```
 
 # understanding the basics 
 
Networks can contain one or more subnets in any given region, when using custom mode this goves you control over the subnet region instead of GCP choosing the region for you. 
 
when creating a subnet you must choose the lowest subnet for the mask, but don't worry google requires this but you must know what the lowest subnet is for the mask you choose. 
 
 
 # Monitoring & Logging with Stackdriver 
 
Stackdriver is used for monitoring, logging, and keeping a close eye on your resources, the amount of features and capabilities offered by stack driver is beyond the scope of this reference. but i do recommend you trying out the tutorials on [codelabs](https://codelabs.developers.google.com)

```

gcloud compute ssh "YOUR_INSTANCE_NAME_HERE 
 
 ```
 
 
 ```
 
 curl -sSO "https://dl.google.com/cloudagents/install-logging-agent.sh" #download the logging agent installation
 

 ```
 
 ```
 
 sudo bash install-logging-agent.sh #run the script
 
 ```
 
 
# remove the logging agent and fluentd

 
 
 ```
sudo service google-fluentd stop
sudo apt-get remove google-fluentd google-fluentd-catch-all-config 

```

```
 gcloud projects list #get projects list  
 
```

```

gcloud compute instances list #get instances status 

```
