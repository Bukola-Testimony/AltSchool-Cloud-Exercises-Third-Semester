
## CREATE AN AUTO SCALING GROUP
- To create auto scaling group, First create a Launch Template or AMI

<br>

## CREATE A LAUCH TEMPLATE

- Go to the EC2 dashboard and select ‘Launch Templates’ in the left-hand menu.
- Click on the ‘Create Launch Template’ button.
- Enter a name for the Launch Template: e.g demo-launch-template
- Enter a description for the Launch Template: e.g This is a demo teplate
- Select the AMI that the Launch Template should use: click on quick start: e.g Ubuntu
- Select the Instance Type: t2.micro
- Select the key pair
- At the "Network settings": do not include a subnet
- Select the Security Groups: e.g demo-security-group (The security group attached to the VPC)
- Under "Advanced network configuration"  Select the User Data that should be associated with the Launch Template.
- Click on the ‘Create Launch Template
<br>
<br>



## NOW CREATE AN AUTO SCALING GROUP

- From the EC2 dashboard  select ‘Auto Scaling Groups’ in the left-hand menu.
- Click on the ‘Create Auto Scaling Group’.
- Enter a name for the Auto Scaling Group:e.g demo-auto-scaling
- Select the Launch Configuration that you just created: demo-launch-template
- click on "next"
- On the "Choose instance launch options"  page Select the VPC for the Auto Scaling Group: demo-VPC
-  Select the Availability Zones: e.g demo-Private subnets 1&2.
- Click "next"
- On the "Configure advanced options" page choose "Attach to an existing load balancer"
- Next "Choose from your load balancer target groups" and select the created target group: e.g demo-target-group
- click on next
- On the "Configure group size and Scaling Policies" page, you can specify the following details:
Group Size:
Desired capacity: 2
Minimum capacity: 2
Maximum capacity: 3

- For Scaling policies select the "Target tracking scaling policy"
- You may leave the Target value on default settings.
- click on "next"
- Select the tags that should be associated with the Auto Scaling Group.
You may add tags to the instances that will be spinned up.
- click on next and review your settings
-  Click on the ‘Create Auto Scaling Group’ button to create the Auto Scaling Group.






















