# aws-spot-instance-cf

Cloudformation template for a spot instance in Amazon Web Services (AWS). 

AWS sells sparse computing capacity trough spot instances at a great discount. This gives one ability to use powerful compute at a fraction of a price. 

Template creates a spot instance with given parameters. Template assumes EBS backed AMI is used. It is currently set to delete the EBS on termination, but if one needs to maintain the EBS for future use, this option can be altered to match the need. Template also creates a role that allows the instance to access S3 service. You can use this template as a way to start spot instance or to develop from here the needed template. 

Setting spot instances with cf template allows one to also delete the whole set up with the deleting of the stack, keeping AWS environment clean. 

You can check the current spot pricing from here https://aws.amazon.com/ec2/spot/pricing/ 

## Before creating cf template

To start the spot instance you should have the following information present that are passed to cf as parameters. 

1. VpcId: VPC where you want to launch the instance (this can be the default one)
2. AMI: AMI of the instance (AWS AMI listing for different regions can be found here https://aws.amazon.com/amazon-linux-ami/ ). You should use EBS backed HVM instance type. 
3. Instance: Instance family type and size (for example m5.xlarge wich gives you 4 cpu and 16 Gb ram)
4. KeyPair: Key pair in the AWS. If you do not have one, create one in the AWS IAM service (https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html ).
5. UserIpAddressCIDR: Your ip. You can get from here http://checkip.amazonaws.com/ . Give your ip as CIDR block in the template (e.g. <your.ip.address.here>/32)

## To clean up

To clean up simply delete the cloudformation stack.


