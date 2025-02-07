# AWS ElastiCache 

AWS ElastiCache falls under the AWS Database Services module which is a Caching Layer that works with databases like RDS, DynamoDB, Neptune and Redshift. It Reduces database load by storing frequently accessed data in memory (Memcached). It Supports AOF (Append-Only File) and Snapshot backups, similar to databases on persistence (Redis only).  
  
**Redis**: **REmote DIctionary Server**, t is an open-source, in-memory data structure store that is widely used as a cache, message broker, and database. Redis supports various data structures like strings, lists, sets, sorted sets, hashes, bitmaps, hyperloglogs, and streams, making it highly versatile for different use cases.  

**Memcached:** Memcached is a high-performance, distributed in-memory caching system designed to speed up dynamic web applications by reducing database load. It is widely used for caching database query results, API responses, and session data.  
  
# Memcached vs. Redis (Key Differences)  
![image](https://github.com/user-attachments/assets/9d0059b4-5436-4d51-97be-9f9bcd55a515)  
![image](https://github.com/user-attachments/assets/2ad11d50-43fe-4ce3-9d39-78e5e6161d1c)  
  
**EC2** instances can be configured to use ElastiCache for Redis or Memcached as a caching layer to improve performance.  
Example Architecture:   
+ An EC2 instance runs a web application.  
+ The application fetches data from ElastiCache (Redis/Memcached) instead of querying a database directly.  
+ This reduces database load and speeds up response times.
  
# AWS ElastiCache Replicas  
AWS ElastiCache Replicas are read-only copies of a primary node in ElastiCache for Redis. They help enhance performance, availability, and fault tolerance in a distributed caching system.  
  
# How AWS ElastiCache Replicas Work
1. Primary Node Handles Writes  
   + All write operations go to the primary node.  
2. Replicas Handle Reads  
   + Applications can be configured to direct read requests to replicas.  
3. Failover Mechanism  
   + If the primary node fails, AWS automatically promotes one of the replicas to primary.  
   + Replicas continue to serve read requests even during failover.  
  
![image](https://github.com/user-attachments/assets/20122301-cdc7-4258-b124-75d08f72eeee)  
![image](https://github.com/user-attachments/assets/063711d8-3408-42da-bdd6-34e8e53dba69)  
