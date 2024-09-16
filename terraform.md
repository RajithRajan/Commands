# apply
Apply the terraform scripts
```
terraform apply
terraform apply -input=false -var-file=dev.tfvars -auto-approve
```

# fmt
Format the terraform code
```
terraform fmt
```

# import
Import the existing resrouces in terraform state to manage it using terraform
```
terraform import <terraform_resrouce_name> <id>
```
# init
Initialize the state file and download the providers and modules the script user
```
terraform init
terraform init -input=false --backend-config=dev.conf
```

# plan
Verifies the current infrastructure with the script to calculate how to make change to make it match
```
terraform plan
```

# validate
To validate the terraform for any syntax errors
```
terraform validate
```

# workspace
A way to organize the state file for the terraform for different environments. ${terraform.workspace} can we used to get the current workspace name in the code
```
terraform.tfstate.d
|
. ->  dev
    |___ terraform.tfstate
    |___ terraform.tfstate.backup
|
. ->  test
    |___ terraform.tfstate
    |___ terraform.tfstate.backup
```
## delete
delete a workspace
```
terraform workspace delete <name>
```

## list
List all the workspace
```
terraform workspace list
```

## new
Create a new workspace
```
terraform workspace new test
```

## select
To switch to a terraform workspace
```
terraform workspace select test
```

## show
Display the active workspace
```
terraform workspace show
```

