# Credit Card Fraud Detection

### The Mission

The [impact of credit card fraud](https://www.prnewswire.com/news-releases/payment-card-fraud-losses-reach-27-85-billion-300963232.html) on both individuals and businesses continues to grow in recent years. The global economic toll from fraudulent transactions ballooned to almost $28B in 2019 and is projected to eclipse $35B in five years. Additionally, the COVID-19 pandemic has greatly accelerated the e-commerce marketplace, prompting more and more consumers to shift towards online orders through credit cards. 

Developing a fundamentally sound CC fraud detector is the first step towards protecting one's business from unwanted thefts. The goal of this project is to show and compare various models that can properly classify a credit card transaction as either fraudulent or not. Special care is taken to use the right metrics to comapre efficacy and to take into account practical usability for each model discussed. 

### The Challenge 

Less than 1% of all credit transactions are truly fraud. In fact, the number of fraudulent transactions in the Kaggle dataset used for this project only amount to 0.17% of all transactions, which begets an interesting question: how do we train a model to accurately recognize an event that rarely occurs? 

For starters, we can simply build our model without any special care and hope for the best (this will be the first pillar in our approach, and serve as a baseline). One addition could be to inject our data with more examples of the minority case by replicating the relevant data points (i.e. the fraudulent transactions).

However, I view this more of a vanity solution - it balances class distribution but doesn't really add any NEW data for our model to learn better. 

Instead, I'll use the SMOTE library to handle training from imbalaned data. SMOTE (Synthetic Minority Oversampling Technique) works by first randomly picking out a minority sample, searching for some k nearest neighbors, and finally synthesizing a new sample between the initial point and its neighbors. This process is repeated as necessary. SMOTE augments our dataset with additional points that are "nearby" the minority values, meaning they have similar - but not duplicated - feature vectors.


#### The Approach

Just like any ML classification problem, fraud detectors can be built from a variety of models. In this project we start by exploring the canonical, supervised DNN model as a baseline. We then make enhancements to the baseline model to compensate for the inherently imbalanced nature of credit card fraud.

Finally, I explore a novel approach for real-time, psuedo-supervised fraud detection making use of the [Matrix Profile](https://www.cs.ucr.edu/~eamonn/MatrixProfile.html), a SOTA software suite designed by UCR for time series analysis. 

I use the following Kaggle dataset for this work: https://www.kaggle.com/mlg-ulb/creditcardfraud

#### Identifying Proper Metrics 

With any complex problem, it is imperative to be able to draw accurate and well-reasoned comparisons between different solutions in order to aptly measure their relative performance. To this end, it is worth spending time to discuss the imbalanced nature of CC fraud and how it affects our metrics. 

Classification accuracy, though perhaps the most commonly used ML metric, won't suffice with imabalnced data. Consider the case of a "dumb" classifier that always inferred a sample belongs to the majority class - with our dataset it would be >99% accurate! 

For a fraud classifier, we should minimize false negatives as much as possible (i.e. transactions that are classified as legitimate but are actually fraud). We can use a variant of the F1 score (which equally considers and consolidates precision and recall into one score) for this problem. The F-beta score allows us to configure beta to give more weight to either precision or recall (standard F1 score has a beta of 1). 

Since recall is not concerned with false positives (see Confusion Matrix for further explanation), we will use a higher beta to skew our metric towards recall. Thus, the F2 measure is most appropriate for fraud detection. 

#### The Outcomes 

It shouldn't come as a huge surprise that DNNs can perform well in the binary classification task of CC fraud detection. As structured for my project, the CC data is already in hand and we simply construct a model of minimal complexity to get decent inference results - this is the classic supervised learning problem that DNNs thrive off of. 
 
