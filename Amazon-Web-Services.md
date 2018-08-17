## Intro

* Virtual Private Cloud (VPC): Virtual network that allows fast communication between resources, while limiting communication from the outside
    * Can have public and private subnets
* Security Group:
    * Manages communication between your VPC and the internet
    * Manages communication between AWS resources
* Amazon Machine Image (AMI): Template for creating environments
* S3: Storage and backup
* EBS Volume: Hard drive for a compute resource

## Elasticity vs. Scalability

* Elasticity implies that something stretches to accomodate increased demand, and then returns back to its previous level
* Scalability that the pieces are stackable by design
    * Horizontal scaling: Adding more lightweight nodes
    * Vertical scaling: Adding more computing power to your existing resources

## Shared Responsibility Model

* Customer is responsible for their data, application and data encryption, OS and Network access control
* AWS is responsible for the computing, storage, database, networking, regions, availability zones, and edge locations

## [Total Cost of Onwership Calculator](https://awstcocalculator.com/)

Generates estimated monthly cost, and a schematic of the architecture at a URL you can send someone. It also helps you compare those costs to on-premises expenses.

## Resource Tags

Key-value pairs for identifying your resources as your infrastructure grows.

* `Name` will show up in your dashboard
* Helps with tagging newly created resources
* Use information systems / hierarchy best practices when coming up with naming schemes for your app
* Search for tagged resources under `Resource Groups -> Tag Editor`
* Resource groups combine sets of tags, and can give you custom dashboards for that group
* You can track costs by resource group

## Budgets

* General admin accounts can't set budgets
* `Your name -> Billing Dashboard -> Budgets`
* Setup alerts for when different usage or cost thresholds are reached

## CLI

### Setup

From scratch:

```
sudo apt update && sudo apt install python unzip
curl https://s3.amazonaws.com/aws-cli/awscli-bundle.zip -o awscli-bundle.zip
unzip awscli-bundle.zip
sudo ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
aws configure
```

From apt:

```
sudo apt install awscli
aws configure
```

Config:

* Get access keys from the AWS console with `Your Name -> Security Credentials -> Access Keys -> Create New Access Key`
* Default region for Oregon is `us-west-2`
* Output options are `none`, `json`, `table`, and `text`
* You can setup multiple profiles with `aws configure --profile profile-name`

### General Use

* Man pages: `aws help`, `aws s3 help`, `aws iam add-user-to-group help`

## High Availability

High availability: System is up for ~100% of the time

* Achieved through redundancy, replication, failover protocols, monitoring, and load balancing

## [[EC2]]

## [[RDS]]

## [[Route 53]]

## [[S3]]

## [[IAM]]

## [[CloudWatch]]

## [[VPC]]

## [[Code Deploy]]

## [[Code Build]]

## [[Code Pipeline]]
