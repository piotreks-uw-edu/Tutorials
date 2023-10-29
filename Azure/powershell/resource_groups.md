# create resource groups
New-AzResourceGroup -Name "az104-10-rg0-lod32955258" -Location "North Europe"

# clear reseource groups
Get-AzResourceGroup -Name 'az104-05*' | Remove-AzResourceGroup -Force -AsJob

# List all assets in a resource group
Get-AzResource -ResourceGroupName "az104-10-rg0-lod32955258"
