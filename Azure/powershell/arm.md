# deploys an Azure Resource Manager template
New-AzResourceGroupDeployment `
  -ResourceGroupName az104-10-rg0-lod32955258 `
  -TemplateFile $HOME/az104-10-vms-edge-template.json `
  -TemplateParameterFile $HOME/az104-10-vms-edge-parameters.json `
  -AsJob
