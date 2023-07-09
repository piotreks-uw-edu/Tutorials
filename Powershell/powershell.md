# invoke a database query
Invoke-Sqlcmd -Query "SELECT * FROM dbo.Products"

# connect to a database
Invoke-Sqlcmd -ConnectionString "Data Source=ComputerName, 12345; Initial Catalog=AdventureWorks; Integrated Sceurity=true"

# disconnect from a remote computer
Exit-PSSession

# connect to a remote computer
Enter-PSSession -ComputerName $ComputerName

# check a command is installed
Get-Command -Noun *az*

# install Azure module and overrride any existing command
Install-Module -Name Az -Force -AllowClobber

# help showing all commands with 'connect'
Get-Command -Verb connect

# connect to an Azure account
Connect-AzAccount

# help showing all commands with 'get' and 'user'
Get-Command -Verb get -Noun *user*

# get Active Directory users
Get-AzADUser

