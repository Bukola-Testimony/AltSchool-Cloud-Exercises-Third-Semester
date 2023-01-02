# AltSchool-Cloud-Exercises-Third-Semester
> ![AltSchool Cloud Exercices](/cloud3.JPG)


- [Back to first page](../README.md)
- [Overview](#overview) 
- [Task](#TASKS) 
- [Process](#Process)
- [Getting started](#Getting-Started)
- [Author](#author)

<br>
<br>

## Overview
### LEARNING CLOUD ENGINEERING WITH ALTSCHOOL.
> This is actually about the end of the first month towards the holodays (Christmas and new year) and so this is an holiday assignment.There has been so much new concepts learnt. Introduction to Virtual Pricate Cloud(VPC) Elatic load balancers (ELC), Autoscaling, Target groups, Listeners, Routing, networking etc. It is now time to put all these knowledge to the test, hence an holiday chalenge.

<br>

## TASK

- Set up 2 EC2 instances on AWS(use the free tier instances).
- Deploy an Nginx web server on these instances(you are free to use Ansible)
- Set up an ALB(Application Load balancer) to route requests to your EC2 instances
- Make sure that each server displays its own Hostname or IP address. You can use any programming language of your choice to display this.
- Work on building a personal portfolio and CV (Check out resumeworded.com).

## Important points to note

- I should not be able to access your web servers through their respective IP addresses. Access must be only via the load balancer
- You should define a logical network on the cloud for your servers.
- Your EC2 instances must be launched in a private network.
- Your Instances should not be assigned public IP addresses.
- You may or may not set up auto scaling(I advice you do for knowledge sake)
- You must submit a custom domain name(from a domain provider e.g. Route53) or the ALB’ domain name.

<br>

## Project Image

![s1](/Exercise-2/images/application-image.png)

<br>



## Process

- Log in to your AWS account and navigate to the VPC service.


<br>

## Getting Started
### Introduction

Creating a Virtual Private Cloud (VPC) with public and private subnets is a great way to isolate your applications and resources away from the public internet. This guide will provide step-by-step instructions on how to create a VPC with public and private subnets, a NAT gateway, and an Internet gateway in the Amazon Web Services (AWS) environment. We will use “my demo” as an example name for the VPC throughout this guide.


## **1. Creating VPC**

Open the Amazon VPC console at https://console.aws.amazon.com/vpc/

On the VPC Dashboard, choose Launch VPC Wizard.

![s1](/Exercise-2/images/vpc1.png)

On the VPC configuration Dashboard choosing VPC and more automatically launches Private Subnets, Public Subnets, Routing Tables and Subnet Associations, Internet GateWay, Elastic IP, IP CIDR block, Availability Zones and Network Access Translator.

On the Auto-generate input field, write the name of your VPC

![s1](/Exercise-2/images/vpc2.png)

Choose the number of Avalaibility Zones (AZ's) in which to create your NAT GateWay.

![s1](/Exercise-2/images/vpc4.png)

The image below shows the auto-generated configurations i.e. Subnets, Routes Tables and Network Connections.

![s1](/Exercise-2/images/vpc3.png)

## **2. Create a Private EC2 Instance**

Navigate to the ec2 console and click on Launch Instance

![s1](/Exercise-2/images/e1.png)

Write the name of your instances, select the number of instances and use Ubuntu as choice of Linux Distro.

![s1](/Exercise-2/images/e2.png)

Select your key-pair if you dont have a key-pair create one

Next, select the VPC that you previously created, and choose any of the private subnet, Disable the Auto-Assigned Public IP, and finally Create a Security Group keeping the default settings then click on Launch Instance.

![s1](/Exercise-2/images/e3.png)

## **3. Create a Bastion Host**

A bastion host is a server whose purpose is to provide access to a private network from an external network. This is necessary because our subnets are private, hence, the bastion host which is within the same VPC serves as a bridge to establibish connection to the private subnets. The best practice is that anyone who needs access to any of the computers inside the VPC must SSH into the bastion host first before doing another SSH to the instance they want to go to.

Navigate to the ec2 console and click on Launch Instance

Write the name of your instance, and use Ubuntu as the choice of Linux Distro.

![s1](/Exercise-2/images/bastion1.png)

Select your key-pair

Next, select the VPC that you previously created, and choose any of the public subnet, Enable the Auto-Assigned Public IP, and finally choose a Security Group keeping the default settings then click on Launch Instance.

![s1](/Exercise-2/images/bastion2.png)

## **4. SSH Connections**

Select on the Bastion Host Instance and click on connect which will launch a Dashboard.
![s1](/Exercise-2/images/connect1.png)

Select SSH client and follow the instructions on how to connect.

![s1](/Exercise-2/images/connect2.png)

Access the bastion host via SSH. Copy the keypair you downloaded to the bastion host server. Then, run chmod 400 yourkeypairname.pem

![s1](/Exercise-2/images/connect3.png)

Run chmod 400 yourkeypairname.pem, then access the Private Server via SSH from the Bastion host.

![s1](/Exercise-2/images/connect7.png)

## **5. Installation and Configuration of Nginx Server on Private EC2 Instances**

Using the following commands; update and install Nginx and login to the root user to setup static webpage.

    $ sudo apt update; sudo apt install nginx -y; sudo su

![s1](/Exercise-2/images/connect8.png)

From the root user, run the following commands to display the hostname of your server;

    # echo "<h1>This is my server2 $(hostname -f)</h1>" > /var/www/html/index.nginx-debian.html

Then cat your file to confirm that host is being displayed using;

    # cat /var/www/html/index.nginx-debian.html

Exit the root user and then enable, start, and confirm status of nginx server using the following commands

    $ sudo systemctl enable nginx; sudo systemctl start nginx; sudo systemctl status nginx

![s1](/Exercise-2/images/connect9.png)

Exit from the first Private server and from your Bastion host ssh into your second server and repeat whole process to update and install nginx, login to root user and echo your hostname, cat file to confirm hostname is being displayed, exit root user, and then enable, start, and confirm status of the nginx server.

## **6. Creating Target Group**

Navigate to Target Group and click on create Target Group

![s1](/Exercise-2/images/target1.png)

Choose instances as your target type and give your target group a name.

![s1](/Exercise-2/images/target2.png)

Select the VPC you have already created on the drop down menu and leave the default protocol on Http1.

![s1](/Exercise-2/images/target3.png)

Click on next

![s1](/Exercise-2/images/target4.png)

Then select the Private instances in your VPC and click on the include as pending.

![s1](/Exercise-2/images/target5.png)

Currently there is no load balancer configured to this target group. Click on the None associated and select the new load balancer.

![s1](/Exercise-2/images/target6.png)

## **7. Creating Application Load Balancer**

Give your Application Load Balancer a name and leave the Scheme and IP address type on default.

![s1](/Exercise-2/images/load1.png)

Then on Network Mapping select your VPC and choose your public subnets associated with your VPC.

![s1](/Exercise-2/images/load2.png)

For the Security Groups click on create new security group

![s1](/Exercise-2/images/load3.png)

Give your Security Group a name, brief description and ensure you choose your created VPC from the drop down menu.

![s1](/Exercise-2/images/load4.png)

Edit the Inbound rules to allow Http and Https traffic from anywhere and leave Outbound rules on default. Then click on create and return to the previous page to assign the newly created Security Group.

On the **Listeners and routing section**, select the target group previously created, leaving the rest of the configuration on default and finally click on create load balancers.

**NOTE:** The Load Balancers takes awhile to provision.

![s1](/Exercise-2/images/load5.png)

## **Configuring Application Load Balancer Security Group**

Navigate to your Security Group and select the security group. that is associated with your instances

![s1](/Exercise-2/images/s1.png)

Edit the inbound rules to allow traffic on only the load balancer by selecting the Security Group that is associated with the load balancer. Then save the rules.

![s1](/Exercise-2/images/s2.png)

Confirm the health status of your target groups, if it is unhealthy, re-start the nginx server and refresh the target groups page

    $ sudo systemctl restart nginx

![s1](/Exercise-2/images/health.png)

Now to check whether things are working properly let's test our Load Balancer Distribution. We will copy the Distribution domain name and enter it into our browser.

![s1](/Exercise-2/images/ip1.png)

![s1](/Exercise-2/images/ip2.png)


<br>
<br>

## Author

- Website - [Bukola Testimony](https://bukola-testimony.github.io/My-Portfolio-website/)
- Twitter - [@BukolaTestimony](https://twitter.com/BukolaTestimony)
