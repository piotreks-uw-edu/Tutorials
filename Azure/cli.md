### installing the Azure Command-Line Interface on your Azure VM
 - First check to see if the Azure CLI is installed by running:
apt list --installed | grep azure | grep cli

curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
 - Once the installation is complete you can veryif the CLI tools are present by running:
az --help

### prints all system information #
uname -a