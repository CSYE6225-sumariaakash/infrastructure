# infrastructure
Infra

# 001568622 Assign09

Create Load Balancer Security Group
Create a security group for the load balancer to access the web application.
Add ingress rule to allow TCP traffic on ports 80, and 443 from anywhere in the world.
This security group will be referred to as the load balancer security group.

App Security Group Updates
Update the EC2 security group for your EC2 instances that will host web applications.
The ingress rule should allow TCP traffic on ports 22 and port on which your application runs.
The Source of the traffic should be the load balancer security group.
Restrict access to the instance from the internet.

The Auto Scaling Application Stack
So far our web application has been accessible by the IP address of the EC2 instance on HTTP protocol. We will now disable direct access to our web application using the IP address of the EC2 instance. The web application will now only be accessible from the load balancer.

Infrastructure as Code w/CloudFormation
DNS & EC2 Instance A Record
Route53 should be updated from the CloudFormation template.
The CloudFormation template should add/update A record to the Route53 zone so that your domain points to your EC2 instance and your web application is accessible thru http://your-domain-name.tld/Links to an external site..
Your application must be accessible using root context i.e. http://your-domain-name.tld/Links to an external site. and not http://your-domain-name.tld/app-0.1/

# infrastructure/aws

#This assignment will focus on setting up our networking resources such as Virtual Private Cloud (VPC), Internet Gateway, Route Tables, and Routes. We will use AWS CloudFormation for infrastructure setup and tear down.

# Tasks Accomplished:

1. Created a Stack using Amazon CloudFormation

2. Deleted a Stack using Amazon CloudFormation

3. Created multiple VPCs (and resources) without any conflicts in the same AWS account & same region.

4. Created another VPCs (and resources) without any conflicts in different AWS Region.

# What you need:

1. Install AWS CLI on your System.

2. IDE

3. 2 new profiles, not the default one.

# Steps:

1. To create a Stack, hit the following command in your AWS CLI

---------------------------------------------------------------------------
aws cloudformation --profile demo create-stack --stack-name stackname --template-body file://csye6225-infra.yaml --parameters ParameterKey=VpcCIDR,ParameterValue=10.0.0.0/16 ParameterKey=PublicSubnet1CIDR,ParameterValue=10.0.1.0/24 ParameterKey=PublicSubnet2CIDR,ParameterValue=10.0.2.0/24 ParameterKey=PublicSubnet3CIDR,ParameterValue=10.0.3.0/24 ParameterKey=envName,ParameterValue=demo ParameterKey=Subdomain,ParameterValue=demo ParameterKey=ImageId,ParameterValue=ami-ID  --region=us-east-1 --capabilities CAPABILITY_NAMED_IAM


2. To delete a Stack, hit the following command in your AWS CLI

-------------------------------------------------------------------------------
aws cloudformation --profile dev delete-stack --stack-name Stack1 --region us-east-1 

# COMMANDS FOR ASSIGN09:

Stack up

aws cloudformation deploy --profile demo --template-file csye6225_infra.yml  --parameter-overrides KeyName=awskey ImageId=ami-000111 --stack-name stackname --region=us-east-1 --capabilities CAPABILITY_NAMED_IAM

AWS Command to import the SSL certificate into AWS ACM

aws acm import-certificate --certificate fileb://Certificate.pem
--certificate-chain fileb://CertificateChain.pem
--private-key fileb://PrivateKey.pem
