# All about AWS that Data Engineer should know

**Compute:**  
EC2 (Elastic Compute Cloud): Virtual servers for running applications.  
Lambda: Serverless compute service for running code in response to events.  
Elastic Beanstalk: Platform as a Service (PaaS) for deploying and managing applications.  
ECS (Elastic Container Service): Container orchestration service for Docker containers.  
EKS (Elastic Kubernetes Service): Managed Kubernetes service.  
AWS Fargate: Serverless compute engine for containers.  
************************************************************************************************
**Storage:**  
S3 (Simple Storage Service): Scalable object storage.  
EBS (Elastic Block Store): Block storage for EC2 instances.  
EFS (Elastic File System): Managed file storage for Linux-based workloads.  
Glacier: Archival storage with low-cost options for long-term data storage.  
Storage Gateway: Hybrid storage service for on-premises access to AWS cloud storage.  
************************************************************************************************
**Database:**  
RDS (Relational Database Service): Managed relational databases (e.g., MySQL, PostgreSQL, MariaDB, Oracle, SQL Server).  
DynamoDB: Managed NoSQL database service.  
Redshift(https://github.com/vineetprasad19/AWS/tree/main/AWS%20Redshift#aws-redshift---complete-guide): Data warehousing service.  
Aurora: High-performance relational database compatible with MySQL and PostgreSQL.  
ElastiCache: Managed in-memory data store (supports Redis and Memcached).  
DocumentDB: Managed document database service compatible with MongoDB.  
************************************************************************************************
**Analytics:**  
EMR (Elastic MapReduce): Managed big data frameworks like Hadoop(raw unprocessed data) , pySpark, sqoop, hbase etc. Its a managed cluster and allows to scale by adding and removing nodes to your cluster. 
It runs on EC2 under the hood. We need to add steps in EMR cluster which pyspark scripts we wrote .  
Glue: ETL (Extract, Transform, Load) service for data preparation. Create crawler from data catalog then add datasource like S3 bucket location, then add database where the data is loaded in the tables, then start crawler to load the data.  
Athena: Serverless query service for analyzing data in S3 using SQL. supports advanced sql, windows funstions and arrays. Very easy for non technical folks and BI Analyst folks.  
QuickSight: Business intelligence (BI) service for data visualization.  
Kinesis: Real-time data processing and analytics.  
Redshift: Data warehousing and analytics service.  
************************************************************************************************
**Developer Tools:**  
CodeBuild: Continuous integration for building and testing code.  
CodePipeline: Continuous integration and delivery service.  
CodeDeploy: Automate code deployments.  
CodeCommit: Version control using Git.  
Cloud9: Cloud-based integrated development environment (IDE).  
************************************************************************************************
**Management & Monitoring:**  
CloudWatch: Monitoring and observability for AWS resources and applications.  
CloudTrail: Logs API calls and activity in AWS accounts.  
Config: Tracks resource configurations and changes.  
************************************************************************************************
**AWS Eventbridge:**  
for workflow scheduling (Based of cron) and automation.  
************************************************************************************************
**message brokers:**  
Amazon Simple Notification Service (SNS) and Amazon Simple Queue Service (SQS) are both message brokers in AWS that allow for asynchronous communication between components  
