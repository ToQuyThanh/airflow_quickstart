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

**If creating from scratch, refer to the instructions from the airflow homepage**
