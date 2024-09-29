Here’s a README file based on your provided Terraform configuration:

---

# Terraform AWS EC2 Infrastructure as Code (IaC) Example

This project provides a basic example of provisioning an AWS EC2 instance using Terraform. It utilizes AWS as the cloud provider and allows for the configuration of instance details through variables defined in the `variable.tf` file.

## Prerequisites

To run this Terraform code, you will need the following:
- An AWS account
- AWS credentials configured (via `~/.aws/credentials` or environment variables)
- Terraform installed (version 0.12 or higher)

## Overview

This Terraform configuration deploys an EC2 instance on AWS with customizable options such as instance type, AMI ID, subnet, and key pair. The EC2 instance module is sourced from a relative path (`../../modules/ec2`).

### Main Components
1. **Provider**: AWS is the provider for this configuration, and the region is set to `us-west-2`.
2. **EC2 Module**: This module manages the deployment of an EC2 instance, with customizable options like instance name, AMI ID, instance type, key pair, and subnets.
3. **Variables**: Variables such as `instance_name`, `ami_id`, `instance_type`, `key_name`, and `subnet_ids` can be customized. Default values are provided in the `variable.tf` file.

## File Structure

- `main.tf`: Defines the AWS provider and uses the EC2 instance module with specified variables.
- `variable.tf`: Contains the input variables for customizing the EC2 instance.

## Configuration Options

You can configure the following parameters through the `variable.tf` file:

- **instance_name**: The name of the EC2 instance. Default is `test-instance`.
- **ami_id**: The AMI ID to use for the instance. Default is `ami-0735c191cf914754d`.
- **instance_type**: The EC2 instance type. Default is `t2.small`.
- **key_name**: The key pair name to associate with the instance. Default is `ansaf-instance`.
- **security_group_ids**: List of security groups to attach to the instance. Default is `["sg-01ce819e8d65269f0"]`.
- **instance_count**: The number of EC2 instances to create. Default is 1.
- **subnet_ids**: List of subnet IDs where the instance will be deployed. Default is `["subnet-058a7514ba8adbb07", "subnet-0dbcd1ac168414927", "subnet-032f5077729435858"]`.

## Usage

### Step 1: Initialize Terraform
Before running any commands, make sure to initialize Terraform within the project directory to download any required providers and modules:
```bash
terraform init
```

### Step 2: Plan the Infrastructure
To see a preview of the resources that will be created by Terraform, run:
```bash
terraform plan
```

### Step 3: Apply the Configuration
To apply the configuration and create the resources on AWS, use the following command:
```bash
terraform apply
```
You will be prompted to confirm the creation of resources. Type `yes` to proceed.

### Step 4: Destroy the Infrastructure (optional)
If you need to tear down the infrastructure and remove the created resources, run:
```bash
terraform destroy
```

## Notes

- Ensure that the key pair (`key_name`) specified exists in your AWS account.
- Modify the AMI ID (`ami_id`) according to the region or operating system you need.
- You may need to update the security group (`security_group_ids`) and subnet IDs (`subnet_ids`) as per your AWS setup.

---

This README should help users get started with the Terraform project and configure their AWS EC2 infrastructure accordingly.