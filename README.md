# Topic: Infrastructure-Creation

### Overview

> In this project we will write a circleCI job that creates infrastructure - an EC2 instance and the associated Security group using CloudFormation on AWS.

#### Prerequisites

> Key pair - You should have an [AWS EC2 key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)  already created in your AWS Console, and downloaded to your local mahcine. We are assuming the key pair name is udacity.pem.

> A public Github repository.

> An account in the [CircleCI](https://app.circleci.com/).

#### STEPS

##### Step 1: Set up a CircleCI project
- > Set up a CircleCI project:

- > Go to https://app.circleci.com/ and set up a new project associated with your Github repository.

- > If you repo does not contain a ./circleci/config.yml file, it will prompt you to create one. Choose a "hello-world" starter config file. The CircleCI will attempt the first build process. Don't worry if it fails at this moment.

- > Feel free to choose a ""hello-world" starter config.yml template or ensure to have a (blank) .circleci/config.yml file in your repo.

![image](https://user-images.githubusercontent.com/40290711/178592636-08d126ae-d61a-4f39-9dcd-75af47b69c17.png)

![Screenshot from 2022-07-12 17-10-14](https://user-images.githubusercontent.com/40290711/178594066-0d8141e9-a92f-4213-a766-47a4bd8dd15d.png)



##### Step 2: Set up Environment variables

- > To use the AWS CLI in your jobs you'll need to the following environment variables to the in Circle CI > Project Settings > environment variables. The value of these variables can be fetched from the AWS IAM user.

- > If not already, create an AWS IAM user with programmatic access, and it will generate these credentials.
```
AWS_ACCESS_KEY_ID
AWS_DEFAULT_REGION
AWS_SECRET_ACCESS_KEY
```

- > Note - While saving the environment variables in the Circle CI project settings, use capital case as discussed in this thread and also mentioned here (see the DEFAULT column for the correct names).

- > Another useful reference: Setting an environment variable in a project. Do read about the various types of environment variables and their relative priorities.

![image](https://user-images.githubusercontent.com/40290711/178605234-8eaa991d-a459-4a89-9def-0f70ae8df33b.png)

##### Step 3. Create the CloudFormation template
- > Create a simple template - template.yml that will create an EC2 instance and the associated security group. This should be pushed into your git repo.

```
# Exercise - Rollback
AWSTemplateFormatVersion: 2010-09-09
Description: "Author: OLORUNTOBI"
Resources:
  EC2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      SecurityGroups:
        - !Ref InstanceSecurityGroup
      # Change this, as applicable to you      
      KeyName: udacity
      # Change this, as applicable to you
      # You may need to find out what instance types are available in your region - use https://cloud-images.ubuntu.com/locator/ec2/
      ImageId: 'ami-052efd3df9dad4825' 
      InstanceType: t2.micro
  InstanceSecurityGroup:
    Type: 'AWS::EC2::SecurityGroup'
    Properties:
      GroupDescription: Enable SSH access via port 22
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: '22'
          ToPort: '22'
          CidrIp: 0.0.0.0/0 


```
> ***Important points:***

> Be mindful of copy-pasting the code above. It may break the YAML indentation.
> Change the KeyName and ImageId, as applicable to you.
> We have used the udacity as the KeyName. That refers to the key pair we created before.
> Fetch and use the correct AMI ID similar to as shown in the snapshot below.


