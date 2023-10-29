# create a custom RBAC role #
## json az104-02a-customRoleDefinition.json
{
  "Name": "Support Request Contributor (Custom)",
  "IsCustom": true,
  "Description": "Allows to create support requests",
  "Actions": [
      "Microsoft.Resources/subscriptions/resourceGroups/read",
      "Microsoft.Support/*"
  ],
  "NotActions": [
  ],
  "AssignableScopes": [
      "/providers/Microsoft.Management/managementGroups/az104-02-mg33266155",
      "/subscriptions/SUBSCRIPTION_ID"
  ]
}
## command
New-AzRoleDefinition -InputFile $HOME/az104-02a-customRoleDefinition.json