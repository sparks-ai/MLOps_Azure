# Operationalizing Machine Learning

## Table of Contents  
[Overview](#overview)  
[Architectural Diagram](#architecture) <br>
[Key Steps](#key_steps) <br> 
[Screen Recording](#recording) <br>
<br>   

<a name="overview"/>

## Overview
This project is part of the Udacity Azure ML Nanodegree. The dataset contains data about financial and personal details of customers of a bank. Based on this data, Azure will be used to configure a cloud-based machine learning production model, deploy it, and finally consume it. Besides, a pipeline will be created, published and consumed. Some of the printscreens are unclear. This is a result of the Virtual Machine used.   
<br>

<a name="architecture"/>

## Architectural Diagram
The steps to take are visualized in the figure below.
<br>
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/Architecture.png)
<br>

<a name="key_steps"/>

## Key Steps
The Key steps follow the architectural diagram and provide more details via screenshots. 
<br>

### Authentication
The Azure Machine Learning Extension needs to be installed in order to interact with Azure Machine Learning Studio (part of the az command). Then, a Service Principal account needs to be created an associated with a specific workspace. Afterwards, security and authentication are enabled and completed. 
<br>

### AutoML Experiment
The Bankmarketing dataset is uploaded and a compute cluster (Standard_DS12_v2 with 1 as the number of mininimum nodes) is created in order to configure an AutoML experiment. The AutoML experiment is a classification problem with a yes/no response. The exit criteria are such that the default 3 hours are set to 1 and the concurrency is set from default ot 5. The reason for this is that the focus is on operationalizing machine learning rather than achieving the best possible model outcomes. The screenshots below show that the Bankmarketing dataset is available (one was preloaded and I wanted to upload it myself which is the reason for 2 datasets), the AutoML experiment is completed and the resulting best model.
<br>
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/AutoML_Registered_Datasets.png)
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/AutoML_experiment_completed_2.png)
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/AutoML_best_model1.png)
<br>

### Deployment
Now that the experiment is completed and the best model is selected (the VotingEnsemble with a accuracy of 91.65%), it can be deployed into production. The voting ensemble is an ensemble learner that takes an "average" of the other top-performing models. Within Azure Machine Learning Studio, this model can be clicked and deployed with the click on a button. Deploying it will allow to interact with the HTTP API service and interact with the model by sending data over POST requests. Within the deployment settings, authentication is enabled and the model is deployed by means of an Azure Container Instance (ACI). The screenshot below shows the deployment settings for the model.    
<br>
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/Deployment.png)
<br>

### Logging
In order to retrieve logs, Application Insights has been enabled. This can be done in two ways: either as part of the deploy settings (checkbox) or afterwards via the terminal. For the last option, the az needs to be installed as well as the Python SDK for Azure. The below screenshots show that Application Insights are enabled and it shows the output of logs (a Python script). 
<br>
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/ApplicationInsights_enabled.png)
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/LogsPY.png)
<br>

### Documentation
Swagger documentation helps in explaining what the deployed model needs as input in order to deliver a valid response. For the deployed model, a Swagger JSON file can be downloaded from within Azure (within the Endpoints section by clicking on the deployed model). There are two important parts of the Swagger documentation: a swagger.sh file that downloads the latest Swagger container and a serve.py file that will start a Python server. All three files need to be in the same directory. When Swagger runs on localhost, it can be accessed via the webbrowser. The screenshots below show that Swagger is running on localhost. 
<br>
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/Swagger_contents1.png)
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/Swagger_contents2.png)
<br>
![alt text](https://github.com/sparks-ai/MLOps_Azure/blob/master/Images/Swagger_contents3.png)
<br>

### Consuming model endpoints
When the model is deployed.............................



<a name="recording"/>

## Screen Recording
Please go to https://vimeo.com/487342635 to see a screencast of the provided work on Azure. 

<a name="standout"/>
