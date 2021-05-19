# iop-aws-services
## Introduction
IOP AWS Services contains AWS Cloudformation templates that can be used to quickly stand up AWS resources for a working software environment. These Cloudformation templates allow for managing the software infrastructure and easily replicating and making changes to infrastructure.

## Cloudformation Templates available
Currently, you can use the BaselineNetwork, BaselineSecurity, and LinuxBastionHost Cloudformation Templates. BaselineNetwork sets up a VPC, subnets, gateways, route tables, and routes. BaselineSecurity creates NACLs for the subnets. BaselineSecurity depends on the creation of BaselineNetwork. LinuxBastionHost deploys Linux bastion hosts into the VPC, the bastion hosts providing secure access to Linux instances located in the subnets. LinuxBastionHost also depends on the creation of BaselineNetwork.

## How to use
First, make sure you have downloaded the desired template files from this GitHub repository to your computer.
Log in to your AWS account and choose an AWS region where you want the AWS resources to be created. Navigate to the CloudFormation service and click Create stack. Typically, you will choose Create stack with new resources (standard). Choose "Template is ready" and "Upload a template file". Select the desired template file you have downloaded to your computer. Click Next. Enter an appropriate stack name: by default you can make the stack name the name of the template. You will see a list of parameters you can configure for your template. 

For BaselineNetwork, please choose the CIDRs you would like for your Subnets and VPC. The default CIDRs demonstrate the sizing framework. You may modify according to your needs, keeping in mind that 9 subnets within the VPC will be created so the VPC and Subnets should be sized accordingly. For example, by default, the VPC is set to /20, and the Subnets to /24.

For BaselineSecurity, please input the name of the BaselineNetwork stack you have created within the same region. By default, that name is assumed to be BaselineNetwork.

For LinuxBastion, please input the name of the BaselineNetwork you have created within the same region. By default, that name is assumed to be BaselineNetwork. Please also choose the CIDR you would like for allowed access to the bastion hosts. By default, the AMI for the instances is Amazon-Linux2-HVM, but you can change that to CentOS-7-HVM, Ubuntu-Server-20.04-LTS-HVM, or SUSE-SLES-15-HVM as desired. The instance type is set as t2.micro but you can change that as well. Decide on a name for the bastion host and the number of bastion hosts desired which is by default 3.

After you have entered the parameters, click next. You may add any appropriate tags to the stack, for example Key: Point of Contact, Value: your email. You can leave the rest of the options as pre-selected; ensure that Rollback on failure is set to Enabled. Click next, review your selections, and click Create Stack.
