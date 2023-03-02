# Terraform

Builds a Postgress Database cluster and separate one for App Deployment. Could be easily configured with modifying the [vars.tf](vars.tf) file.

To build everything use either env.bat or env.sh depending on your OS to set sensible data (actually you have to remove this scripts and manage your secrets better, but it is great for a quickstart or demonstration). Than use:

- `terraform init`

- `terraform apply`


---
To get ingress_floating_ip manually (for following automation) use

- `terraform output -raw ingress_floating_ip`
