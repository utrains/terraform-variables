# Terraform variables

- You can use input variables to customize your Terraform configuration with
values that can be assigned by end users of your configuration. 
- Input variables allow users to re-use and customize configuration by providing a consistent
interface to change how a given configuration behaves.

### Goal : In this tutorial, you're going to use some custom variables type like : List, Map, String, ...

- The configuration in __main.tf__ defines a web application, __including a VPC__, __load balancer__, and __EC2 instances__.

1. initialize and apply the configuration
```
terraform init
terraform apply -auto-approve
```
### String variable : 

### Example 1 : 
1. In the __variables.tf__ file, create variable __aws_region__ with default value __"us-west-2"__
2. In the main.tf file change the provider block (line 2) and assign this created variable.

### Example 1 : Solution
1. string variable

```
variable "aws_region" {
  description = "AWS region"
  type        = string
  default     = "us-west-2"
}
```
2. String variable assign to provider block
```
provider "aws" {
  # region  = "us-west-2"  ==> ligne that we change
  region  = var.aws_region
}
```
Note: you can save your changes and make terraform apply to see if all works fine

### Example 2 : 