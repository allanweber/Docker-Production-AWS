# AWS With Docker

## IAM Best Practicies

* TWO factor authentications
* Assign privilegies to IAM roles, then IAM roles to groups
  * IAM role includes policies to allows access to AWS resources
  * This allows temporary user elevations access

* Create account alias
  * IAM > customize > create alias (allan-alias)
* Create IAM role (admin)
  * Another Account > Account ID - flag MFA > AdministratorAccess

## AWS CLI

* pip install awscli
* AWS console > IAM > User > Create access key
* Add to .bash, .zshrc or etc: `export PATH=~/.local/bin:$PATH`
* `source ~/.zshrc`
* `export AWS_PROFILE=allan-aws-free-admin`
* `aws configure`
* Test access: `aws ec2 describe vpcs`

## ECS

<img src="./img/1.png" width="50%" height="50%"/>

* Create new ECR repository: [https://eu-central-1.console.aws.amazon.com/ecr/repositories?region=eu-central-1](https://eu-central-1.console.aws.amazon.com/ecr/repositories?region=eu-central-1)
* Create new Repository
* `eval $(aws ecr get-login --no-include-email)`
* Click **View push commands** to see build tag and push commands
* **For microtrader project run**:
  * `make test`
  * `make tag:default`
  * `make publish`

### ECS Cluster

* Create a cluster filling the fields
* Select to create a new Security Group allowing SSH port 22 from anywhere

#### Log in into the cluster instance

* Copy the ec2 instance IPV4 public ip address
* `sudo chmod 400 ~/.ssh/allan-admin.pem`
* On WSL copy the .pem from windows .ssh to `\\wsl$\Ubuntu-20.04\home\USER\.ssh`
* `ssh -i ~/.ssh/allan-admin.pem ec2-user@ec2-3-68-114-38.eu-central-1.compute.amazonaws.com`
* `docker ps`
* `sudo yum install jq -y`
* `docker inspect -f '{{json .HostConfig.Binds}}' ecs-agent | j`
* Cluster logs: `ls -l /var/log/ecs`
* See logs: `cat /var/log/ecs/ecs-agent.log`
* Get cluster info: `curl -s localhost:51678/v1/metadata | jq`
* Show ECS services or tasks: `curl -s localhost:51678/v1/tasks | jq`

## OLDER Prerequisites Packages

`pip3 install ansible`

`pip3 install boto3 netaddr`

`sudo -H easy_install pip`

`sudo -H /usr/bin/python -m pip install boto3 --ignore-installed six`

`brew unlink python`

`brew link --overwrite python`

## Other Recommended Tools

`brew install tree`

## Source Repository

[https://github.com/docker-production-aws](https://github.com/docker-production-aws)

## Frameworks

[https://vertx.io/docs/#microservices](https://vertx.io/docs/#microservices)

[App Sample - http://escoffier.me/vertx-hol/](http://escoffier.me/vertx-hol/)

## Projects

[Microtrader](https://github.com/allanweber/microtrader)

[Microtrader-base](https://github.com/allanweber/microtrader-base)
