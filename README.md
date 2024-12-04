# airflow_quickstart

This guide helps you set up a basic environment to run Apache Airflow using Docker.

***

1. Create the required directories

Apache Airflow requires the following directories to store its related files: dags, logs, plugins, and config. Run the command below to create these directories:

```
mkdir -p ./dags ./logs ./plugins ./config
```


2. Configure environment variables

Apache Airflow uses environment variables for configuration. The AIRFLOW_UID variable ensures proper file permissions for the Docker container.

Run the following command to create a .env file with the required AIRFLOW_UID value:
```
echo -e "AIRFLOW_UID=$(id -u)" > .env
```

For other operating systems, you may get a warning that AIRFLOW_UID is not set, but you can safely ignore it. You can also manually create an .env file in the same folder as docker-compose.yaml with this content to get rid of the warning:

```
AIRFLOW_UID=50000
```

3. Build image
```
docker-compose build
```

4. Initialize the database

On all operating systems, you need to run database migrations and create the first user account. To do this, run the following command:

```
docker-compose -f docker-compose.yaml up airflow-init -d
```


5. Start Airflow using Docker Compose

Customize the `docker-compose.yaml` file to select your preferred database and Redis configuration. Afterward, run the following command to start Airflow and all associated services:

```
docker-compose -f docker-compose.yaml up -d
```

6. Cleaning up

To stop and delete the containers, remove volumes with database data, and delete downloaded images, run the following command:

```
docker-compose down --volumes --rmi all
```

***

([Airflow docker compose](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html))
