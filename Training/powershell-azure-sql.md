### check if a module exists
Get-Module -ListAvailable -Name SqlServer

### installing a module
Install-Module SqlServer

### Prompt for credentials
$credential = Get-Credential

### Use the credentials with Invoke-Sqlcmd
Invoke-Sqlcmd -ServerInstance 'watsettlement.database.windows.net' `
              -Database 'settlement' `
              -Username $credential.UserName `
              -Password $credential.GetNetworkCredential().Password `
              -Query 'SELECT * FROM dbo.WorkDay' | 
			  Format-Table -AutoSize

### select all views in the database
SELECT * FROM INFORMATION_SCHEMA.VIEWS;

### see table' schema
SELECT * FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = 'Workday'