# cbs-deploy-terraform


Terraform examples for deploying Pure Cloud Block Store (CBS) with all the associated pre-requisites

_Note: This repo only supports deploying Cloud Block Store in Azure_

# How to Use

1. Deploy an Azure VM in the same subscription where you are planning to deploy CBS.
2. SSH to the VM, then install Terraform.
3. Authenticate to Azure.
4. Clone this repo.
5. Navigate to the desired example, and edit `terraform.tfvars` with your own parameters and input. ( `terraform.tfvars` file has a basic example on the required input required for the deployment )
6. Run `terraform init`, then `terraform apply`

#\_\_\_

# How it is Built

The content of this repo is mostly Azure and CBS Terraform Provider Code. It is split into:

1. Example dir: `Depoly-*` where you would need to navigate and excite the terraform commands.

   | Example Name                  | Cloud Provider | Modules Used                              |
   | ----------------------------- | -------------- | ----------------------------------------- |
   | [Deploy-CBS-Prerequisites-Only](/Deploy-CBS-Prerequisites-Only) | Azure          | CBS-VNET,CBS-NAT-GW, VM-JUMPBOX           |
   | [Deploy-CBS-Array-with-all-Prerequisites](/Deploy-CBS-Greenfield)         | Azure          | CBS-Array,CBS-VNET,CBS-NAT-GW, VM-JUMPBOX |


2. Modules files:
   | Module Name | |
   | ----------- | --- |
   | [CBS-VNET](/Modules/CBS-VNet) | Creates an Azure VNet with four Subnet |
   | [CBS-NAT-GW](/Modules/CBS-NAT-GW) | Creates an Azure NAT GW and associate it with CBS System Subnet |
   | [CBS-Key-Vault](/Modules/CBS-Key-Vault) | Creates an Azure KeyValut that is used by CBS Terraform Provider to perform management operations |
   | [CBS-Identity](/Modules/CBS-Identity) | Creates an Azure Custom Role and Assign it to a User Managed Identity |
   | [VM-JUMPBOX](/Modules/VM-JUMPBOX) | Creates an Azure VM on the same CBS VNet, it can be used as a Jump Host or repurpose as an storage initiator|
   | [CBS-Array](/Modules/CBS-Array) | Creates a Cloud Block Store Array |
   | [CBS-VNET-Peering](/Modules/CBS-VNet-Peering) | Creates a peering link between the Terraform VM to the new created CBS VNET | 

