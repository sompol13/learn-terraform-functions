## Perform Dynamic Operations with Functions
In this tutorial, you create an EC2 instance running a pre-built webapp. You will:
* use the `templatefile` function to create a `user_data` script to dynamically configure an EC2 instance with resource information from your configuration.
* use the `lookup` function to pass a map output to a variable as an input.
* use the `concat` function to concatenate and output multiple lists of rules to an AWS Security Group.

### Add the `templatefile` function
- Open the `variables.tf` file in your editor to find the variables associated you will assign to the `name` and `department` keys in your template file.
- Add the `user_data` attribute to the `aws_instance` resource block.

### Initialize and apply the Terraform configuration
- `terraform init`
- `terraform apply`

### Map regions to AMIs with `lookup`
You will use the `lookup` function to dynamically apply the region-appropriate AMI ID for the EC2 instance.
- Open `variables.tf` file. Copy and append the `aws_amis` map variable block below to your `variables.tf` file.
- In your `aws_instance` resource, change the `ami` attribute to your lookup function.
- Copy and append the `ami_value` output block below to your `outputs.tf` file. This is to verify the lookup function works as expected.

### Edit your region variable and observe the changes
- Run `terraform apply` with a command-line variable flag changing the region to `us-east-2`.
- Destroy your infrastructure `terraform destroy -var "aws_region=us-east-2"`

### Use the `concat` function to output lists of security groups
- Create an SSH key and a security group resource.
- In `main.tf`, add a new `aws_security_group` resource. Copy and append the resource block below to your `main.tf` file.
- Create a new `aws_key_pair` resource to add your newly created SSH key to the instance. 
- Edit your `aws_instance` `web` resource to allow this security group and the ssh key.

### Add the list of Security Groups to your outputs
- Open the `outputs.tf` file. The vpc_security_group_ids attribute in your aws_instance resource.
- terraform apply
> `ssh ubuntu@$(terraform output -raw web_public_ip) -i ssh_key`

> Note: It may take up to five minutes for your instance to be fully built and configured. If you receive a public key error message, wait a couple minutes before trying again.

### Reference
https://learn.hashicorp.com/tutorials/terraform/functions