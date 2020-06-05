---
title: Project Scope - Part 3 of 3
author: ~
date: '2020-06-05'
slug: project-scope-part-3-of-3
categories: []
tags: []
description: ''
topics: []
---


Welcome to the final part of our project scope! If you missed the first two, you can read [**part 1 here**](../project-scope-part-1-of-3/) and [**part 2 here**](../project-scope-part-2-of-3/).

Last time we discussed some of the differences between supervised and unsupervised algorithms. In this competition I’ll most likely be using supervised algorithms. 

The data will be broken into two main sections: train and test (I will also be using a validation set but we won't dive into that here).

Technical side note: There are two excellent articles about splitting the data. The first is from Google developers and it only talks about train and test sets. You can read it [**here**](https://developers.google.com/machine-learning/crash-course/training-and-test-sets/splitting-data). The [**second article**](https://towardsdatascience.com/train-validation-and-test-sets-72cb40cba9e7) is from Tarang Shah on Medium and it goes into the role of the validation set as well.  


A training set of data includes the correct answers. It’s an opportunity for the algorithm to make a guess, check to see if it’s right or not, and then learn from that. In this case, since we are trying to predict if a machine will be hit with malware, our “answer key” is a column that tells whether or not that machine was actually hit. That column is called *HasDetections*.

Here’s a snippet of what the data looks like. The first row is our unique machine identifier and the second column is our “answer key” that says whether or not malware was detected on that machine. There are several other columns of that as well but they aren’t pictured for simplicity’s sake. 

![](../Images/data_header_1.png)

Once the algorithm has learned from the training data (and you have tuned the parameters to your liking), you can then feed it the test data. Again, the test data is exactly like the training data, it just has different rows and does not include the “answer key” column. The hope is that the algorithm learned well and you can get a high confidence score as an output. 

Another technical side note: There are several different metrics that can be used to measure confidence (AUC, MSE, F1, etc). Although it’s not comprehensive, [**this article**](https://towardsdatascience.com/metrics-to-evaluate-your-machine-learning-algorithm-f10ba6e38234) goes into a few of the scoring methods that can be used to determine the accuracy of your model. If you have experience with machine learning but need ideas on how to boost your accuracy, [**here’s a bonus resource**](https://machinelearningmastery.com/machine-learning-performance-improvement-cheat-sheet/) with ideas of how to do that. 


Okay, let's dive into the last paragraph of the competition introduction provided on Kaggle. 

>*“The sampling methodology used to create this dataset was designed to meet certain business constraints, both in regards to user privacy as well as the time period during which the machine was running. Malware detection is inherently a time-series problem, but it is made complicated by the introduction of new machines, machines that come online and offline, machines that receive patches, machines that receive new operating systems, etc. While the dataset provided here has been roughly split by time, the complications and sampling requirements mentioned above may mean you may see imperfect agreement between your cross validation, public, and private scores! Additionally, this dataset is not representative of Microsoft customers’ machines in the wild; it has been sampled to include a much larger proportion of malware machines.”*


This section is outlining some of the real-world business constraints that security researchers face. There are factors that have to be taken into consideration, such as customer privacy and the timeline of events. 

Ideally, we would be able to line everything up in a nice timeline and see clearly what happened prior to a breach. The issue is that technology changes. Like the paragraph mentioned, new machines are introduced, existing machines go on and offline, machines are updated and patched, and sometime machines will receive entirely new operating systems. 

These factors do complicate the process but with careful awareness, it’s still possible to make predictions. In this competition, competitors are using the Area Under the Curve metric and the current leader has achieved 71% accuracy. This means that they can correctly predict if a machine will be hit with malware 71% of the time. 


That brings us to the end of this introductory series of posts! Thanks for reading along! Stay tuned for future posts on the progress as I sort through the data and begin the competition. 
