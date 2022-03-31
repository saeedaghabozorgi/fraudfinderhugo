---
title: "Lab 1: Feature Engineering"
date: 2022-03-29T17:23:55Z
draft: false
weight: 201

---

Open `1_data_engineering.ipynb` lab. This notebook shows a common Data Engineering trasformation in order to create:

* Calculate customer spending behaviour features
* Calculate terminal spending behaviour features
* Calculate terminal risk factors features 
* Calculate terminal risk index features

and obtain the wide features table to ingest in the feature store. 


### What is a feature store?

Vertex AI Feature Store provides a centralized repository for organizing, storing, and serving ML features. Using a central featurestore, enables an organization to efficiently share, discover, and re-use ML features at scale, which can increase the velocity of developing and deploying new ML applications.

### Why would you like to set up it?

Based on the scenario, so far you build and store features on BigQuery. Now, in order to predict fraud, you want to serve those features in realtime around milliseconds scale. In particular, when the ML gateway receives a prediction request for a specific entity (customer, terminal and transaction), the system needs to fetch the features related to that entity and pass them as inputs to the model for online prediction. And, as you can imagine, an analytical data warehouse such as BigQuery are not able to manage low-latency singleton read operations. 

Last year, Google Cloud announched Vertex AI, a managed machine learning (ML) platform that allows data science team to accelerate the deployment and maintenance of ML models. The plaftform is composed by several building blocks and one of the is represented by Vertex AI Feature store which would provides a managed service for low latency scalable feature serving. Also it provides a centralized feature repository with easy APIs to search & discover features and feature monitoring capabilities to track for drift and other quality issues. 

Vertex AI Feature Store uses a time series data model to store a series of values for features. This model enables Vertex AI Feature Store to maintain feature values as they change over time. Vertex AI Feature Store organizes resources hierarchically in the following order: `Featurestore -> EntityType -> Feature`. You must create these resources before you can ingest data into Vertex AI Feature Store. 

Let's do that by using the **new SDK**!

### How would you set it?

Vertex AI Feature Store uses a time series data model to store a series of values for features. This model enables Vertex AI Feature Store to maintain feature values as they change over time. Vertex AI Feature Store organizes resources hierarchically in the following order: `Featurestore -> EntityType -> Feature`. 

You must create these resources before you can ingest data into Vertex AI Feature Store.

![Example image](/assets/ff_data_model.png)

Below you have a view of how Feature store looks like when we create it on Vertex AI

![Example image](/assets/ff_view.png)