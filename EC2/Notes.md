# EC2 (Elastic Compute Cloud)

• Amazon EC2 is a web service that provides resizable compute capacity in the cloud.  
You can scale the compute capacity up and down as per the computing requirement changes.  
Amazon EC2 changes the economics of computing by allowing you to pay only for the resources that you actually use.  
• EC2 is an example of IAAS  
• We can scale the compute capacity up and down as per the computing requirement changes.

## Features of EC2
• Provides scalable computing capacity  
• Launch as many or as few virtual servers as you need  
• Configure security and networking  
• Manage storage  

## Amazon Machine Image (AMI)
• Its gives the basic information about the instance created also shown running states of instance.

## Instance Type
• It store the information about instance such as ram, cpu etc.

## Key Pairs
a) Used secure system to store the private key  
b) Public key is store by AWS  
c) Private key is store in secure place instead of password we can used a key pair to access the ec2  
d) Private key never be recovered  

## Amazon EBS (Elastic Block Store) Volumes
• EC2 is a virtual server in a cloud while EBS is a virtual disc in a cloud.  
• Amazon EBS allows you to create storage volume and attach them in to the EC2 instances.

## Security Group
• Used for handle the incoming and outgoing traffic.  
• We can modify the security groups according to our requirement.

## Elastic IP Address
• This feature provides static public IPv4 addresses for dynamic cloud computing.  
• This ip's can be attached to EC2 instances.  
• Elastic IP can be quickly re-map to new instances, if your current EC2 instance fails

## Tags
• It's a meta data that you can define for your amazon EC2 resources.  
• Tags helps you to classify our AWS resources in different ways If you have number of resources then tag help us to find the specific resource

## Virtual Private Cloud
• It helps you to define in which amazon VPC you want to launch the instance.

## Amazon EC2 Pricing
Amazon EC2 instances are priced per second according to five different options:

• On-demand (you can pay as per your demand like if you want service for 1hr then you can only able to pay for 1hr and then you can stop)  
• Spot instances (Spot Instances are useful for those applications that have flexible start and end time, discounted short-term capacity if available)  
• Savings Plans (commitment to a certain amount of usage)  
• Reserved Instances (discounted reserved long-term capacity, if your application is ready and you have long term plane then you can used this pricing)  
• Dedicated Hosts (A dedicated host is a physical server with EC2 instance capacity which is fully dedicated to your use., on-demand hourly or by reserved instances)
