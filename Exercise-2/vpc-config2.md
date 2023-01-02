## Create VPC
Name: altschool-VPC
IPv4 CIDR Block: 10.1.0.0/16

## Create Subnets

Name: altschool-Public1
Availability Zone: us-east-1c
IPv4 CIDR Block: 10.1.1.0/24

Name: altschool-Public2
Availability Zone: us-east-1d
IPv4 CIDR Block: 10.1.2.0/24

Name: altschool-Private1
Availability Zone: us-east-1c
IPv4 CIDR Block: 10.1.3.0/24

Name: altschool-Private2
Availability Zone: us-east-1d
IPv4 CIDR Block: 10.1.4.0/24


## Create private route table
Name: Altschool-Private-RT
 VPC: altschool-VPC
Explicit Subnet associations: altschool-Private1, altschool-Private2


## Name Public route table
Name: Altschool-Public-RT


## Create Internet Gateway
Name: Altschool-internet-gateway
Attach to VPC: altschool-VPC

#Edit Public route table ( Altschool-Public-RT)
Destination: 0.0.0.0/0 
Target: Altschool-internet-gateway


## Create Nat Gateway
Name: Altschool-nat-gateway
subnet: altschool-Public1
Allocate Elastic IP: Create new EIP



## Edit Private route table  ( Altschool-Private-RT)
Destination: 0.0.0.0/0 
Target: Altschool-nat-gateway






























