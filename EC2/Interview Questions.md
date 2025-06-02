# EC2 Interview Questions

## 🔹 Basic EC2 Concepts

1. **What is Amazon EC2 and how does it work?**  
   Amazon EC2 (Elastic Compute Cloud) is a web service that provides resizable compute capacity in the cloud. It allows users to run virtual machines (instances) with different configurations. Users can scale up/down based on demand.

2. **What are the different instance types in EC2? How do you choose the right one?**  
   Instance types include General Purpose (t2, t3), Compute Optimized (c5), Memory Optimized (r5), Storage Optimized (i3), etc. The choice depends on workload requirements such as CPU, memory, and IOPS.

3. **What is an AMI and what does it contain?**  
   Amazon Machine Image (AMI) is a template that contains the software configuration (OS, application server, applications) required to launch an instance.

4. **How do you launch an EC2 instance using the AWS Management Console and CLI?**  
   - Console: Go to EC2 Dashboard > Launch Instance > Select AMI > Choose Instance Type > Configure > Launch.  
   - CLI: Use `aws ec2 run-instances` with required parameters.

5. **What is the difference between EC2 and EBS?**  
   EC2 is a virtual server; EBS (Elastic Block Store) is virtual disk storage attached to EC2 instances.

## 🔹 Security and Access

6. **What are security groups in EC2? How do they differ from NACLs?**  
   Security groups act as virtual firewalls for instances to control inbound/outbound traffic. NACLs are stateless and operate at the subnet level.

7. **What is a key pair in EC2, and why is it important?**  
   Key pairs (public/private) are used to securely SSH into EC2 instances. AWS stores the public key, and the user downloads the private key.

8. **How would you SSH into an EC2 instance?**  
   Use the command `ssh -i <key.pem> ec2-user@<public-ip>` with the private key file and the instance’s public IP.

9. **What is an Elastic IP? Why and when would you use it?**  
   An Elastic IP is a static public IPv4 address that can be associated with EC2 instances. It is used to maintain a fixed IP address despite instance stops/restarts.

10. **How do you securely connect to your EC2 instance without exposing the private key?**  
    Use EC2 Instance Connect (browser-based), bastion host, or Systems Manager Session Manager.

## 🔹 Storage and Volumes

11. **What is the difference between EBS and Instance Store?**  
    EBS is persistent and survives instance stop/start. Instance Store is temporary and data is lost if the instance is stopped/terminated.

12. **Can you resize or modify an EBS volume attached to an EC2 instance? How?**  
    Yes, use the AWS Console or CLI to modify the volume, then use OS-level tools (like `resize2fs` for Linux) to resize the filesystem.

13. **What are the steps to back up an EC2 instance?**  
    - Create an AMI  
    - Take EBS snapshots  
    - Use AWS Backup service

14. **How can you automate the creation of AMIs from EC2?**  
    Use AWS CLI/SDK with automation tools like Lambda or scheduled tasks using AWS EventBridge.

## 🔹 Networking

15. **What is a VPC and how does EC2 fit into it?**  
    A Virtual Private Cloud (VPC) is a virtual network. EC2 instances are launched inside subnets of a VPC, allowing control over networking.

16. **How do you configure EC2 instances in public and private subnets?**  
    - Public subnet: Attach Internet Gateway and public IP  
    - Private subnet: Use NAT Gateway for internet access without exposing public IP

17. **How does EC2 handle inbound and outbound traffic?**  
    Traffic is controlled using security groups (instance level) and NACLs (subnet level).

## 🔹 Scaling and Availability

18. **What is an Auto Scaling Group (ASG) in EC2?**  
    ASG automatically scales EC2 instances in or out based on defined metrics (CPU, traffic, etc.) to maintain availability and performance.

19. **How do you implement High Availability (HA) with EC2?**  
    Deploy EC2 instances across multiple Availability Zones (AZs), use Elastic Load Balancers (ELB), and Auto Scaling.

20. **What is the role of Load Balancer in EC2 setup?**  
    Distributes incoming application traffic across multiple EC2 instances in different AZs for fault tolerance.

21. **How does EC2 work with Route 53 for DNS routing?**  
    Route 53 routes user requests to EC2 instances using domain names, enabling geo-based routing, failover, and weighted load balancing.

## 🔹 Pricing and Cost Optimization

22. **What are the different pricing models for EC2?**  
    - On-demand  
    - Spot Instances  
    - Reserved Instances  
    - Savings Plans  
    - Dedicated Hosts

23. **When should you use Spot Instances over On-Demand?**  
    For fault-tolerant and flexible applications that can handle interruptions, such as big data and CI/CD jobs.

24. **What are Reserved Instances and when would you use them?**  
    They offer significant discounts for long-term (1-3 years) workloads with predictable usage.

25. **How do you monitor and optimize EC2 costs in DevOps projects?**  
    Use Cost Explorer, Budgets, CloudWatch metrics, Rightsizing recommendations, and automation for start/stop unused resources.

## 🔹 Automation & DevOps Integration

26. **How do you provision EC2 instances using Terraform/CloudFormation?**  
    Define infrastructure as code using `.tf` or YAML/JSON templates, specifying instance type, AMI, and key pairs.

27. **How do you install software or run scripts automatically on EC2?**  
    Use user data scripts during instance launch to install packages and configure the environment.

28. **How do you integrate EC2 into a CI/CD pipeline (e.g., CodeDeploy)?**  
    Use AWS CodeDeploy with deployment groups tied to EC2 instances to automatically push application updates.

29. **What are user data scripts and how are they used in EC2?**  
    User data scripts run at the first boot of an EC2 instance, often used for bootstrapping software.

30. **How can Jenkins deploy code to EC2 instances?**  
    Use SSH or CodeDeploy plugins, configure credentials, and trigger deployment jobs from Jenkins pipelines.