### set an alias
function airflow { docker-compose run --rm airflow-cli airflow $args }

### connect to SQL Server database and query 
Invoke-SQLCmd -ServerInstance localhost -Database AdventureWorks2019 -Query "SELECT TOP 1 * FROM Person.Person"
 
### invoke a database query
Invoke-Sqlcmd -Query "SELECT * FROM dbo.Products"

### connect to a database
Invoke-Sqlcmd -ConnectionString "Data Source=ComputerName, 12345; Initial Catalog=AdventureWorks; Integrated Sceurity=true"

### disconnect from a remote computer
Exit-PSSession

### connect to a remote computer
Enter-PSSession -ComputerName $ComputerName

### check a command is installed
Get-Command -Noun *az*

### help showing all commands with 'connect'
Get-Command -Verb connect

### help showing all commands with 'get' and 'user'
Get-Command -Verb get -Noun *user*

### resolve a Domain Name System (DNS) domain name or IP address to its respective DNS record
Resolve-DnsName -Name microsoft.com

### test connection
Test-NetConnection -ComputerName 10.52.0.4 -Port 3389 -InformationLevel 'Detailed'

### check public ip address
(Invoke-WebRequest ifconfig.me/ip).Content.Trim() 

### connect to Azure
Login Az-Account

### check if a module exists
Get-Module -ListAvailable -Name 'SqlServer'

### installing a module
Install-Module SqlServer

### 



