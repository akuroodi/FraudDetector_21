# Credit Card Fraud Detection

### Why Build a Fraud Detector?

The [impact of credit card fraud](https://www.prnewswire.com/news-releases/payment-card-fraud-losses-reach-27-85-billion-300963232.html) on both individuals and businesses continues to grow in recent years. The global economic toll from fraudulent transactions ballooned to almost $28B in 2019 and is projected to eclipse $35B in five years. Additionally, the COVID-19 pandemic has greatly accelerated the e-commerce marketplace, prompting more and more consumers to shift towards online orders through credit cards. 

### The Purpose of this Project

Developing a fundamentally sound CC fraud detector is the first step towards protecting one's business from unwanted thefts. The goal of this project is to show and compare various models that can properly classify a credit card transaction as either fraudulent or not. Special care is taken to use the right metrics to comapre efficacy and to take into account practical usability for each model discussed. 

I use the following Kaggle dataset for this work: https://www.kaggle.com/mlg-ulb/creditcardfraud


#### Types of Fraud Detectors

Just like any ML classification problem, fraud detectors can be built from a variety of models. In this project we start by exploring the canonical, supervised DNN model as a baseline. We then make enhancements to the baseline model to compensate for the inherently imbalanced nature of credit card fraud - the fact that less than 1% of transactions are truly fraudulent. 

Finally, I explore a novel approach for real-time, psuedo-supervised fraud detection making use of the [Matrix Profile](https://www.cs.ucr.edu/~eamonn/MatrixProfile.html), a SOTA software suite designed by UCR for time series analysis. 



 
