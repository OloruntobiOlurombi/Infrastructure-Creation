# Topic: Infrastructure-Creation

### Overview

> In this project we will write a circleCI job that creates infrastructure - an EC2 instance and the associated Security group using CloudFormation on AWS.

#### Prerequisites

> Key pair - You should have an [AWS EC2 key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)  already created in your AWS Console, and downloaded to your local mahcine. We are assuming the key pair name is udacity.pem.

> A public Github repository.

> An account in the [CircleCI](https://app.circleci.com/).

#### STEPS

##### Step 1
> Set up a CircleCI project:
> Go to https://app.circleci.com/ and set up a new project associated with your Github repository.
> If you repo does not contain a ./circleci/config.yml file, it will prompt you to create one. Choose a "hello-world" starter config file. The CircleCI will attempt the first build process. Don't worry if it fails at this moment.
> Feel free to choose a ""hello-world" starter config.yml template or ensure to have a (blank) .circleci/config.yml file in your repo.

![image](https://user-images.githubusercontent.com/40290711/178592636-08d126ae-d61a-4f39-9dcd-75af47b69c17.png)





