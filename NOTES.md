# Terraform Notes 📘

These are my hands-on notes while practicing Terraform for SRE/Cloud/DevOps roles.  
It includes interview Q&A and simple examples I’ve actually tried in AWS.

---

## 🟢 Basic Terraform Interview Q&A

**Q1: What is Terraform?**  
Terraform is an Infrastructure as Code (IaC) tool that lets you define, provision, and manage cloud resources in a repeatable and automated way.

**Q2: What is a Terraform state file?**  
The state file (`terraform.tfstate`) keeps track of the resources Terraform manages.  
Without it, Terraform won’t know what exists and may recreate resources unnecessarily.

**Q3: What are some common Terraform commands?**  
- `terraform init` → Initialize a project and download providers  
- `terraform plan` → Show execution plan (what will change)  
- `terraform apply` → Apply the changes to create/update infra  
- `terraform destroy` → Tear down the infrastructure  

**Q4: What are variables and outputs in Terraform?**  
- Variables make configurations reusable and dynamic.  
- Outputs display useful information after resources are created (like public IP, bucket name, etc.).  

---

## 🟡 Example 1: EC2 Instance

Provisioning an EC2 instance in AWS:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "my_ec2" {
  ami           = "ami-0c02fb55956c7d316"
  instance_type = var.instance_type

  tags = {
    Name = "Aman-Terraform-EC2"
  }
}
````

👉 Launches a basic EC2 instance with tags.
👉 Uses variables for instance type.

---

## 🟡 Example 2: S3 Bucket

Provisioning a simple S3 bucket:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "my_bucket" {
  bucket = "aman-terraform-demo-bucket"
  acl    = "private"

  tags = {
    Name        = "Aman S3 Demo"
    Environment = "Dev"
  }
}
```

👉 Creates a private S3 bucket with tags.
👉 Bucket names must be globally unique across AWS.

---

## 🔜 Next Steps in My Learning

* Add **VPC example**
* Experiment with **Terraform remote state (S3 backend)**
* Explore **Terraform modules** for reusable code
* Deploy a **multi-tier application infra** using Terraform

---

### ⚡ Disclaimer

All `.tfvars` or sensitive details are excluded.
This repo is for **learning and demonstration only**.

```

---
