---
title: "Lab 9: Model Monitoring"
date: 2022-03-29T17:23:55Z
draft: false
weight: 501
---

### What is Vertex AI Model Monitoring?

Modern applications rely on a well established set of capabilities to monitor the health of their services. Examples include:

* software versioning
* rigorous deployment processes
* event logging
* alerting/notication of situations requiring intervention
* on-demand and automated diagnostic tracing
* automated performance and functional testing

You should be able to manage your ML services with the same degree of power and flexibility with which you can manage your applications. That's what MLOps is all about - managing ML services with the best practices Google and the broader computing industry have learned from generations of experience deploying well engineered, reliable, and scalable services.

Model monitoring is only one piece of the ML Ops puzzle - it helps answer the following questions:

* How well do recent service requests match the training data used to build your model? This is called **training-serving skew**.
* How significantly are service requests evolving over time? This is called **drift detection**.

[Vertex Explainable AI](https://cloud.google.com/vertex-ai/docs/explainable-ai/overview) adds another facet to model monitoring, which we call feature attribution monitoring. Explainable AI enables you to understand the relative contribution of each feature to a resulting prediction. In essence, it assesses the magnitude of each feature's influence.

If production traffic differs from  training data, or varies substantially over time, **either in terms of model predictions or feature attributions**, that's likely to impact the quality of the answers your model produces. When that happens, you'd like to be alerted automatically and responsively, so that **you can anticipate problems before they affect your customer experiences or your revenue streams**.

### Objective

In this notebook, you will learn how to... 

* configure model monitoring
* understand how to interpret the statistics, visualizations, other data reported by the model monitoring feature

## Configure and Start your Monitoring Job

In this section, you will configure and create a model monitoring job for the fraud detection model you deployed in a previous notebook using the Cloud Console. Start by selecting your clicking your endpoint on the Vertex AI Endpoints page

![Example image](/assets/endpoint.png)

On the resulting endpoint-specific page, click the "Edit Settings" button.

![Example image](/assets/settings.png)

Click the "Model Monitoring" step in the ensuing dialog.

![Example image](/assets/mm.png)

Click the toggle to enable model monitoring for this endpoint.

![Example image](/assets/toggle.png)

We'll take a look at some of the detailed settings together.

![Example image](/assets/details.png)


After a minute or two, you should receive email at the address you configured above for USER_EMAIL. This email confirms successful deployment of your monitoring job. Here's a sample of what this email might look like:
<br>
<br>
<img src="https://storage.googleapis.com/mco-general/img/mm6.png" />
<br>
As your monitoring job collects data, measurements are stored in Google Cloud Storage and you are free to examine your data at any time. The circled path in the image above specifies the location of your measurements in Google Cloud Storage. 

Run the following cell to see an example of the layout of these measurements in Cloud Storage. If you substitute the Cloud Storage URL in your job creation email, you can view the structure and content of the data files for your own monitoring job.

You will notice the following components in these Cloud Storage paths:

- **cloud-ai-platform-..** - This is a bucket created for you and assigned to capture your service's prediction data. Each monitoring job you create will trigger creation of a new folder in this bucket.
- **[model_monitoring|instance_schemas]/job-..** - This is your unique monitoring job number, which you can see above in both the response to your job creation requesst and the email notification. 
- **instance_schemas/job-../analysis** - This is the monitoring jobs understanding and encoding of your training data's schema (field names, types, etc.).
- **instance_schemas/job-../predict** - This is the first prediction made to your model after the current monitoring job was enabled.
- **model_monitoring/job-../serving** - This folder is used to record data relevant to drift calculations. It contains measurement summaries for every hour your model serves traffic.
- **model_monitoring/job-../training** - This folder is used to record data relevant to training-serving skew calculations. It contains an ongoing summary of prediction data relative to training data.
- **model_monitoring/job-../feature_attribution_score** - This folder is used to record data relevant to feature attribution calculations. It contains an ongoing summary of feature attribution scores relative to training data.


### You can create monitoring jobs with other user interfaces

In a previous cell, you created a monitoring job using the Cloud Console. You can also use the *gcloud* command line tool to create a model monitoring job as well as the Python client library.


### Here's what a sample email alert looks like...

<img src="https://storage.googleapis.com/mco-general/img/mm7.png" />
