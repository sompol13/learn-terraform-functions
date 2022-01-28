## Perform Dynamic Operations with Functions
In this tutorial, you create an EC2 instance running a pre-built webapp. You will:
* use the `templatefile` function to create a `user_data` script to dynamically configure an EC2 instance with resource information from your configuration.
* use the `lookup` function to pass a map output to a variable as an input.
* use the `concat` function to concatenate and output multiple lists of rules to an AWS Security Group.

### Reference
https://learn.hashicorp.com/tutorials/terraform/functions