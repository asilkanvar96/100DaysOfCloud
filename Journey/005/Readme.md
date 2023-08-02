# Data Analytics and Real-time Data Ingestion

## Cloud Research

**Data Analytics**

**Athena →** interactive query service that can analyze data in S3 with SQL. Its serverless and you pay only for the queries that you run. If you don’t need an ETL job, its also a good service to work on. In seconds delivery with large-scale datasets. You need to define a schema in Athena.

<img src='/images/Amazon-Athena.png'>

**EMR →** big data solution for petabyte-scale data processing and interactive analytics and ml that use big data knowledge like Apache Spark, Hive and Presto. Users need to know big data related topics to operate with EMR.

<img src='/images/EMR.png'>

**OpenSearch Service →** To perform interactive log analytics, real-time application monitoring, website search. OpenSearch is an open source, distributed search and analytics suite that is derived from Elasticsearch.

<img src='/images/OpenSearch-Service.png'>

## **Data Movement**

### **Amazon Kinesis**

It collect, process and analyze real-time, streaming data for quickly analysis. Its also cost-effective. Data that can be ingested can be real-time data like video, audio, logs, website clickstreams and IoT. for ml, analytics. You can use Amazon Kinesis to process and analyze data as it arrives, which means that you can respond quickly—you don’t need to wait for all your data to be collected before processing can begin.

**Kinesis Data Streams**
Its a real-time data streaming service. Designed to continuously capture gigabytes of data per second from hundreds of thousands of sources. (like website clickstreams, database event streams, financial transactions.) Data can be available in milliseconds.
<img src="/images/Amazon-Kinesis-Data-Streams.png">

**Kinesis Data Firehose**
Designed to load streaming data into data lakes, stores and analytics services. Its fully managed and capture, transform and deliver streaming data to many services such as S3, Redshift, generic HTTP endpoints. Automatically scales and batch compress, transform and encrypt your data streams before loading.
<img src="/images/Amazon-Kinesis-Data-Firehose.png">

**Kinesis Data Analytics**
Designed to transform and analyze streaming data in real-time with Apache Flink. Its also scales automatically to match the volume and throughput of your incoming data. It takes care of everything thats required to run streaming app continuously. You pay only for the resources that your streaming apps consume.
<img src="/images/Kinesis-Data-Analytics.png">

**Kinesis Video Streams**
Amazon Kinesis Video Streams is designed to securely stream video from connected devices to AWS and like others, it can scale automatically based on the need.

<img src="/images/Amazon-Kinesis-Video-Streams.png">

### **AWS Glue** \*\*

Its serverless data integration service. Its mostly use for discover, prepare and combine with other data analytics tools. Its also used tasks like enriching, cleaning, normalizing, and combining data; and loading and organizing data in databases, data warehouses, and data lakes.

### **AWS DMS**

Data Migration Service helps you migrate databases to AWS. Source db remains fully operational during the migration.

**S3 CRR**

S3 Cross-Region Replication (CRR), you can replicate objects and their respective metadata and object tags into other AWS Regions for reduced latency, compliance secure and most importantly disaster recovery. It automatically replicates data between buckets across different AWS Regions. Some use-cases are;

- Compliance: Amazon S3 stores your data across multiple geographically distant Availability Zones by default. However, compliance requirements might require you to store data at even greater distances. You can use CRR to replicate data between distant AWS Regions to satisfy these requirements.
- Latency performance: If your customers or end users are distributed across one or more geographic locations, you can minimize latency for data access by maintaining multiple object copies in AWS Regions that are geographically closer to your customers.
- Regional efficiency: If you have compute clusters in two or more AWS Regions that analyze the same set of objects, you might choose to maintain object copies in all of those AWS Regions.

**S3 Intelligent-Tiering** is a good storage class for data with unknown, changing, or unpredictable access patterns—independent of object size or retention period. There are no retrieval charges in S3 Intelligent-Tiering. S3 Intelligent-Tiering has no minimum eligible object size, but objects smaller than 128 KB are not eligible for automatic tiering.

**QuickSight**

Its a serverless interactive dashboard service used for BI. It can connect multiple resources at once and scale your data. It can also automatically look for patterns and outliers. It can deliver personalized email reports and alerts to end users. Can be accessible from virtually anywhere. (like iOS, Android, mobile web apps.) It has ml integrations like anomaly detection, forecasting and what-if analyses. Customize Auto-Narratives and weave them into dashboards. Optimize costs through the pay-per-session model by paying only for actual usage, with no need to buy thousands of end-user licenses for large-scale BI or embedded analytics. Use row-level and column-level security with API support for control at the user or group level.
