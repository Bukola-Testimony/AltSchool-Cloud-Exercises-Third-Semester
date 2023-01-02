## Launch instance in VPC Public 1A
aws ec2 run-instances --image-id ami-0574da719dca65348 --instance-type t2.micro --security-group-ids sg-0a0c3a5d6421e7ce1 --subnet-id subnet-0554ecb422fc8626a --key-name ansiblekeys --user-data file://userdata-Nginx-ubuntu


## Launch instance in VPC Private 1A
aws ec2 run-instances --image-id ami-0574da719dca65348 --instance-type t2.micro --security-group-ids sg-0a0c3a5d6421e7ce1 --subnet-id subnet-06bb72e03814b1b94 --key-name ansiblekeys --user-data file://userdata-Nginx-ubuntu


## Launch instance in VPC Private 1B
aws ec2 run-instances --image-id ami-0574da719dca65348 --instance-type t2.micro --security-group-ids sg-0a0c3a5d6421e7ce1 --subnet-id subnet-0bc60ce2862d84bc3 --key-name ansiblekeys --user-data file://userdata-Nginx-ubuntu



## Terminate instances

aws ec2 terminate-instances --instance-ids i-0954022db0f74870a <value> <value>