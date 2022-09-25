# A_Startup_Data-_Warehouse-
# Data Warehouse
in this project we are  creating a Data warehouse as a startup by using a dataset taken from Drone.
The Data Warehouse architectures we learnt and build a Data Warehouse on AWS cloud. We build an ETL pipeline to extract and transform data stored in json format in s3 buckets and move the data to Warehouse hosted on Amazon Redshift.
# Steps followed to create a Data warhouse and tools used
the following steps used to develope a our data warhouse 
# How to run?
This repo contains a runnable demo using containerized Airflow, which is a convenient option to run everything in a Docker container.
  - This will start up the Airflow scheduler, webserver, and a Postgres database 
  - Once the webserver is up (takes about 30 seconds), you can access the Airflow web UI at localhost:8080
  - You can run a data wareouhse  stop to stop the container again
  - You can also run the DAG in this repo with a standard Airflow installation if you want. 
  - You'll have to install the relevant dependencies (Airflow, dbt, Great Expectations, the respective operators, etc) and 
   - probably handle some more configurations to get it to work.
# Development
In order to develop the dbt DAG  locally instead of in the containers (for faster dev loops),  a new virtual environment created and installed relevant packages wit pip install -r requirements.txt

- dbt setup: run dbt init dbt to create the dbt directory in this repo
- copied ~/.dbt/profiles.yml into the root of this project and added the a startup data warahouse postgres creds to have a database available 
- -- you wouldn't use this database in production or keep the file in the repo, this is just a shortcut for this demo!!
- The profiles.yml target setup allows  to run the dbt pipeline both locally and within the container:
- Container:connect to shell within the scheduler container
           -  run cd dbt
           -  run dbt run --profiles-dir /usr/local/airflow --target a startup data warehouse
 - Local:
           -  run cd dbt
           -  run dbt run --profiles-dir /Users/sam/code/dag-stack --target local_dev

# Airflow DAG setup
   - The setup is done by using the custom dbt and Airflow operators, in addation to that Python and bash operators also used
   
