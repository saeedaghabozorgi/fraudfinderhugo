---
title: "Lab 6: CI/CD for Pipeline"
date: 2022-03-29T17:23:55Z
draft: false
weight: 403
---

### Continuous integration
Pipeline continuous integration: You build source code and run various tests. The outputs of this stage are pipeline components (packages, executables, and artifacts) to be deployed in a later stage.

In this setup, the pipeline and its components are built, tested, and packaged when new code is committed or pushed to the source code repository. Besides building packages, container images, and executables, the CI process can include the following tests:

* Unit testing your feature engineering logic.

* Unit testing the different methods implemented in your model. For example, you have a function that accepts a categorical data column and you encode the function as a one-hot feature.

* Testing that your model training converges (that is, the loss of your model goes down by iterations and overfits a few sample records).

* Testing that your model training doesn't produce NaN values due to dividing by zero or manipulating small or large values.

* Testing that each component in the pipeline produces the expected artifacts.

* Testing integration between pipeline component


### Continuous delivery
In this level, your system continuously delivers new pipeline implementations to the target environment 