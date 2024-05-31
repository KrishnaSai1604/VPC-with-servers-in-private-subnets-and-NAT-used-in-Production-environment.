# First-AWS-Project
Created a VPC that can be used for servers in a production environment.
To improve the resiliency deployed the servers in two Availability zones using Auto Scaling Group and an Apllication Load Balancer.
For additional security deployed the servers in private subnets.
The server recieves the request through Load Balancer.
These servers can connect to the internet using NAT Gateways.
By this way we can Securely deploy a static application on servers in aws private subnets in 2 AZ's using ASG and ALB for high end availability.
# Architecture
![Screenshot 2024-05-22 170700](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/190e8d65-bdfa-4e3e-a898-c2628b8fbc0b)
# Step1
Create a VPC with 2 Availability Zones with public subnet and private subnet in each zone.
Public subnet contains NAT Gateway and LoadBalancer.
![Screenshot 2024-05-23 183117](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/464a59c9-e3d7-48b3-8eff-7e58bb59cd55)
# Step2
The Servers are launched in the private subnets by using Auto Scaling Group and recieves traffic from LoadBalancer.
![Screenshot 2024-05-23 183138](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/9b48d8ac-5b06-4333-9a64-fe3f22af4ed5)
While Creating ASG we need to launch a new template which will be used in Auto Scaling Group.
![Screenshot 2024-05-23 183226](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/556146e1-3fce-4821-b9f8-1eb8c029b6c3)
# Step3
Go to EC2 Instances and check we can see 2 instances are up and running by Auto scaling group.
![Screenshot 2024-05-23 183049](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/6b760020-fcb2-47aa-bb74-43807da8c924)
Now to connect and deploy a static application in these 2 servers in private subnet , we create a new server Bastion host/Jump server in public subnet and connect to this public server.
After connecting to this Bastion host copy .pem file(Key value pair used while creating server) and by using this .pem file we can connect to the servers in private subnets and run the application there.
# Step4
Create Application LoadBalancer in public subnet by attching the 2 instances in private subnet as Target groups.
![Screenshot 2024-05-23 201517](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/906cd0cb-ae63-4ae5-a2f7-e5a3b716fd7c)
Now the server recieves the request through Load Balancer.
# Step5
Select the Application LoadBalancer and copy the address link and check in the new tab.
![Screenshot 2024-05-23 201551](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/74091482-ae85-4bac-8b4c-31d3e17f3b3a)

![Screenshot 2024-05-23 192744](https://github.com/KrishnaSai1604/First-AWS-Project/assets/169227593/47cef5f9-a0d4-4034-84a2-8c13a069772a)
For every new request we can clearly see that Application LoadBalancer is migrating the traffic once to the each servers in different Availability Zones. 
# Conclusion
By this approach we can Securely deploy a static application on servers in aws private subnets to be more secure. And for high availability we deployed servers in 2 Availability Zones by using Auto Scaling Group and Application Load Balancer for managing the traffic.
