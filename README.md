# JMeter Terraform

This repo will help you to spin up an AWS EC2 instance with Java, JMeter, and JMeter Plugins installed.

## Prerequisites

* Terraform
* AWS Console w/ IAM role

## Setup

### AWS Key Pair

* Log into AWS console
* Navigate to EC2 -> Key Pairs
* Create a new key pair w/ RSA and Private Key format (PEM)
* Save the private key to a file in a secure location

## Usage

```terraform
module "jmeter" {
  source  = "github.com/giulianisanches/terraform-aws-jmeter"
  aws_instance_type = "t2.small"
  aws_key_name      = "terraform"
  jmeter_version    = "5.4.3"
  subnet_id         = "subnet-id-here-0df8d7f80asf7"
}
```

By default, we use the latest Amazon Linux AMI. You can pass an custom one with `aws_ami` parameter.

You can also pass a `subnet_id` to set the network where the instance will be created.

To configure other input variables, refer to the [documentation](https://registry.terraform.io/modules/QAInsights/jmeter/aws/latest?tab=inputs#optional-inputs).

To configure [outputs](outputs.tf), refer to the [documentation](https://registry.terraform.io/modules/QAInsights/jmeter/aws/latest?tab=outputs).

## Terraform Plan and Apply

* Run `terraform init` (or `terraform init --upgrade` to upgrade to the latest version of this module)
* Run `terraform plan`
* Run `terraform apply` when prompted to continue, enter `yes` to spin up the instance

## JMeter validation

ssh into the instance using the PEM and run `jmeter -v` to verify JMeter is installed and working.

## Reference

* [Terraform](https://www.terraform.io/)
* [AWS](https://aws.amazon.com/)
* [JMeter](https://jmeter.apache.org/)
