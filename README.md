# Call Center Instrumentation & Analytics (CCIA)

This document provides guidance and background for a hands-on lab (in Python) leveraging [Watson Studio](https://console.bluemix.net/catalog/services/watson-studio) and [Watson AI services](https://www.ibm.com/watson/developer/). 

This lab is broken into five notebooks which provide an end-to-end solution for a very common and powerful use case, the Call Center Instrumentation and Analytics (CCIA) pattern. These notebooks leverage several [Watson AI services](https://www.ibm.com/watson/developer/) to help organizations extract useful information from the unstructured data (audio files) to better understand the unstructured "dark data" that arises from phone calls to call centers. 

## Usecase

Enterprises spend more than $1 trillion on 250 billion customer service calls each year.  By using multiple IBM Watson "signal services" to extract signal from raw audio data; perform data analytics, clustering, unsupervised and machine learning, and visualizations, technical teams can use data understand patterns in call centers. KPI and ROI positive.

## What is the process? And what Watson services are used?
This lab consists of five notebooks (each step below is implemented as a separate notebook) detailed as follows:
- [Step 1](https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step1-speech-to-text.ipynb) - Speech to Text (STT) – Converts Raw Audio to Transcripts
- [Step 2](https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step2-natural-language-understanding.ipynb) - Natural Language Understanding (NLU) - extracts features concepts, entities, keywords, categories/topics,  sentiment and emotion
- [Step 3](https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step3-natural-language-classifier.ipynb) - Natural Language Classifier (NLC) - is a user trained classification service, with user defined “ground truth” that classifies text chunks
- [Step 4](https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step4-tone-analysis.ipynb) - Tone Analyzer – uses linguistic analysis to detect emotional and language tones in written text
- [Step 5](https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step5-call-center-analytics.ipynb) - Call Center Analytics – analyzes and visualizes the data signal to allow for interpretation of data and in cases, actionable insights

## Beginner Audience & Focus on Basics

-	This is a beginner lab intended to educate on the fundamentals of getting from data to insights with IBM Watson and open source tools 
-	Audience may include IT and operations teams curious about enriching unstructured data – the lab is NOT intended for sophisticated call center technologists 
-	Lab/code does NOT purport to compete with expensive and sophisticated solutions already in market 
-	The lab and code cover the basics – to educate on the fundamental plumbing and steps, to provide base for instrumentation 

## Getting Started

This lab requires the following services which you can create on IBM Cloud.
1. [Watson Studio](https://console.bluemix.net/catalog/services/watson-studio): Watson Studio provides a suite of tools and a collaborative environment for data scientists, developers and domain experts for end-to-end data exploration, analysis and insights using the most popular open source machine learning packages and frameworks.
2. [Cloud Object Storage](https://console.bluemix.net/catalog/services/cloud-object-storage): IBM Cloud Object Storage is a highly scalable cloud storage service, designed for high durability, resiliency and security.
3. [Apache Spark](https://console.bluemix.net/catalog/services/apache-spark): Apache Spark service on IBM Cloud is a hosted offering for Apache Spark which is an open source cluster computing framework optimized for extremely fast and large scale data processing, which you can access via the newly integrated notebook interface IBM Analytics for Apache Spark. You can connect to your existing data sources or take advantage of the on-demand big data optimization of Object Storage.
4. [Speech to Text](https://console.bluemix.net/catalog/services/speech-to-text) (STT): The Watson Speech to Text service converts human voice to text. It supports multiple languages and it offers the unique capability of being able to train custom language and acoustic models, a much needed feature for enterprise applications.
5. [Natural Language Understanding](https://console.bluemix.net/catalog/services/natural-language-understanding) (NLU): The Watson Natural Language Understanding service extracts several useful features from text such as concepts, entities, keywords, relations, sentiment, semantic roles, categories, and emotion.
6. [Natural Language Classifier](https://console.bluemix.net/catalog/services/natural-language-classifier) (NLC): The Watson Natural Language Classifier service applies cognitive computing techniques to return the best matching classes for a sentence or a phrase. NLC basically informs what the text is about.
7. [Tone Analyzer](https://console.bluemix.net/catalog/services/tone-analyzer) (TA): The Watson Tone Analyzer service leverages cognitive linguistic analysis to identify a variety of tones at both the sentence and document level.
To create these services, you need to have an IBM Cloud account. You can sign up for an IBM Cloud account if you don't already have one.

### Cloud Object Storage
-	Log into your [IBM Cloud](https://ibm.com/cloud) account
-	Navigate to Catalog.
-	Click on Storage category in the left navigation column.
-	Select Object Storage service, provide a name for the service (or use default name), choose the Lite plan, and click Create.

### Apache Spark
-	Log into your [IBM Cloud](https://ibm.com/cloud) account
-	Navigate to Catalog.
-	Click on Data & Analytics category in the left navigation column.
-	Select Apache Spark service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.

### Speech to Text
-	Log into your [IBM Cloud](https://ibm.com/cloud) account
-	Navigate to Catalog.
-	Click on Watson category in the left navigation column.
-	Select Speech to Text service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
-	Once the service is created, its info page is loaded. Click on Service Credentials in the left navigation column. If no credentials are created, click on New Credentials to create a new set of credentials.
```
{
  "url": "https://stream.watsonplatform.net/speech-to-text/api",
  "username": "**********",
  "password": "**********"
}
```

-	Copy the credentials as we'll need them in the notebook.

### Natural Language Understanding
-	Log into your [IBM Cloud](https://ibm.com/cloud) account
-	Navigate to Catalog.
-	Click on Watson category in the left navigation column.
-	Select Natural Language Understanding service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
-	Once the service is created, its info page is loaded. Click on Service Credentials in the left navigation column. If no credentials are created, click on New Credentials to create a new set of credentials.
```
{
  "url": "https://gateway.watsonplatform.net/natural-language-understanding/api",
  "username": "**********",
  "password": "**********"
}
```
-	Copy the credentials as we'll need them in the notebook.

### Natural Language Classifier
-	Log into your [IBM Cloud](https://ibm.com/cloud) account
-	Navigate to Catalog.
-	Click on Watson category in the left navigation column.
-	Select Natural Language Classifier service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
-	Once the service is created, its info page is loaded. Click on Service Credentials in the left navigation column. If no credentials are created, click on New Credentials to create a new set of credentials.
```
{
  "url": "https://gateway.watsonplatform.net/natural-language-classifier/api",
  "username": "**********",
  "password": "**********"
}
```
-	Copy the credentials as we'll need them in the notebook.

### Tone Analyzer
-	Log into your [IBM Cloud](https://ibm.com/cloud) account
-	Navigate to Catalog.
-	Click on Watson category in the left navigation column.
-	Select Tone Analyzer service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
-	Once the service is created, its info page is loaded. Click on Service Credentials in the left navigation column. If no credentials are created, click on New Credentials to create a new set of credentials.
```
{
  "url": "https://gateway.watsonplatform.net/tone-analyzer/api",
  "username": "**********",
  "password": "**********"
}
```
-	Copy the credentials as we'll need them in the notebook.

### Watson Studio
- Log into your [IBM Cloud](https://ibm.com/cloud) account
- Navigate to **Catalog**.
- Click on **Watson** category in the left navigation column.
- Select **Watson Studio** service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
- Once the service is created, its info page is loaded. Click on  **Get Started** to launch Watson studio.

To execute these notebooks:
1. In Watson Studio, create a new Project and select the Complete option.
2. Provide a project name and under Define Storage, select the cloud object storage instance to associate with your project. If you haven't created any cloud object storage instances, click **Add** to associate a Cloud Object Storage instance with your project. If you already have a Cloud Object Storage created, you can select it. If not, you can step through the screens to create a Cloud Object Storage service and associate it with your project.
3. Associate an Apache Spark service with your project:
   - In your project, navigate to the **Settings** tab and scroll down to the **Associated Services** section.
   - Click on the *Add Service* drop down and select Spark ==> this will load the Apache Spark service page on IBM Cloud.
   - If you have already created the Apache Spark service, select the *Existing* tab and select the Apache Spark service you want to associate with your project. If not, then selec the *New* tab to create a new Apache Spark service. Select the Lite plan and click **Create**.
   - Provide a name for the service (or use the auto-generated name) and select the Lite plan and the Space (any of your IBM Cloud spaces; you may only have one). Click **Confirm**.
   ==> This would associate an Apache Spark service with your project which we need later on since we'll use SparkML machine learning code in the notebook.
4. In your project, under the **Assets** tab, click on New Notebook.
5. Provide a name for the notebook, and click on the **From URL** tab and provide the URL link for the notebook:
https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step1-speech-to-text.ipynb
6. Click **Create Notebook**
This would load the notebook in Watson Studio
7. Execute the steps of the notebook. Make sure the steps of each notebook are run to completion before proceeding to the sub-sequent notebooks.
8. Repeat steps 4-7 for the the notebooks corresponding to steps 2, 3, and 4:

* Step2: https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step2-natural-language-understanding.ipynb

* Step3: https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step3-natural-language-classifier.ipynb

* Step4: https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step4-tone-analysis.ipynb

9. In your project, under  **Assets** tab, click on New Notebook.
10. Provide a name for the notebook, and click on the **From URL** tab and provide the URL link for the notebook:
https://github.com/mamoonraja/call-center-think18/blob/master/notebooks/Step5-call-center-analytics.ipynb
11. For the runtime, select the Apache Spark service instance you had associated with your project.
7. Click **Create Notebook**
This would load the notebook in Watson Studio.
8. Make sure your kernel says **Python 3.5 with Spark 2.1**
If not, then go to the **Kernel** menu drop down, select **Change Kernel** and choose the **Python 3.5 with Spark 2.1** kernel.
9. Execute the steps of the notebook.

## Success Metrics

If successful – the lab participants or notebook users will

1. Gain experience in using an [IPython/Jupyter notebooks](https://ipython.org/notebook.html)
1. Connect to four [Watson](https://www.ibm.com/watson/developer/) ‘signal service’ APIs
1. Connect to [IBM Cloud Object storage](https://www.ibm.com/cloud/object-storage) for data read and write  
1. Understand how the tools and methods might benefit org


## More Documentation
- [Overview](https://github.com/mamoonraja/call-center-think18/blob/master/resources/docs/LAB-8672%20-%20Call%20Center%20Instrumentation%20%26%20Analytics%20-%20Data%20Discovery%20Overview%20Deck%20V1.pdf)
- [Detailed](https://github.com/mamoonraja/call-center-think18/blob/master/resources/docs/Call%20Center%20Instrumentation%20%26%20Analytics%20-%20Watson-Call-Center-Think18%20Documentation%20V1.pdf)

## Youtube Videos

- Speech To Text 
  - [Think2018 Lab 8672 Demo - Watson Studio + CCIA Analytics - STEP-1.A STT](https://youtu.be/CbB6dBRz07k)
  - [Think2018 Lab 8672 Demo - Watson Studio + CCIA Analytics - STEP-1.B ST](https://youtu.be/tREgpDNt9Jk)
- [Think2018 Lab 8672 Demo - Watson Studio + CCIA Analytics - Step 2 NLU](https://youtu.be/nrezUTCKf2k)
- [Think2018 Lab 8672 Demo - Watson Studio + CCIA Analytics - Step 3 NLC](https://youtu.be/z6NAjlfAFZ8)
- [Think2018 Lab 8672 Demo - Watson Studio + CCIA Analytics – Step 4 TONE](https://youtu.be/HR2PvL3CBn0)
- [Think2018 Lab 8672 Demo - Watson Studio + CCIA Analytics - Step 5]()


## Other Links:

- [Bits and bobs, including some Raw “R” Code](https://github.com/rustyoldrake/call_center_instrumentation_analytics)
- [Ground Truth Used for Pre-Trained natural language classifier](https://github.com/rustyoldrake/call_center_instrumentation_analytics/blob/master/call_center_gt_NLC_V2.csv)
