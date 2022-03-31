---
title: "Lab 7: Continues Training"
date: 2022-03-29T17:23:55Z
draft: false
weight: 404
---

For continuous training, the automated ML training pipeline can fetch a batch of the up-to-date feature values of the dataset that are used for the training task.

### ML pipeline triggers
You can automate the ML production pipelines to retrain the models with new data, depending on your use case:

* On demand: Ad-hoc manual execution of the pipeline.
On a schedule: New, labelled data is systematically available for the ML system on a daily, weekly, or monthly basis. The retraining frequency also depends on how frequently the data patterns change, and how expensive it is to retrain your models.
* On availability of new training data: New data isn't systematically available for the ML system and instead is available on an ad-hoc basis when new data is collected and made available in the source databases.
* On model performance degradation: The model is retrained when there is noticeable performance degradation.
* On significant changes in the data distributions (concept drift). It's hard to assess the complete performance of the online model, but you notice significant changes on the data distributions of the features that are used to perform the prediction. These changes suggest that your model has gone stale, and that needs to be retrained on fresh data.