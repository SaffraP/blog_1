---
title: Project Scope - Part 2 of 3
author: ~
date: '2020-06-05'
slug: project-scope-part-2-of-3
categories: []
tags: []
description: ''
topics: []
---


Hello again! And welcome to my second post. If you missed the first one, you can read it [**here**](../project-scope-part-1-of-3/).

We left off by talking about what heartbeat and threat reports are.  

The purpose of a heartbeat report is to determine if the end client is responsive. “System Center Operations Manager uses heartbeats to monitor communication channels between an agent and the agent's primary management server. A heartbeat is a packet of data sent from the agent to the management server on a regular basis, by default every 60 seconds, using port 5723 (UDP).” [**1**](https://docs.microsoft.com/en-us/system-center/scom/manage-agent-heartbeat-overview?view=sc-om-2019) Every 60 seconds a communication happens to determine if a device is still active. You can read more about heartbeat reports [**here**](https://docs.microsoft.com/en-us/system-center/scom/manage-agent-heartbeat-overview?view=sc-om-2019).

A threat report is more in-depth. Rather than just determining if an agent (or computer or system) is running, it outlines details of what has been going on. It’s like reviewing the security camera footage on your home surveillance cameras. I found a great description of what a threat is, provided by the good folks at Rapid7. They say, “When there is an adversary with the intent, capability, and opportunity, a threat exists. When two or more of these elements are present (e.g., intent and capability, but no opportunity), we call it an impending threat, because there is just one missing piece before it becomes a true threat. When there is just one element present (e.g., an opportunity in the form of a software vulnerability), we call it a potential threat.” [**2**](https://www.rapid7.com/research/report/2020-threat-report/) A threat report from Microsoft Defender may look something like this:

![](../Images/threat_report.png)
[**Source**](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/threat-protection-reports)

There are two main sections here, *Alert Trends* and *Alert Summaries*. A trend allows you to see what is currently happening (if there a spike in resources or attacks) and a summary shows the aggregated events that have happened. For more examples of what these reports show, check out [**here**](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/threat-protection-reports).

Alright, now we understand that we are working with Microsoft Defender data and we know it’s located at the endpoints of our network. Let’s move on. 

>*“Each row in this dataset corresponds to a machine, uniquely identified by a MachineIdentifier. HasDetections is the ground truth and indicates that Malware was detected on the machine. Using the information and labels in train.csv, you must predict the value for HasDetections for each machine in test.csv.”*

This is we begin getting into some of the details about what columns we have in our data. We need to take a quick step back and review how machine learning data is structured. Since this is a machine learning competition, that will be important. 

First off, what is machine learning? In my own words, it is what happens when you use an algorithm to help predict something. There is a lot of math and programming that goes behind creating a machine learning algorithm but generally rather than creating our own algorithms, we just use the ones that have already been nicely packaged. 

There are two main types of algorithms: supervised and unsupervised. 
A *supervised* algorithm is when you feed it data that already has answers built in. It then learns from that data and when you start feeding it new data it says “Oh, I remember seeing something like this before, I’ll make an educated guess about what this new value should be.” For example, maybe we are trying to predict how many tee-shirts a gift shop will sell when they adjust their prices. We give it this information:


![](../Images/table_1.png)

The algorithm now knows how many tee-shirts were sold when the price was $10/shirt, $10.50/shirt, etc. 

We then ask it to calculate the price when a shirt is priced a $11.50. It hasn’t seen this price before, but it knows how much the sale rate tends to increase or decrease when the prices have been adjusted in the past. 

![](../Images/table_2.png)

In this example, the algorithm would likely tell us that if we adjusted the price to be $11.50/tee-shirt, we would probably sell 13 tee-shirts. If you’re interested in learning about how supervised algorithms can be further broken down into regression and classification, which algorithms are in each category, and advantages or disadvantages, see [**footnote #4**](http://intellspot.com/unsupervised-vs-supervised-learning/).

Rather than focusing on producing a finite value, an *unsupervised* algorithm tries to find patterns in the data. 

Going back to our gift shop example, maybe we don’t have information about tee-shirt sales. Instead, we have information about our customers. We have recorded the gender, age, and time of day when they visited the shop for five of our customers.

![](../Images/table_3.png)

We can’t ask the algorithm to tell us who will walk in the store next, but we can ask it what patterns it sees. It would likely help us recognize that most of our customers come in the AM. It could also break it down a bit further and recognize that of those AM customers most of them are Male or most of them are young. 

This is a super simple example. In short, unsupervised algorithms are typically best used for exploring the data and finding association and clustering patterns.

If you're interested in diving into this subject a bit deeper, [**this article**](https://machinelearningmastery.com/supervised-and-unsupervised-machine-learning-algorithms/) explains the difference between supervised, unsupervised, and semi-supervised machine learning algorithms. 

That wraps it up for part 2 of 3! In [**post #3**](../project-scope-part-3-of-3/)  we'll take a look at how to prepare your data for a machine learning algorithm and what some of the constraints are. 
