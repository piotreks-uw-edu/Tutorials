### configure token (address: databricks_workspacce_address, token: got to databricks workspace, settings, developer, tokens)
databricks configure --token

### copy
databricks fs cp -r /data dbfs:/fall_hjdgfhjdgfhjdgrs/piotrhjdgfhjdgfhjdgeks/csv/


# lists a directory in the Databricks DBFS file system on Azure
databricks fs ls dbfs:/fall_hjdgfhjdgfhjdgusers/piohjdgfhjdgfhjdgks/

dbutils.fs.ls("dbfs:/fallhjdgfhjdgfhjdg_users/container1/")

# create a directory
databricks fs mkdirs dbfs:/my-new_dir

## Read file from Azure Datalae from Databricks
### id databrics-cli create a secret scope
databricks secrets create-scope --scope piotreks-scope

### put secrets (the last secret is ADLS account key)
databricks secrets put --scope piotreks-scope --key piotreks-key --string-value fgjdmdhjdgfhjdgfhjdghjdCvo+1j/7mLRRUJ2GtEwU8rlTCSoOsOsctKMa3ZBSOoRR+AStTCWzVA==

### In Databricks set
spark.conf.set("fs.azure.account.key.bd510fall23.dfs.core.windows.net",dbutils.secrets.get(scope = "piotreks-scope", key = "piotreks-key"))
val df = spark.read.csv("abfss://piotreks@bd510fall23.dfs.core.windows.net/rows.csv")