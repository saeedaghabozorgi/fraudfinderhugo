---
title: "Lab 10: All together"
date: 2022-03-29T17:23:55Z
draft: false
weight: 503
---
# All Together Now

In this notebook, we'll connect the pieces you've already built:

* engineered features
* feature store
* model
* endpoint

into one web application.

## App Description

The application we're deploying consists of the following four microservices deployed to Google Cloud Run:

* ff-web - the web user interface
* ff-datagen - the data generator, produces a live stream of fabricated financial transactions
* ff-predict - the predictor, reads a pub/sub queue of streaming transactions, combines incoming transaction data with corresponding aggregates from the feature store, makes model predictions, and deposits the results in a BigQuery table
* ff-server - the Vertex server, this provides access to the Vertex AI API so your app can query and display the resources in your project

Here's a block diagram of the application you will deploy:

![Example image](/assets/app_diagram.png)