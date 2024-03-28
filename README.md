# Customer-Segmentation-Analysis

## Project Overview

Customer segmentation is a powerful technique in marketing analytics, where you group customers based on common characteristics. This helps businesses tailor their strategies to target specific groups effectively. In Python, you can use machine learning algorithms like K-Means clustering to segment customers based on various features such as demographics, purchasing behavior, and more.
We will conduct a comprehensive analysis of the retail company’s customer data to discern patterns in consumer behavior. Our objective is to uncover actionable insights that will inform the company’s strategic planning for upcoming marketing campaigns, identify target demographics for new products, and recognize the most valuable customer segments.

### Data

The dataset comprises 2,205 entries across 39 distinct fields. Notably, there is a discrepancy between the dataset’s accompanying description and the actual columnar data it contains. Provided below is a detailed enumeration of the dataset’s actual columns, accompanied by inferred descriptions based on the nomenclature of each column.The complete primary dataset used for this analysis is the "ifood_df.csv" file,containing detailed information about each segmantation.

<img width="463" alt="data 1" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/f8e59726-2e7d-4491-9ba8-15e3ec98fd6b">


### Data Preparation and Cleaning 

In the initial data preparation phase we perfomed the following tasks:
- Remove null values
- Create new features to the dataset
- Remove outliers

#### Remove null values

First, we are going to do the good and old check for null values:

<img width="515" alt="null values" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/f9740506-a565-4afb-afd1-b02dab88b693">


Our dataset exhibits a mere 24 missing entries within the ‘income’ attribute, indicative of its substantial consistency and reliability.We’ll fill those with the mean.

#### Create new features to the dataset

New features comes to our rescue

<img width="514" alt="new features" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/f36e5038-9ffe-4b1a-9c6d-b17edd612117">


Two of the most importants are:

- Percentage of purchases made with discount.
- Percentage of value spent on essential items (fruits + meat + fish + sweet)

## Removing outliers
We will proceed to exclude certain customers from the dataset due to their outlier values, which deviate significantly from the general customer base

<img width="521" alt="remove" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/9106bfe2-1948-49eb-ba8c-4538cbb11388">


Okay, the new dataset have 2236 rows. In this phase of data cleansing, a nominal total of four customers were excluded from the analysis

## Feature Engineering

In this section:

- New feature: Marital
- New feature: In_relationship

#### New feature: Marital

The data frame contains 5 columns to reflect marital status. We are going to create a new column 'marital' with values: Divorced, Married, Single, Together, Widow. This column will allow us to draw some additional plots.



<img width="479" alt="19" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/c93493c6-9a8c-4d8b-b67f-b0011fefb410">



#### New feature: In_relationship

There are 3 features that reflect if a person is single (Single, Divorced, Widow) and 2 features if a person is in relationship (Together, Married). We will add an additional feature 'In_relationship'. This feature will equal 1 if a customer's marital status is 'Married' or 'Together' and 0 in all other cases.





<img width="477" alt="2o in" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/bcd1516c-7f3d-427d-9eec-24c84800f6c7">






#####                                  MntTotal by marital status

<img width="415" alt="grp" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/db8ff7eb-d769-4a0f-9115-d0084a23bc71">



## K-Means Clustering

K-means clustering, an unsupervised machine learning technique, is employed to segment data into clusters predicated on similarity metrics. This algorithm is renowned for its practical efficacy and its ability to efficiently scale to accommodate large datasets

<img width="478" alt="cluster" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/573ac7cf-49d3-4343-92d1-d3311cb5e0cd">




In this section:

- Standardising data
- Principal Component Analysis (PCA)
- Elbow method
- Silhouette score analysis

#### Standardising data

K-means clustering algorithm is based on the calculation of distances between data points to form clusters. When features have different scales, features with larger scales can disproportionately influence the distance calculation. There are various ways to standardise features, we will use standard scaling .


<img width="478" alt="sklearn" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/fcca9f7f-c0d1-4e99-8460-3cdf657a5c89">


<img width="338" alt="calcu" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/9afa581c-68de-4136-a7be-454a844ae2b3">



The mean value for all colums is almost zero and the standard deviation is almost 1. All the data points were replaced by their z-scores.

#### Principal Component Analysis (PCA)

PCA is a technique of dimensionality reduction. PCA takes the original features (dimensions) and create new features that capture the most variance of the data.


<img width="473" alt="plearn" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/8a147d15-dce0-413f-9f72-7ebe62136c2d">




#### Elbow method

The elbow method is a technique used to determine the optimal number of clusters (K) for K-means clustering algorithm.


<img width="475" alt="clustering" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/7e614508-ac3f-44d6-925e-8dcf25405586">












<img width="482" alt="cluster1" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/a44d3a15-9551-457b-8df8-c0b8307de987">






<img width="420" alt="graph" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/7aa01e4e-92a5-4826-b80b-b3a3ac9c3e3f">


Elbow method suggests 4 or 5 clusters

#### Silhouette score analysis

Silhouette score is a metric that used to assess the quality of clustering. A higher silhouette score indicates that the clusters are well-separated, while a lower score suggests that the clusters may overlap or are poorly defined.








<img width="475" alt="image" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/6789b828-b24a-4139-8db3-c40cba1424b2">


















<img width="457" alt="graph1" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/4f4d8eb4-ee7f-4628-a9d3-03950475106c">

















<img width="482" alt="28" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/21be316e-33b1-4806-a3a6-121ce15b4455">





The highest silhouette score is for 4 clusters.




## Consolidating Categorical Variables

We are faced with a challenge: The attributes detailing relationship status and educational attainment encompass an extensive array of categories, many of which bear close resemblance to one another. To streamline our analysis, it is prudent to consolidate these categories. 

Consequently, the ‘relationship status’ attribute will be bifurcated into two distinct groups: individuals with a partner and those without. Similarly, the ‘education’ attribute will be trifurcated into three categories: Undergraduate, Graduate, and Postgraduate.”



<img width="512" alt="cat" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/bc2bb1fc-17ba-4a11-8d35-adb9ed766587">



Excellent! Prior to advancing, it is imperative to evaluate the efficacy of the categorization within the education segment: We must ascertain the variance in purchasing behaviors across the different educational groups



<img width="521" alt="relation" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/3dcc315c-3977-47c1-9c09-b1ea82813fc8">




Upon analysis, it has been observed that customers within the ‘Graduated’ and ‘Postgraduate’ categories exhibit analogous behavioral patterns. Consequently, we will amalgamate these segments into a single unified group for enhanced analytical clarity.

## Investigating “accepted_cpm_N” features

The initial dataset contains five attributes that denote the client’s acceptance of the respective offers: AcceptedCmp1, AcceptedCmp2, AcceptedCmp3, AcceptedCmp4, AcceptedCmp5.

The attributes appear promising; however, I have several inquiries to address:

- What are the implications if a customer’s tenure with the company is insufficient to have been eligible for all offers? 
- How can we ascertain that the customer was indeed exposed to these offers? 
- Additionally, what is the protocol should a customer receive in excess of five offers?

Let’s examine how these features relate to the “pct_purchases_with_discount”. I anticipate them to have a strong correlation.



<img width="562" alt="image" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/6e932b73-8572-4140-96aa-773ba879fe13">




Contrary to expectations, an inverse correlation has emerged: a higher acceptance rate of offers correlates with a lower percentage of purchases made with discounts. This counterintuitive finding, coupled with the unresolved queries previously mentioned, has led to the decision to exclude this set of features. Instead, we will explore the responsiveness of customers to discounts.I’ll use the ‘pct_purchases_with_discount’ that is more straightforward.

## Exploratory Data Analysis

We will conduct an in-depth examination of our features, analyzing their distributions and interrelationships, with a focus on the most pertinent visualizations.

### Categorical Features



<img width="542" alt="feature" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/1ddb97e4-d7fd-4021-a9a5-20dc33e820ba">




We can see that most of our customers:

- Are in a relationship
- Have a high_education (graduated or more)
- Have 1 children
- Are between 30~60 years

### Continuous Features


<img width="505" alt="inco" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/0978de15-a2fb-4b4e-bdf8-de735b4cf89b">



We can see that most of our continuous variables are somewhat well distributed: We don’t have a specific range with the vast majority of data. One exception is the pct_purchases_with_discount, where 75% of our customers have less than 18.2% of purchases with discount.




### Relation between variables

From this first set of plots, we can see some interesting relationships:




<img width="521" alt="corr" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/07f0de4a-7b72-4275-a198-b0b6ebfcda6a">

Some of these relationships stand out: Let’s plot them.

<img width="521" alt="habits" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/5c8d622c-aa39-4993-83e8-2e6f03a3b5ca">


- The higher the income, the more purchases are made, and more money is spent.
- Customers with higher income are less likely to wait for discounts to buy products. This is a very actionable piece of information! Knowing that, the marketing team can have a personalized strategy for sending discounts to different customers.


  #### Now to the next set of plots:


<img width="533" alt="lebz" src="https://github.com/Releb/Customer-Segmentation-Analysis/assets/164650018/00129e1c-b21a-45b8-9b62-03389d8c42f7">




As the number of children in a household increases, 
- there is a corresponding rise in expenditure,
- a greater propensity to purchase discounted items,
- and an uptick in the acquisition of non-essential goods.

Interestingly, it has been observed that individuals without children at home tend to spend more overall and frequently purchase items at full price, positioning them as  as particularly valuable customers for the company.”

## Results
This section contains the results of the K-means clustering analysis, which aimed to identify distinct customer segments based on the total amount of purchases they made (MntTotal). The analysis utilised 'Income' and 'In_relationship' features.

### Optimal number of clusters = 4
The Elbow Method and Silhouette Analysis suggested 4 clusters (k=4). The elbow method highlighted the number of 4 or 5 clusters as a reasonable number of clusters. The silhouette score analysis revealed a peak silhouette score for k=4.

### Cluster Characteristics

#### Cluster 0: High value customers in relationship (either married or together)
- This cluster represents 26% of the customer base
- These customers have high income and they are in a relationship

#### Cluster 1: Low value single customers
- This cluster represents 21% of the customer base
- These customers have low income and they are single
  
#### Cluster 2: High value single customers
- This cluster represents 15% of the customer base
- These customers have high income and they are single

#### Cluster 3: Low value customers in relationship
- This cluster represents 39% of the customer base
- These customers have low income and they are in a relationship

## Recommendations
Based on the clusters, tailored marketing strategies can be created. Customers from these segments will have different interests and product preferences.

### Marketing Strategies for Each Cluster

#### Cluster 0: High value customers in relationship (either married or together)

- Preliminary analysis showed that high income customers buy more wines and fruits.
- A tailored campaign to promote high quality wines may bring good results.
- This cluster contains customers in relationship, family-oriented promo-images should be quite effective for this audience.

#### Cluster 1: Low value single customers

- Promos with discounts and coupons may bring good results for this targeted group.
- Loyalty program may stimulate these customers to purchase more often.
  
#### Cluster 2: High value single customers
- Similar to the Cluster 0, these customers buy a lot of wines and fruits.
- This cluster contains single customers. Promo images with friends, parties or single trips may be more efficient for single customers

#### Cluster 3: Low value customers in relationship
- This cluster has the highest percentage of our customers (39%).
- Family offers and discounts may influence these customers to make more purchases
- 
## Prospects for Subsequent Analysis:

- In-depth Investigation: Assessing the impact of children on product consumption patterns.
- Educational Influence Study: Examining the effects of educational backgrounds on consumer behavior.
- Frequent Buyer Analysis: Profiling customers who make purchases regularly.
- Sales Channel Evaluation: Comparing the effectiveness of different sales channels, such as in-store and online platforms.
- Marketing Campaign Response Analysis: Gauging the success and customer engagement of marketing initiatives.
- Dataset Enhancement: Incorporating gender data into the dataset could provide valuable insights.
- Algorithm Testing: Evaluating the performance of various clustering algorithms to optimize segmentation.

😄 🏆
