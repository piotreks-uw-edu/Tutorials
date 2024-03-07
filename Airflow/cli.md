### set an alias to run a container commands (I set it in wsl)
echo "alias airflow='docker-compose run --rm airflow-cli airflow'" >> ~/.bashrc

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

### check successfull parsing
python ./dags/tutorial.py

### test tasks (dag_id - task_id - date_in_the_past)
airflow tasks test tutorial sleep 2015-06-01

### test the whole dag
airflow dags test tutorial 2015-06-01

### initialize the database tables
airflow db migrate

### print the list of active DAGs
airflow dags list

### prints the list of tasks in the "tutorial" DAG
airflow tasks list tutorial

### prints the hierarchy of tasks in the "tutorial" DAG
airflow tasks list tutorial --tree

### testing one task (print_date here)
airflow tasks test tutorial print_date 2015-06-01

### start your backfill on a date range
airflow dags backfill tutorial \
    --start-date 2015-06-01 \
    --end-date 2015-06-07

### add connection to mssql
airflow connections add 'mssql_server' \
    --conn-type 'mssql' \
    --conn-host 'your_host' \
    --conn-login 'your_login' \
    --conn-password 'your_password' \
    --conn-schema 'your_database' \
    --conn-port 1433
