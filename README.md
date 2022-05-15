# Terraform

This repository contains the terraform definition for the high availability deployment of AWS infrastructure. It consists of the following `.tf` files:

* `provider.tf` - defines version and configuration of terraform, S3 bucket and AWS provider
* `ec2.tf` - creates two EC2 instances in default VPC/Subnets based on latest Ubuntu 20.04 AMI
* `alb.tf` - load balancer configuration for EC2 instances
* `variables.tf` - definition of variables
* `ansible.tf` - downloads the SSH key from bucket and prepares ansible inventory file based on `inventory.tpl` template to be used further in CD pipeline

Additionally, there is a sample `terraform.tfvars` file provided which should be modified to reflect your own AWS environment configuration.

## Commands to run:

Init:
* `terraform init -backend-config=bucket=<name>-<surname>-doc-8`

Check what will be done:
* `terraform plan`

Apply configuration:
* `terraform apply -auto-approve`

Check the loadbalancer readiness:
* `watch -n 1 curl -s alb-xxxxxxxxx.us-east-1.elb.amazonaws.com`

## Destroy environment:

* `terraform destroy -auto-approve`
