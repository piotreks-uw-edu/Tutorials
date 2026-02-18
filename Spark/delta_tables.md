### Delete data
delta_table.delete("cs_solde_date_sk = 24051")

### show a Delta table's history
delta_table.history().display()

### obtain detailed metadata information about the specified Delta table.
describe detail delta.`abfss://examples@bd510fall22.dfs.core.windows.net/module_four/dir/catalog_sales_delta`

### delete any Parquet files and directories that are not needed by the table for maintaining older versions up to the retention threshold, the argument is in hours
catalog_sales_vacuum.vacuum(0)

### usage of time travel
time_travel_df = (spark.read
                  .format("delta")
                  # This also works with timestampAsOf
                  .option("versionAsOf", 0)
                  .load(f"abfss://examples@bd510fall22.dfs.core.windows.net/module_four/{current_user}/catalog_sales_delta"))

### update in delta tables
(customer_delta
 .update(condition = "c_preferred_cust_flag = 'Y'", 
         set = { "c_preferred_cust_flag": "true" })
)

### merge 
(customer_delta.alias("customer_target")
 .merge(
   #### Merge in the the new data
  source_customer_dataframe.alias("customer_source"),
   ##### Key on which to match
  "customer_target.c_customer_sk = customer_source.c_customer_sk")
 ##### If the keys match 
 .whenMatchedUpdate(set = { "c_first_name" : "customer_source.c_first_name" } )
 ##### Insert all records that don't match on an existing key. You can selectively add columns as well.
 .whenNotMatchedInsertAll()
 .execute()
)
