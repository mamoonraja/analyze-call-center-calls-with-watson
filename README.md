# Call Center Instrumentation & Analytics (CCIA)

This document provides guidance and background for a hands-on Python + IBM Watson lab being presented at IBM Think2018 conference in March 2018, and for an IPython / Jupyter notebook and python code available for open source after the event.

The focus is Call Center Instrumentation and Analytics (CCIA) pattern.   The Notebook and information here seek to help organizations beginning to explore how to better understand the unstructured "dark data" that arises from phone calls to call centers. 

## Usecase

Enterprises spend more than $1 trillion on 250 billion customer service calls each year.  By using multiple IBM Watson "signal services" to extract signal from raw audio data; perform data analytics, clustering, unsupervised and machine learning, and visualizations, technical teams can use data understand patterns in call centers. KPI and ROI positive.

## What is the process? And what Watson services are used?

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

## Success Metrics

If successful – the lab participants or notebook users will

1. Gain experience in using an [IPython/Jupyter notebooks](https://ipython.org/notebook.html)
1. Connect to four [Watson](https://www.ibm.com/watson/developer/) ‘signal service’ APIs
1. Connect to [IBM Cloud Object storage](https://www.ibm.com/cloud/object-storage) for data read and write  
1. Understand how the tools and methods might benefit org


## More Documentation
- [Overview]https://github.com/mamoonraja/call-center-think18/blob/master/resources/docs/LAB-8672%20-%20Call%20Center%20Instrumentation%20%26%20Analytics%20-%20Data%20Discovery%20Overview%20Deck%20V1.pdf)
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
