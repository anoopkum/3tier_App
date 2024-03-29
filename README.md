# Terraform code to deploy three-tier Environment on azure
Problem Statement
A 3 tier environment is a common setup
One virtual network tied in three subnets.
Each subnet will have one  virtual machines scalesets.
First virtual machine -> allow inbound traffic from internet only.
Second virtual machine -> entertain traffic from first virtual machine only and can reply the same virtual machine again.
App can connect to database and database can connect to app but database cannot connect to web.

Solution
The Terraform resources will consists of following structure
 main.tf                   // The primary entrypoint for terraform resources.
vars.tf                   // It contain the declarations for variables.
output.tf                 // It contain the declarations for outputs.
terraform.tfvars          // The file to pass the terraform variables values.

For the solution, we have created and used five modules:

resourcegroup - creating resourcegroup
networking - creating azure virtual network and required subnets
securitygroup - creating network security group, setting desired security rules and associating them to subnets
compute - creating availability sets, network interfaces and virtual machines
database - creating database server and database
All the stacks are placed in the modules folder and the variable are stored under terraform.tfvars
To run the code, need to append the variables in the terraform.tfvars
Each module consists minimum two files: main.tf, vars.tf
resourcegroup and networking modules consists of one extra file named output.tf

Deployment
Steps  
Step 0 terraform init
Step 1 terraform plan
Step 2 terraform validate
Step 3 terraform apply
