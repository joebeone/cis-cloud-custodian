# cis-cloud-custodian
Cloud Custodian Policies for CIS Benchmark level 1

##Prerequisites 
-Directions below assume windows environment for development

# Setup Development Environment:

## Clone Repo
1) git clone <repo-url>

## Install Cloud Custodian
1) Install Python3
2) Create python virtual environment
```
python -m venv .python
```

3) Source new python virtual environment
```
./.python/Scripts/activate
```.

4) Install Cloud Custodian
```
(.python) pip install c7n  #AWS Package
(.python) pip install c7n-mailer #mailer (i.e. AWS SES)
(.python) pip install c7n-org  #Deploy accross regions and organizations

```

## Install & Configure AWS Credentials
Reference: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html

5) Run AWS Configure & Enter accesskey & secretkey
```
 $ aws configure
   AWS Access Key ID [None]: accesskey
   AWS Secret Access Key [None]: secretkey
   Default region name [None]: us-west-2
   Default output format [None]
```

6) list aws profiles
   
```
 cat ~/.aws/config
  [default]
  region=us-east-2

  [profile <profile-name1>]
  region=us-east-1

  [profile <profile-name2>]
  region=us-west-1
  
  ...

```
7) Use *--profile* (example: --profile <profile-name>) flag for AWS cli commands or Setup *AWS_PROFILE*


# Setup AWS sqs


# Create Account Config file


# Deploy Policy to new AWS Account



#Commands to deploy 
c7n-org run -c .\accounts\accounts.yml -s output -u .\policies\iam.yml  --dryrun
c7n-org run -c .\accounts\accounts.yml -s output -u .\policies\logging.yml --cache-period 0 

#To get resource key filters:
custodian run  .\policies\resource_key\ec2.yml -s .\output\