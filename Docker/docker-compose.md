### run docker compose with build
docker-compose up --build

### start a container
docker-compose run airflow-cli airflow

### restart one service (preserves state)
docker-compose restart docker-compose restart staging_srv

### stop the container
docker-compose stop staging_srv

### remove the container
docker-compose rm staging_srv
 

