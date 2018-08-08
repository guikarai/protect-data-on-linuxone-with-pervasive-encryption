# Welcome in Step 2 about instantiating the ELK microservice from the IBM Cloud private catalog

The objective is to discover the IBM Cloud private catalog in order to instantiate containers from Docker images that once together create the ELK microservice. In this way, you will be able to create later your crypto dashboard from ICp.

## The agenda for this section is about:
1. What the ELK..?!
2. What to Keep in mind about ELK?
3. Discover the Helm chart from the calalog
4. Configure and install your banking microservice
5. Access your banking microservice

## Agenda of this Step 2 is the following:

Build the Docker image
2. Deploy the docker image to IBM Cloud private

# ELK Stands for ElasticSearch Logstach Kibana

## What the ELK..?!
Elasticsearch is a search engine based on Lucene. It provides a distributed, multitenant-capable full-text search engine with an HTTP web interface and schema-free JSON documents. Elasticsearch is developed in Java and is released as open source under the terms of the Apache License. Official clients are available in Java, .NET (C#), PHP, Python, Apache Groovy, Ruby and many other languages. According to the DB-Engines ranking, Elasticsearch is the most popular enterprise search engine followed by Apache Solr, also based on Lucene.

Elasticsearch is developed alongside a data-collection and log-parsing engine called Logstash, and an analytics and visualisation platform called Kibana. The three products are designed for use as an integrated solution, referred to as the "Elastic Stack" (formerly the "ELK stack").

Elasticsearch can be used to search all kinds of documents. It provides scalable search, has near real-time search, and supports multitenancy. "Elasticsearch is distributed, which means that indices can be divided into shards and each shard can have zero or more replicas. Each node hosts one or more shards, and acts as a coordinator to delegate operations to the correct shard(s). Rebalancing and routing are done automatically". Related data is often stored in the same index, which consists of one or more primary shards, and zero or more replica shards. Once an index has been created, the number of primary shards cannot be changed.

More information about ELK here: https://www.elastic.co



👍 Congratulations! Your ELK application has been instantiated from IBM Cloud Private. You can now ready for the step 4.

## What to Keep in mind about ELK?
"ELK" is the acronym for three open source projects: Elasticsearch, Logstash, and Kibana. 

* Elasticsearch is a search and analytics engine. 
* Logstash is a server‑side data processing pipeline that ingests data from multiple sources simultaneously, transforms it, and then sends it to a "stash" like Elasticsearch. 
* Kibana lets users visualize data with charts and graphs in Elasticsearch. 

The Elastic Stack is the next evolution of ELK.

# Build the Docker image 
The objective is to build a Docker image from the banking application and then deploy it to the IBM Cloud private.

Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build, users can create an automated build that executes several command-line instructions, step by step.
