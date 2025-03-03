# All about AWS that Data Engineer should know

**Advanced Permissions and Accounts**  
[MFA](https://github.com/vineetprasad19/AWS/blob/main/mfa.md)  
[IAM](https://github.com/vineetprasad19/AWS/blob/main/iam.md) 
[AWS Organizations](https://github.com/vineetprasad19/AWS/blob/main/organizations.md)  
[STS](https://github.com/vineetprasad19/AWS/blob/main/sts.md)  
[Policies](https://github.com/vineetprasad19/AWS/blob/main/policies.md)  
[AWS Resource Access Manager - RAM](https://github.com/vineetprasad19/AWS/blob/main/ram.md)  
[AWS Service Quotas](https://github.com/vineetprasad19/AWS/blob/main/service-quotas.md)  
************************************************************************************************
**Networking**  
[VPC - Virtual Private Cloud](https://github.com/vineetprasad19/AWS/blob/main/vpc.md)  
[VPNs](https://github.com/vineetprasad19/AWS/blob/main/vpn.md)  
[AWS Transit Gateway](https://github.com/vineetprasad19/AWS/blob/main/transit-gateway.md)  
[BGP - Border Gateway Protocol](https://github.com/vineetprasad19/AWS/blob/main/bgp.md)  
[AWS Global Accelerator](https://github.com/vineetprasad19/AWS/blob/main/global-accelerator.md)  
[DX - Direct Connect](https://github.com/vineetprasad19/AWS/blob/main/direct-connect.md)  
[Route53](https://github.com/vineetprasad19/AWS/blob/main/route53.md)  
[AWS PrivateLink](https://github.com/vineetprasad19/AWS/blob/main/privatelink.md)  
************************************************************************************************
**Compute:**  
EC2 (Elastic Compute Cloud): Virtual servers for running applications.  
Lambda: Serverless compute service for running code in response to events.  
Elastic Beanstalk: Platform as a Service (PaaS) for deploying and managing applications.  
ECS (Elastic Container Service): Container orchestration service for Docker containers.  
[EKS (Elastic Kubernetes Service)](https://github.com/vineetprasad19/AWS/blob/main/Kubernetes/README.md): Managed Kubernetes service.  
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
RDS (Relational Database Service): Managed Traditional OLTP relational databases (e.g., MySQL, PostgreSQL, MariaDB, Oracle, SQL Server).  
DynamoDB: Serverless Fully Managed NoSQL (Key-Value, Wide Column) database service.  
[Redshift](https://github.com/vineetprasad19/AWS/tree/main/AWS%20Redshift#aws-redshift---complete-guide): Data warehousing service (OLAP).  
Aurora: OLTP (High-performance) relational database compatible with MySQL and PostgreSQL. (5X performance vs MySQL)  
[ElastiCache](https://github.com/vineetprasad19/AWS/blob/main/ElasticCache/README.md): Managed in-memory data store (supports Redis and Memcached).  
DocumentDB: Serverless Fully Managed NoSQL (Document-based) document database service compatible with MongoDB for document storage (JSON-based).   
![image](https://github.com/user-attachments/assets/0fb1340d-f817-4784-a229-8355a6e311d4)  
![image](https://github.com/user-attachments/assets/438d859c-d35a-44b1-b457-ebd6fa0a3744)  
************************************************************************************************
**Analytics:**  
EMR (Elastic MapReduce): Managed big data frameworks like Hadoop(raw unprocessed data) , pySpark, sqoop, hbase etc. Its a managed cluster and allows to scale by adding and removing nodes to your cluster. 
It runs on EC2 under the hood. We need to add steps in EMR cluster which pyspark scripts we wrote .  
[AWS Glue](https://github.com/vineetprasad19/AWS/blob/main/AWS%20Glue/README.md): ETL (Extract, Transform, Load) service for data preparation. Create crawler from data catalog then add datasource like S3 bucket location, then add database where the data is loaded in the tables, then start crawler to load the data.  
Athena: Serverless query service for analyzing data in S3 using SQL. supports advanced sql, windows funstions and arrays. Very easy for non technical folks and BI Analyst folks.  
QuickSight: Business intelligence (BI) service for data visualization.  
Kinesis: Real-time data processing and analytics.  
Redshift: Data warehousing and analytics service.  
![image](https://github.com/user-attachments/assets/b2f4e1e2-eaa6-4b51-849e-4cc933ddec9c)
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
