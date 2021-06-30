# AWS With Docker

# IAM Best Practicies
* TWO factor authentications
* Assign prevvilegies to IAM roles, then IAM roles to groups
  * IAM role includes policies to allows access to AWS resources
  * This allows temporary user elevations access

* Create account alias
  * IAM > customize > create alias (allan-alias)
* Create IAM role (admin)
  * Another Account > Accouint ID - flag MFA > AdministratorAccess
  
# AWS CLI
* pip install awscli
* AWS console > IAM > User > Create access key
* Add to .bash, .zshrc or etc: `export PATH=~/.local/bin:$PATH`
* `source ~/.zshrc`
* `export AWS_PROFILE=allan-aws-free-admin`
* `aws configure`
* Test access: `aws ec2 describe vpcs`

# ECR
* 
  
## Prerequisites Packages

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
