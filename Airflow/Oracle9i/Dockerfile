# Image: Apache Airflow
FROM apache/airflow:3.0.3

USER root

RUN apt-get update && apt-get install -y \
    alien \
    libaio1 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

ADD oracle-instantclient11.2-basic-11.2.0.4.0-1.x86_64.rpm oracle-instantclient11.2-basic-11.2.0.4.0-1.x86_64.rpm
RUN alien --to-deb -i oracle-instantclient11.2-basic-11.2.0.4.0-1.x86_64.rpm
ADD oracle-instantclient11.2-sqlplus-11.2.0.4.0-1.x86_64.rpm oracle-instantclient11.2-sqlplus-11.2.0.4.0-1.x86_64.rpm
RUN alien --to-deb -i oracle-instantclient11.2-sqlplus-11.2.0.4.0-1.x86_64.rpm

COPY tnsnames.ora /usr/lib/oracle/11.2/client64/network/admin/tnsnames.ora
ENV TNS_ADMIN=/usr/lib/oracle/11.2/client64/network/admin/
ENV PATH="/usr/lib/oracle/11.2/client64/bin:$PATH"
ENV LD_LIBRARY_PATH="/usr/lib/oracle/11.2/client64/lib"

# Change to airflow user for subsequent commands
USER airflow