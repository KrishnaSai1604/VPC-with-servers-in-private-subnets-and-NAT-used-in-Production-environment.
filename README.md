# First-AWS-Project
Created a VPC that can be used for servers in a production environment.
To improve the resiliency deployed the servers in two Availability zones using Auto Scaling Group and an Apllication Load Balancer.
For additional security deployed the servers in private subnets.
The server recieves the request through Load Balancer.
These servers can connect to the internet using NAT Gateways.
By this way we can Securely deploy a static application on servers in aws private subnets in 2 AZ's using ASG and ALB for high end availability.
