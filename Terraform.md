# Terraform
    provider "aws" {

    region = "us-east-1"
    access_key = "xxxxxxxxxxxxxxxxxxx"
    secret_key = "xxxxxxxxxxxxxxxxxxxxxxxxxxxx"  
    }

    resource "aws_vpc" "krushnaji-vpc" {
  
     cidr_block = "172.32.0.0/16"

    }

## in terminal
terraform version

**Terraform v1.0.5**

on windows_amd64

to initialize with aws use terraform init

    terraform init

![terraform-init](https://user-images.githubusercontent.com/66898077/130344247-d177afce-f4f7-436c-ad75-2536d1d12e09.png)


.terraform folder gets created and credentials are stored in lock file

to apply the same use terraform apply and type yes

    terraform apply
    
aws_vpc.krushnaji-vpc: Creating...
aws_vpc.krushnaji-vpc: Still creating... [10s elapsed]
aws_vpc.krushnaji-vpc: Creation complete after 11s [id=vpc-076068fba606a31f0]

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

### Terraform destroy

to destroy all creation use terraform destroy
        
        terraform destroy

  Enter a value: yes

aws_vpc.krushnaji-vpc: Destroying... [id=vpc-076068fba606a31f0]
aws_vpc.krushnaji-vpc: Destruction complete after 1s

Destroy complete! Resources: 1 destroyed.
