# infrastructure
Infra

# 001568622

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
aws cloudformation --profile dev create-stack --stack-name Stack1 --template-body file://csye6225-infra.yml --region us-east-1 --parameters ParameterKey=VpcName,ParameterValue=testVPC1 ParameterKey=VpcCIDR,ParameterValue=10.0.0.0/16 ParameterKey=Subnet1CIDR,ParameterValue=10.0.1.0/24 ParameterKey=Subnet2CIDR,ParameterValue=10.0.2.0/24 ParameterKey=Subnet3CIDR,ParameterValue=10.0.3.0/24


2. To delete a Stack, hit the following command in your AWS CLI

-------------------------------------------------------------------------------
aws cloudformation --profile dev delete-stack --stack-name Stack1 --region us-east-1 
