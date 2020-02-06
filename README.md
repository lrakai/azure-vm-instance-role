# azure-vm-instance-role

Example ARM template showing how to assign a role to an Azure VM. This simulates how roles are assigned to EC2 instances in AWS. Azure uses the concept of managed identities (previously "managed system identities") to execute the feat.

## Deploy

- PowerShell

    ```ps1
    $resourceGroupName = "qa-lab"
    New-AzureRmResourceGroup -Name $resourceGroupName -Location "eastus"
    New-AzureRmResourceGroupDeployment -ResourceGroupName $resourceGroupName -Name vmrole -TemplateFile .\azure-deploy.json
    ```

- Bash

    ```sh
    resourceGroupName="qa-lab"
    az group create --name $resourceGroupName --location "eastus"
    az group deployment create --resource-group $resourceGroupName --name vmrole --template-file ./azure-deploy.json
    ```

## Destroy

- PowerShell

    ```ps1
    Remove-AzureRmResourceGroup -Name $resourceGroupName -Force
    ```

- Bash

    ```sh
    az group delete --name $resourceGroupName --yes
    ```


## References

- Also a quickstart template [here](https://github.com/Azure/azure-quickstart-templates/tree/master/201-vm-msi).