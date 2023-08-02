# get details about the Azure subscriptions available in your account
Get-AzSubscription

# list all modules that have been installed                                       
Get-Module -ListAvailable

# get Active Directory users
Get-AzADUser

# install Azure module and overrride any existing command
Install-Module -Name Az -Force -AllowClobber