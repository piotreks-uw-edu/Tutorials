### The airflow standalone command initializes the database, creates a user, and starts all components.
airflow standalone

### If you want to run the individual parts of Airflow manually rather than using the all-in-one standalone command, you can instead run:
airflow db migrate

airflow users create \
    --username admin \
    --firstname Peter \
    --lastname Parker \
    --role Admin \
    --email spiderman@superhero.org

airflow webserver --port 8080

airflow scheduler

### optional, start a web server in debug mode in the background
 airflow webserver --debug &


### test tasks (dag_id - task_id - date_in_the_past)
airflow tasks test forex_data_pipeline is_forex_rates_available 2021-01-01