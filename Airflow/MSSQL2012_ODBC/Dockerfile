# Image: Apache Airflow
FROM apache/airflow:3.0.3

USER root

# MSSQL
RUN apt-get update && apt-get install -y \
    freetds-dev \
    freetds-bin \
    unixodbc-dev \
    tdsodbc \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# Change to airflow user for subsequent commands
USER airflow