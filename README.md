# Portfolio

### Sr. Data Engineer | Python, Scala, SQL, Spark | GCP, AWS 

Hi ! Welcome to my portfolio!
Here I will describe some of my work as a Data Engineer.
Feel free to reach me out :)  
<br />

## GCP Data Acquisition

Goal of the project was to ingest multiple source data files coming from a Google Cloud Storage bucket using this kind of routing referential:
|source_project|source_bucket|source_file_mask|destination_project|destination_bucket|destination_directory|
|----|-----|-------|----|-----|-------|
|source_bucket|raw_data|finance.*.csv|finance|raw_data||
|source_bucket|raw_data|sale.*.csv|sales|raw_data||

So, when new file of type "finance" is uploaded, I need to redirect it to the finance's project (in bucket raw_data).

To do so, I did 2 implementations for the two use cases below:

### Use Case 1 : Event-Based Ingestion

The architecture of the event-based solution is :
<img width="1220" alt="image" src="https://github.com/Bass22/portfolio/assets/29351163/2d3a9082-73c5-4dbb-be2b-aa0fd454c317">

I created a Cloud Function which is triggered by the upload of new file in Google Cloud Storage. When triggered, the Cloud function uses the routing 
referential in order to route files to their destination.
Github code is available here: [Routing Cloud Function (Event-Based)
](https://github.com/Bass22/data-acquisition-cloud-function/tree/feature/cloud_function_event_based)  

  
### Use Case 2 : Batch Ingestion

Event-based Ingestion works really well but for some of our treatments, we wanted to do them in batch mode. In other terms, instead of treating one file at a time,
we wanted to use services that will allow to group multiple source files and treat them together. The solution, I developed, consists of connecting Google Cloud 
Storage to Pub/Sub by creating notifications in Pub/Sub whenever a new file is uploaded. And, use Cloud Scheduler as a cron scheduler to launch 
a Cloud Function that will consume the messages (source files) in Pub/Sub regularly.
Github project link: [Routing Cloud Function with Pub/Sub](https://github.com/Bass22/data-acquisition-cloud-function)  

<br />
<br />
## Analytics Engineering with DBT

I worked on this migration project from legacy SQL to DBT: [Legacy SQL to DBT](https://github.com/Bass22/dbt-path-to-certification).  
![download](https://github.com/Bass22/portfolio/assets/29351163/c7765aab-93e4-4948-aba2-6dbb38482aae)

<br />
<br />
## AWS Data Transformations  

This one is the general architecture of one of the project that I was in for more than 3.5 years. The general purpose was to develop data pipelines for luxury brands using Spark Scala, Python, AWS (Lambda, Athena, S3, EMR, EC2), Spark Streaming, Kafka, Airflow, ETL (Nifi), Cassandra, Solr, Github (Github Action).

FIrst use case, when I just arrived on the project was to migrate from on-premise (Fujitsu servers) to AWS all our data pipelines. 
This reduced significantly the cost of the project and it lasted about 6 months.

<img width="1220" alt="Screenshot 2024-06-25 at 11 36 23" src="https://github.com/Bass22/portfolio/assets/29351163/aa73af5a-7984-4d5e-adbd-e4a3b4f0747c">

