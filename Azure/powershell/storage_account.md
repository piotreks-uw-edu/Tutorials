# return a list of storage accounts in the specified resource group
Get-AzStorageAccount -ResourceGroupName "az104-10-rg0-lod32955258"

# create storage accounts
New-AzStorageAccount -ResourceGroupName "az104-10-rg0-lod32955258" -Name "cloudshell32955258" -Location "North Europe" -SkuName "Standard_LRS" -Kind "StorageV2"

# get the resource ID of a specific storage account
$storageAccount = Get-AzStorageAccount -ResourceGroupName "az104-10-rg0-lod32955258" -Name "cloudshell32955258"
$storageAccount.Id

