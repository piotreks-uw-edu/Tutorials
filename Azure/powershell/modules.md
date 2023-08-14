# list all modules that have been installed                                       
Get-Module -ListAvailable

# install Azure module and overrride any existing command
Install-Module -Name Az -Force -AllowClobber

# remove Module
Uninstall-Module AzureRM -AllVersions