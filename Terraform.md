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


![terraform-init](https://user-images.githubusercontent.com/66898077/130344247-d177afce-f4f7-436c-ad75-2536d1d12e09.png)




