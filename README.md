# Portfolio

### Sr. Data Engineer | Python, Scala, SQL, Spark | GCP, AWS 

Hi ! Welcome to my portfolio!
Here I will describe some of my work as a Data Engineer.
Feel free to reach me out :) 


## GCP Data Ingestion

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
Github code is available here: (Please ask me the authorization to see the code!)

### Use Case 2 : Batch Ingestion

Event-based Ingestion works really well but for some of our treatments, we wanted to do them batch mode. In other terms, instead of treation one file at a time,
we wanted to use services that will allow to group multiple source files and treating them together. That's why, I developed this solution. It consists of connecting
the source Google Cloud Storage to Pub/Sub by creating notifications in Pub/Sub whenever a new file is uploaded. And, use Cloud Scheduler as a cron scheduler to launch 
a Cloud Function that will consume the messages (source files) in Pub/Sub regularly.



## AWS Data Transformations

This one is the general architecture of one of the project that I was in for more than 3.5 years. The general purpose was to develop data pipelines for luxury brands.
