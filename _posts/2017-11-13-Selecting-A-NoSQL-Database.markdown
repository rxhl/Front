---
layout: post
title: Selecting a NoSQL Database
comments: true
---

Challenges with traditional databases and selecting the right NoSQL solution.

<img class="no-shadow" alt="NoSQL" src="/Front/assets/img/11/nosql.jpg" style="width: 60%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>courtesy: Simon Jakowicz</em></p>

Relational databases (RDBMS) have long been a cornerstone in the computing industry, but like everything else, change is the only constant. 

### **Challenges with traditional databases**

* Not a good fit for large data volume with varying datatypes e.g. images and videos.

* [Vertical scaling](https://en.wikipedia.org/wiki/Scalability#Horizontal_and_vertical_scaling) is feasible only upto a certain extent.

* [Sharding](https://en.wikipedia.org/wiki/Shard_(database_architecture)) causes operational problems e.g. managing shard failures.

* Consistency (satisfying [ACID](https://en.wikipedia.org/wiki/ACID) requirements) has been a bottleneck for scalability in RDBMS.

<img class="no-shadow" alt="CAP" src="/Front/assets/img/11/cap.jpg" style="width: 40%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>CAP theorem</em></p>

### **Benefits of NoSQL**

* NoSQL is a **BaSE** system.
    * **Basically Available:** The system does not guarantee availability in accordance with the
      [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem).
    * **Soft State:** The state of the system may change over time, even without an input.
    * **Eventual Consistency:** The system will become consistent over time, provided that the system does
    not receive any input during that period.

* A non-locking concurrency control mechanism so that the real time reads will not conflict with the writes.

* Scalable replication and distribution.

Now we have SQL vs NoSQL differences cleared out, it's time to dig in some of the most popular options and their use cases.

### **I. Document Store**

Most popular, most diverse. Best suited for applications with varied data requirements. Instead of storing data in different tables, data that is frequently queried together is stored together in the same document.

<img class="no-shadow" alt="MongoDB" src="/Front/assets/img/11/mongo.jpg" style="width: 30%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>MongoDB: The poster child of NoSQL</em></p>

**When to use them?**

* Backend of large websites with a high volume of R/W using JSON.

* Real-time analysis and high speed logging.

* Caching and high scalability.

Some of the big names using MongoDB include Sony, Udacity, IBM, HTC and Foursquare.

### **II. Column Store**

Column type NoSQL boasts high availability. They are best suited for high velocity random reads and writes.
They have flexible sparse/wide column requirements.  Column types run on clusters of multiple servers and are perfect for gigantic applications.

<img class="no-shadow" alt="Cassandra" src="/Front/assets/img/11/cas.png" style="width: 30%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Cassandra</em></p>

**When to use them?**

* Applications that always require frequent writes.

* Applications that are geographically distributed over multiple data centers.

* Applications that are really huge (>100 TB) and can tolerate short term inconsistency.

Some of the big names using Cassandra include CERN, Netflix and Facebook.

### **III. Key-Value Store**

Key-Value stores are well suited for frequent but smaller reads and writes. They have a relatively simple query structure compared to other three types.

<img class="no-shadow" alt="Redis" src="/Front/assets/img/11/redis.png" style="width: 30%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Redis</em></p>

**When to use them?**

* Caching data from RDBMS to improve performance.

* Tracking transient attributes in a bigger application e.g. shopping cart.

* Storing configuration and user information for mobile applications.

Some of the big names using Redis are GitHub, StackOverflow and Pinterest.

### **IV. Graph Store**

Graph stores are well suited for leveraging data relationships that store relationship information as a first-class entity. They are usually built on top of column stores to provide richer functions e.g. Facebook.

<img class="no-shadow" alt="Neo4j" src="/Front/assets/img/11/neo.png" style="width: 30%; height: auto; display: block; margin: 0 auto;"/>
<p style="text-align: center; font-size:15px;"><em>Neo4j</em></p>

**When to use them?**

* Network and IT infrastructure management.

* Identity and access management.

* Recommendation systems and social networks.

### **Furthermore**
Hope this brief introduction will help you select the right NoSQL solution. Here are some additional resources:

* [NoSQL by MongoDB](https://www.mongodb.com/nosql-explained)
* [List of NoSQL databases](http://nosql-database.org/) 
