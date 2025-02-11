# AWS Glue

Glue is a service which has many components and capabilities, and we will talk about some of those capabilities.

# Why name glue?

Because basically it binds together multiple components and that's why maybe it is a good logical name to give. It is called AWS glue.

What it is in a very basic sense it is a serverless data integration service.

It helps you to integrate data from different sources and then perform analytics, or at least give
you a base on which analytics can be performed. It gives you all the capabilities you need for data integration, and that is all done in a serverless fashion. So you do not have to set up any infrastructure. The most common capability you would probably get started off glue is what we call catalog.

# Catalog

Catalog itself has two components which means that two things make up a catalog. One is called a glue crawler, another is called a glue data catalog.

Once we have data, obviously we need to process it and for that processing we have services like AWS Glue Studio. Then we have glue development endpoint where you could connect and then perform analysis. And then you can obviously define workflows if the need be. So glue workflows can also be there.

If you are more on DevOps side and you need some approach. Let's say you want to run serverless, spark workload, or you need capabilities like dynamic frame, or you want to use some streaming capabilities so that glue streaming dynamic frame and serverless spark can also be very useful to you. So there are multiple things. And obviously when you have so much data, you need to ensure quality of the data. And we don't want to manually verify all these things. So there is a machine learning powered data cleansing system also which you could leverage for your application.

![image](https://github.com/user-attachments/assets/cdef8618-8de3-4a5b-adcc-9d28e4464e24)

when you build a data catalog it is a logical reference of your enterprise data. All the data is information is stored into this data catalog. So what are common characteristics.   
What we would expect from a data catalog I would be able to discover data from that right. I should be able to discover what I am looking for. I should have search capabilities in that.  
I should also be able to harvest metadata from various sources. It should also be having some data intelligence capabilities so that you should be able to provide.  
Also, I may want to scale it so that multiple multiple data sets can be included in that, and multiple people at the same time can access it provided they have access to it means security also become important in these cases.  
So this is all settings we would be expecting into a catalog.  

![image](https://github.com/user-attachments/assets/7b6d40c8-f44c-48ac-8351-9d5646a3e907)

# What is a Glue Catalog Formal Defination?   

Glue catalog is an index to the location, schema and runtime metrics of your data. So database would be the logical boundary in which you would be keeping this information. So catalog would contain databases.  
And obviously those databases would contain tables in that. So tables would be there and through my data stores which could be a traditional database or Amazon S3, I would be running some crawler.  
That crawler would be bringing data to my databases. So crawler is a program who goes scans your data store, checks what type of information is available there, what type of data is there, what is the schema associated.  
And that information is then put together in a table format into the database. So that is called a crawler. So crawler scans your data source and then creates a table. Table would contain the metadata.  
It would contain the details of those data including its schema inside. So that is the work of crawler. If you want you could also create these tables manually. That is also possible. 
Maybe you don't want to use automated discovery of your data, or maybe crawler is not capable to discover your data. You may be able to add manually these tables, and once these tables are ready, you should be able to reference them for your analytics services.  
And one catalog can obviously contain multiple databases. And those databases can contain multiple tables right from storage perspective. But what this catalog is actually it is a Apache Hive Metastore compatible catalog.  
So what technology they use behind the scene in AWS that is not revealed, but it is still similar to Apache Hive.  

![image](https://github.com/user-attachments/assets/3b2c85de-9b66-414d-aab3-62c264b9443f)

# Crawler  
crawlers are basically the program that connect to a data store, progress through the list of classifiers, and determine the schema for your data.   
Classifier is the program who identifies your data format?   
Is it a CSV file?  
Is it a tab separated value?  
Is it a database? If it is a database, what are the tables inside it?   
So that is all identified by glue classifier when the crawler actually runs.  

# Classifier Option
Let's say your data is in format, which a glue cannot understand by default. So what you should do in that case. we have option to create classifiers. Classifier are basically the identification mechanism of glue.  
Classifiers will help you in identifying the data. So there are common file format like Avro, Awsy, parquet, JSON, binary, JSON, XML and all these type of thing, It also works on operating system logs files.  
Ruby squid reads CSV file, Amazon Redshift, MySQL, these are all automatically identified and these can be in compressed format even. We should be able to uncompress and able to detect it.  
So these are all built in classifiers. If you feel, let's say you want to uh, to catalog a PDF file which is not here, what you could do in that case, you could create your own custom classifier.  
And it uses a specific language by which you could identify that is called grok pattern. And through that you should be able to identify it. So there are a lot of examples where you can look for this data.  
[Click here to read more](https://docs.aws.amazon.com/glue/latest/dg/add-classifier.html)

![image](https://github.com/user-attachments/assets/7bac4322-14e5-4721-a50f-7999e4e3bbc2)
