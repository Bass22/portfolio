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

<img width="1220" alt="image" src="https://github.com/Bass22/portfolio/assets/29351163/2d3a9082-73c5-4dbb-be2b-aa0fd454c317">

### Use Case 2 : Batch Ingestion


## AWS Data Transformations
