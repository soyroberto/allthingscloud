---
title: "How to Create Random Passwords Using Terraform"
seoTitle: "terraform password generator"
seoDescription: "a quick module to generate a random password"
datePublished: Fri Dec 13 2024 04:14:48 GMT+0000 (Coordinated Universal Time)
cuid: cm4m8iciz000109k2guv4h2e4
slug: how-to-create-random-passwords-using-terraform
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/FnA5pAzqhMM/upload/aa921677485d5914330e3abaff67b80f.jpeg
tags: cloud-computing, automation, terraform

---

When creating VMs, it's common to use a username and password to connect to them. While using SSH keys is definitely better for Linux machines, the other day I needed to set a password for an Ubuntu VM

I checked out the Terraform function for creating random strings:

# [**random\_password (Resource)**](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/password)

Then I wrote the code below which later re-use in the VM creation module

```go
variable "length" {
  description = "The length input from the user"
  type        = number
  default     = 18
}
resource "random_password" "password" {
  length           = var.length
  special          = true
  override_special = "!#$%&*()-_=+[]{}<>:?"

   keepers = {
    # this will recreate the password if the timestamp changes: meaning every running will generate a new password
    timestamp = "${timestamp()}"
  }
}

output "espassword" {
  value     = random_password.password.result
  sensitive = true
}

/*  Create a random password with the following requirements:
  - Length: 18 default value
  to change the length, use the following command
  export TF_VAR_length=20 in the shell changing the lenght will regenerate the password
   
   Can also be done using the following command: terraform apply -var 'length=20' -auto-approve
  - Special characters: !#$%&*()-_=+[]{}<>:?
  - Output the password as a sensitive output
  to show the password in the Terraform output
  terraform output espassword
  to regenerate the password
    terraform taint random_password.password
    terraform apply
    terraform output espassword
*/
```

To execute this code:

1. **terraform init**
    
2. **terraform plan** (optional)
    
3. **terraform apply**
    
4. **terraform output *espassword*.** This will show the password string in the console
    
5. Easier to execute all in 1 liner: **terraform apply -auto-approve;terraform output espassword**
    
6. Also, it's possible to create passwords of different length which can be specified at runtime, ***ex***: **terraform apply -var 'length=22' -auto-approve;terraform output espassword**
    

Once that done the password will be show in the console, ex:

"**w$5(sLht)N&gt;!{IjQ7r**" **Note**: Quotes are not meant to be part of the password

| **The password repo** | [https://github.com/soyroberto/terraform-library/blob/main/101/passwordgenerator/main.tf](https://github.com/soyroberto/terraform-library/blob/main/101/passwordgenerator/main.tf) |
| --- | --- |

## Roberto