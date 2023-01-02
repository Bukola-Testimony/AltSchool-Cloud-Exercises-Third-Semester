
## CREATE AN AUTO SCALING GROUP
To create auto scaling group, First create a Launch Template or AMI

<br>

## CREATE A LAUCH TEMPLATE

2. Go to the EC2 dashboard and select ‘Launch Templates’ in the left-hand menu.
3. Click on the ‘Create Launch Template’ button.
4. Enter a name for the Launch Template: e.g demo-launch-template
5. Enter a description for the Launch Template: e.g This is a demo teplate
6. Select the AMI that the Launch Template should use: click on quick start: e.g Ubuntu
7. Select the Instance Type: t2.micro
8. Select the key pair
9. At the "Network settings": do not include a subnet
10. Select the Security Groups: e.g demo-security-group (The security group attached to the VPC)
11. Under "Advanced network configuration"  Select the User Data that should be associated with the Launch Template.
12. Click on the ‘Create Launch Template
<br>
<br>



## NOW CREATE AN AUTO SCALING GROUP

2. From the EC2 dashboard  select ‘Auto Scaling Groups’ in the left-hand menu.
3. Click on the ‘Create Auto Scaling Group’.
4. Enter a name for the Auto Scaling Group:e.g demo-auto-scaling
5. Select the Launch Configuration that you just created: demo-launch-template
6. click on "next"
7. On the "Choose instance launch options"  page Select the VPC for the Auto Scaling Group: demo-VPC
8.  Select the Availability Zones: e.g demo-Private subnets 1&2.
9. Click "next"
10. On the "Configure advanced options" page choose "Attach to an existing load balancer"
11. Next "Choose from your load balancer target groups" and select the created target group: e.g demo-target-group
12. click on next
13. On the "Configure group size and Scaling Policies" page, you can specify the following details:
Group Size:
Desired capacity: 2
Minimum capacity: 2
Maximum capacity: 3

14. For Scaling policies select the "Target tracking scaling policy"
15. You may leave the Target value on default settings.
16: click on "next"
17: Select the tags that should be associated with the Auto Scaling Group.
You may add tags to the instances that will be spinned up.
18: click on next and review your settings
19:  Click on the ‘Create Auto Scaling Group’ button to create the Auto Scaling Group.






















