day5_terraform_documentation: |
  # Day 5 – Terraform Infrastructure as Code

  This document explains the fundamentals of Terraform and demonstrates how infrastructure can be provisioned automatically using Infrastructure as Code (IaC). The session focuses on understanding Terraform workflow, providers, resources, variables, and execution lifecycle.

  ---

  ## 📘 Introduction

  Terraform is an Infrastructure as Code (IaC) tool used to define, provision, and manage infrastructure using declarative configuration files.

  Instead of manually creating servers or services, Terraform allows infrastructure to be written as code and deployed consistently across environments.

  Terraform works by:

  - Reading configuration files
  - Creating an execution plan
  - Applying changes to infrastructure
  - Maintaining state of resources

  ---

  ## 🏗 Core Concepts

  ### 1️⃣ Provider  
  Defines the platform where infrastructure is created (AWS, Azure, GCP, etc.).

  ### 2️⃣ Resource  
  Represents infrastructure components such as virtual machines, networks, or storage.

  ### 3️⃣ State  
  Terraform maintains a state file to track created resources.

  ### 4️⃣ Variables  
  Used to make configurations reusable and dynamic.

  ### 5️⃣ Execution Plan  
  Shows what Terraform will create, update, or destroy before applying.

  ---

  ## ⚙️ Environment Used

  - Ubuntu (Terraform Control Machine)
  - Cloud Provider account (or local provider)
  - VS Code / Terminal
  - Internet connection

  ---

  ## 📦 Installing Terraform

  Update packages:

  sudo apt update

  Install Terraform:

  sudo apt install terraform -y

  Verify installation:

  terraform --version

  ---

  ## 📁 Project Structure

  terraform-project/
   ├── main.tf
   ├── variables.tf
   └── outputs.tf

  ---

  ## 📝 main.tf

  Defines provider and resources.

  Example:

  provider "aws" {
    region = "us-east-1"
  }

  resource "aws_instance" "demo" {
    ami           = "ami-0abcdef1234567890"
    instance_type = "t2.micro"

    tags = {
      Name = "Terraform-Instance"
    }
  }

  ---

  ## 📝 variables.tf

  variable "instance_type" {
    default = "t2.micro"
  }

  ---

  ## 📝 outputs.tf

  output "instance_ip" {
    value = aws_instance.demo.public_ip
  }

  ---

  ## ⚡ Terraform Workflow

  Terraform always follows this lifecycle:

  Step 1 – Initialize Project  
  terraform init  
  Downloads required providers and prepares environment.

  Step 2 – Validate Configuration  
  terraform validate  
  Checks syntax and configuration correctness.

  Step 3 – Preview Changes  
  terraform plan  
  Shows what resources will be created or modified.

  Step 4 – Apply Infrastructure  
  terraform apply  
  Creates resources automatically.  
  Type yes when prompted.

  Step 5 – Destroy Infrastructure  
  terraform destroy  
  Removes all created resources.

  ---

  ## 🧠 Key Concepts Learned

  1️⃣ Infrastructure as Code  
  Infrastructure is managed through version-controlled files.

  2️⃣ Declarative Approach  
  Describe desired state — Terraform handles execution.

  3️⃣ State Management  
  Terraform tracks infrastructure using state files.

  4️⃣ Automation  
  Manual cloud setup is replaced with automated provisioning.

  5️⃣ Reusability  
  Same configuration can be reused across environments.

  ---

  ## 🔄 Typical Terraform Flow

  Write Code → terraform init → terraform plan → terraform apply

  To clean up:

  terraform destroy

  ---

  ## ✅ Outcome

  By the end of Day 5:

  - Installed Terraform
  - Created Terraform configuration files
  - Understood providers and resources
  - Executed terraform init, plan, apply, destroy
  - Learned Infrastructure as Code principles
  - Automated infrastructure provisioning

  This session demonstrated how Terraform enables consistent, repeatable, and scalable infrastructure deployment.
