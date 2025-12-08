#   Cloud Infrasture set up Bastion Host or Systerm manager
This document outlines the architecture and configuration of a secure, scalable AWS environment hosting [Application Name]. The infrastructure leverages public/private subnets, a bastion host for secure access, and encrypted S3 storage for data persistence.

2. Architecture Overview
Diagram
(Include a diagram here using AWS VPC Flow or Draw.io. Example structure below)

[Internet]  
│  
├── Internet Gateway (IGW)  
│   │  
│   └── Public Subnet (10.0.1.0/24)  
│       ├── Bastion Host (t3.medium)  
│       └── NAT Gateway  
│  
└── Private Subnet (10.0.2.0/24)  
    └── Application Server (c5.xlarge)  
        └── S3 Bucket (Mounted via IAM Role)  

Components
Component	Details
VPC	CIDR: 10.0.0.0/16
Public Subnet	CIDR: 10.0.1.0/24 (Hosts Bastion Host + NAT Gateway)
Private Subnet	CIDR: 10.0.2.0/24 (Hosts Application Server)
EC2 Instances	- Bastion: t3.medium (Public IP)
- Application: c5.xlarge (No Public IP)
NAT Gateway	Deployed in Public Subnet; EIP: [Elastic_IP_1]
Internet Gateway	Attached to VPC for public traffic.


3. Network Configuration
Route Tables
Route Table	Destination	Target
Public Route Table	0.0.0.0/0	Internet Gateway (IGW)
Private Route Table	0.0.0.0/0	NAT Gateway
Elastic IPs (EIPs)
Bastion Host: [Elastic_IP_1] (Public SSH access).

NAT Gateway: [Elastic_IP_2] (Outbound internet for private subnet).

bash
# Test SSH access to Bastion:  
ssh -i key.pem ec2-user@[Bastion_Elastic_IP]  

# Test SSH from Bastion to Private Instance:  
ssh -i key.pem ec2-user@[Private_Instance_Private_IP]  


# USE Terrafomr to create the cloud cnfiguration enivronment

Generate your access key from setting

![Alt text]<img width="1866" height="507" alt="Screenshot 2025-12-05 024102" src="https://github.com/user-attachments/assets/258cbd09-cb77-4ba4-986e-c3dd126fb47f" />

Download aws cli  

Download terraform  and add it to the enivronment variabale
 create a main.tf and write your variables 

run this 
terrafirm init

![Alt text]<img width="1839" height="919" alt="Screenshot 2025-12-05 045434" src="https://github.com/user-attachments/assets/87fdd70d-a1dc-4b18-95fd-559aafa470b0" />

terraform fmt 
terraform plan

![Alt text]<img width="1873" height="880" alt="Screenshot 2025-12-05 050449" src="https://github.com/user-attachments/assets/aede3b53-0daf-4acd-9ef2-5062010be74c" />

terraform apply 

![Alt text]<img width="1590" height="447" alt="Screenshot 2025-12-05 053035" src="https://github.com/user-attachments/assets/915feeb3-418d-45b7-9e55-374a576b6782" />

![Alt text]<img width="1590" height="447" alt="Screenshot 2025-12-05 053035" src="https://github.com/user-attachments/assets/e7b5509b-d8ef-4cb8-a222-5b5d0b11f26d" />

![Alt text]<img width="1908" height="540" alt="Screenshot 2025-12-05 053156" src="https://github.com/user-attachments/assets/8577d636-b68c-4632-8383-79502a9da775" />

![Alt text]<img width="957" height="272" alt="Screenshot 2025-12-05 053255" src="https://github.com/user-attachments/assets/d7fac09e-2861-4c94-a553-8640d5798885" />



1.  # Set Up environment
 
 **install all the tools with a bashscript called tools.sh** 

   ### use this command  to excute the script
   vim tools.sh
   chmod +x tools.sh
   sudo ./tools.sh

   ![Alt text]<img width="1631" height="860" alt="Screenshot 2025-12-05 075811" src="https://github.com/user-attachments/assets/c78dd21f-0c6c-45e9-bcd3-7c39b2d78b7d" />

   # Set up gtihub runner configure your vm as a runner 
1 Click the repository , click on settings
2 on the left side you would troll down to the action and select runners
3 click runners and select self hosted runner 
4) select linux and follow all the commands avaialabe . NOTED: instruction will be giving


 ![Alt text]<img width="836" height="421" alt="image" src="https://github.com/user-attachments/assets/f9e397c8-2fd4-4937-8124-b48dedb6832b" />

  ![Alt text] <img width="955" height="485" alt="Screenshot 2025-12-06 005441" src="https://github.com/user-attachments/assets/e65e9402-c4a3-46b3-a50f-600edef1eb2f" />


 




