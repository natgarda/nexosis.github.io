---
title: How It Works&#58; Model Building
description: Understand how to interact with the Nexosis API for both regression, classification and anomaly detection models.
copyright: 2017 Nexosis 
layout: default
category: [Regression, Classification, Anomaly Detection]
tags: [Predict, Classify, Anomaly Detection, Quick Links, Favorite]
order: 1
use_codestyles: false
---
## The Process

Regression allows you to estimate the relationships between variables. Classification allows you to organize information into categories. Anomaly Detection helps you find outliers in your data. The Nexosis API allows you to upload a dataset and it will model these relationships. Once the relationship is understood this model is persisted and used to further predict values or classify your data, given new inputs. Take a moment to familiarize yourself with the high-level process before using Regression and Classification.

We've worked hard to keep the high-level process simple. Here's the basic process:

1. [Submit a _Dataset_](#dataset)
2. [Initiate a _Session_](#session)
3. [Get Results](#results)

Then optionally:

1. [Use the Model API endpoint](#predict) to make predictions if you liked the results of the model.
2. Update _Dataset_ with additional new data and rebuild, or train new model.
3. Start a new Session. Repeat.

|<img src="../assets/img/regression-classification-anomaly.png" alt="[How It Works - Regression and Classification]" width="75%"/>

<h3 id="dataset" class="jumptarget">Submit a Dataset</h3>

<h4>Regression</h4>
Regression is a process by which the Nexosis API, through the analysis of a particular dataset, will attempt to understand the relationship a series of variables have with one specific target value given many different sets of observed data. This relationship can then be used to predict a new target value given any combination of known new variables.

For example, if you wanted to be able to predict an approximate sale price of a house you'd need a dataset containing real attributes of many different kinds of houses and their real historical sale price.  Each row describes a distinct house - its columns represent specific attributes (independent variables) that likely influence the sale price (dependent variable). These independent variables are called _features_ and the dependent variable is called the _target_. Some examples of attributes that might correspond to the sale price could be the year a house was built, the number of rooms, the number of bathrooms, livable square footage, zip code, and so on.

<h4>Classification</h4>
Classification is a process by which the Nexosis API, through the analysis of a particular dataset, will attempt to understand the categories by which you might group the rows of data together.

For example, if you had a variety of measurements of characteristics of an Iris flower that allowed you to determine which species it was - such as sepal length and width, and petal length and width, you could train a Classification model to learn to make this distinction given only these characteristics.

<h4>Anomaly Detection</h4>
Anomaly Detection is a process by which the Nexosis API, through the analysis of a particular dataset, will attempt to find observations in your dataset that fall outside of what's normal inside your dataset. It can then predict if other observations are anomalous, or outliers, using the generated model.

For example, if you had a variety of heart measurements from an EKG (encephalograph) you could determine if some of the signals were outside of the normal range.

<h4>The DataSet</h4>
Once the _dataset_ has been submitted, a _regression_ or _classification_ session can be created to build a model.

Read [Sending Data](sendingdata) for the technical details.

<h3 id="session" class="jumptarget">Initiate A Session</h3>

A _Session_ is simply the process of building the model using the supplied Dataset. This exploration of the data is computationally expensive and can be time consuming depending on the amount of data in the _dataset_.

This is where the data science happens at scale. Behind the scenes a host of algorithms will work to discover what makes your dataset tick, attempting to find what factors are influential to others, where the correlations are and ultimately provide predictions given new data inputs.

Read [Sessions](session) for the technical details.

<h3 id="results" class="jumptarget">Retrieve the Results</h3>

Once the all the results are analyzed and the relationships present are discovered, a model is built and deployed. The _SessionResult_ will contain a _modelId_ used to identify the production model endpoint where predictions get made. Additionally, the session result will also returns metrics to illuminate the strength of the relationships that were found between the features and the target value in the form of an accuracy metric in the dataset.

Read [Retrieving a Session](session#retrievingSession) for more technical details.

<h3 id="predict" class="jumptarget">Use Model API Endpoint</h3>

Once the model is deployed and you like there results, it becomes your prediction endpoint. By simply sending in new variables - or series of variables - a set of predictions can be made.

Over time you may collect more data that can help improve the model, or you could add additional variables to the _dataset_ allowing even better predictions in the future. Simply upload more data and create a new session and get new results! Each new session will create a new model with a new _modelId_, so you don't have to worry about your current model getting clobbered.

Read [Prediction Quick Start](quickstartguidepredict) for an end-to-end example where you can see how the whole process works with Regression.

Read [Classification Quick Start](quickstartguideclassification) for an end-to-end example to see how the Classification process works.

Read [Anomaly Detection Quick Start](quickstartguideanomaly) for an end-to-end example to see how the Anomaly Detection process works.