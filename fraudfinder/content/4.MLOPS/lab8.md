---
title: "Lab 8: Model Delivery"
date: 2022-03-29T17:23:55Z
draft: false
weight: 405
---

### Model Continuous delivery
In this section, your system continuously delivers new pipeline implementations to the target environment that in turn delivers prediction services of the newly trained model. For rapid and reliable continuous delivery of pipelines and models, you should consider the following:

Verifying the compatibility of the model with the target infrastructure before you deploy your model. For example, you need to verify that the packages that are required by the model are installed in the serving environment, and that the memory, compute, and accelerator resources that are available.

Testing the prediction service by calling the service API with the expected inputs, and making sure that you get the response that you expect. This test usually captures problems that might occur when you update the model version and it expects a different input.

Testing prediction service performance, which involves load testing the service to capture metrics such as queries per seconds (QPS) and model latency.

Validating the data either for retraining or batch prediction.

Verifying that models meet the predictive performance targets before they are deployed.

Automated deployment to a test environment, for example, a deployment that is triggered by pushing code to the development branch.

Semi-automated deployment to a pre-production environment, for example, a deployment that is triggered by merging code to the main branch after reviewers approve the changes.

Manual deployment to a production environment after several successful runs of the pipeline on the pre-production environment.