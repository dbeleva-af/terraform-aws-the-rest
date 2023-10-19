# Simple ec2 instance terraform module for deploying aws_instance with Amazon Machine Image 

## Prerequisites

- git
- terraform (>=1.5)
- AWS subscription
- Terraform installed localy
- AWS credentials configured to work with terraform

## Configuration

- Create `main.tf` file

```
data "aws_ami" "ubuntu" {}
resource "aws_instance" "web" {}
```

- Create `variables.tf` file
```
variable "instance_type" {}
```

- Create `outputs.tf` file
```
output "ami_id" {
  description = "The AMI ID after apply"
  value       = data.aws_ami.ubuntu.id
}

output "instance_id" {
  description = "The id after apply"
  value       = resource.aws_instance.web.id
}
```

#### Inputs

| Name  |	Description |	Type |  Default |	Required
| ----- | ----------- | ---- |  ------- | --------
| access_key | Requester AWS access key | string | - | yes
| secret_key | Requester AWS secret key | string | - | yes
| instance_type | The type for aws instance | string | t2.micro | yes
