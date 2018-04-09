# tech-talk

## What is Spinnaker?

## Setup Instruction

Setting up Spinakker has three steps:

### Prepare an AWS Account

1. If you don’t already have an AWS account, create one.
2. Choose the AWS Region where you want to deploy Spinnaker on AWS. Currently supported regions are  US East (N.Virginia), US West (N. California), US West (Oregon), and South America (SãoPaulo).
3. Create a key pair in your preferred region.
4. Open the IAM console at at https://console.aws.amazon.com/iam/, create an IAM role called BaseIAMRole, and choose Amazon EC2 as the role type. EC2 instances launched with Spinnaker will be associated with this role.

### Launch the Quick Start

1. Launch the AWS CloudFormation template into your AWS account and create a Stack. The template is launched in the US West (Oregon) region by default. This template is accessible in https://s3.amazonaws.com/quickstart-reference/spinnaker/latest/templates/quickstart-spinnakercf.template . 
2. On the Select Template page, keep the default setting for the template URL, and then choose Next.
3. On the Specify Details page, review the parameters for the template. Enter values for the parameters that require your input. For all other parameters, you can customize the default settings provided by the template. Suggested parameters are as follows: 

  
      ![parameters](https://media.github.ncsu.edu/user/8135/files/07f85076-3b73-11e8-9cad-350dacfd1e48)


4. On the Review page, review and confirm the template settings. Under Capabilities, select the check box to acknowledge that the template will create IAM resources.
5. Choose Create to deploy the stack.
6. Monitor the status of the stack. When the status is CREATE_COMPLETE, the deployment is complete. It takes about 5 minutes.

### Test the Deployment

1. Copy SSHString1 from Output tab of created stack and add `-i keypair path` and execute it:

```
ssh -i keys/devops.pem –A -L 9000:localhost:9000 -L 8084:localhost:8084 -L 8087:localhost:8087 ec2-user@ec2-198-51-100-1.compute1.amazonaws.com
```
2. Copy the keypair .pem file to bastion host after connecting to it.
3. Copy SSHString1 from Output tab of created stack and add `-i keypair path` and execute it inside bastion host:

```
ssh -i keys/devops.pem –L 9000:localhost:9000 -L 8084:localhost:8084 -L 8087:localhost:8087 ubuntu@10.100.10.182

```
4. Spinnaker is accessible in following address:  http://localhost:9000 .


## Demo

The demo of using Spinnaker can be found [here](https://www.youtube.com/watch?v=3R59USSvtqQ&t=26s).
