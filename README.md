# __Determination-of-Short-Tail-Keywords-for-Marketing__
 
<br/>

## 1. __Case Overview__
  
- The client has some data containing several research papers scrapped from the web and they want our help to organise all of them and group the papers by keywords or groups.<br/>
- This in turn would help them to run separate ads on social media and use SEO to target the respective keywords within them.<br/>
- One thing has to be kept in mind which is to make minimal numbers of cluster as there are a lot of distinct values within keywords and group features, thus they would result in many clusters of SEO keywords. <br/>

## 2. __Approach To solve this problem__

- The given problem required us to build an unsupervised clustering model which can categorize different keywords under similar groups.

- As per the requirement, we have to look at the following questions and anlyse their solutions properly:<br/>
  
  - How many clusters would be optimal from the data provided?
  - How should we visually present the data and, ultimately, the findings?  
  
### 2.1 Data Transformation for Modeling
  
- For our model we converted the “groups” feature into Boolean, such that a research paper that falls within a group will have 1 marked next to it, and 0 otherwise.<br/>
  
- After transform the data will look something like this:<br/>
!['Transformed Data'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/png%201.PNG)

### 2.2 Modeling the data Using Clustering Algorithms
(I wont go into the funtioning of K-means infact I would just show the analysis and where it failed to acheive the results.)

1. __K-means Clustering__

Applying Elbow Method on Data Matrix 
!['Elbow Method'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/elbow%201.png)<br/>
__Observations:__<br/>
- As per the figure above we can deduce the elbow to occur at k=9.<br/>

Applying Variance Explained on Data Matrix
!['Alt Text'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/elbow%202.png)
__Observations:__<br/>
- We can observe that the gradient to start smoothing from k = 9, similar to what he had observered with the Elbow method.<br/>

!['Alt Text'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/output_20_0.png)
__Observations:__<br/>
- On plotting silhouette score, I found out that optimal number of clusters according to silhouette score , is 27(to be the point where the Silhouette coefficient is the highest).
- Therefore, we couldn't realistically choose 27 to be the right number of clusters for the following reasons:

  1. 27 clusters will be too many for a data matrix having 398 observations in total.
  2. We couldn't market 27 different segments within the limited amount of time we had.
 
- When I plotted the 9 clusters using PCA(reduced 9 cluster to two), this is what I get:
!['Alt Text](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/output_26_1.png) 
- Cluster memberships in Figure above seemed to be distinct and non-overlapping.
- We saw  that except for two clusters, which had 80 observations each, the remaining seven clusters had 30 observations each on average

- I wanted to see weather the keywords in each group were overlapping with other clusters or not. For this I used wordcloud to see all the keywords inside a cluster.<br/>
- This is the output I got:
!['Alt Text](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/output_32_0.png)
<br/>

After looking at Figure above, we can define the nine clusters as follows: <br/>
- __Cluster 1__ : Papers talking about search and robotics
- __Cluster 2__: Papers talking in depth about models’ learning and optimization
- __Cluster 3__: Topics of application of data analytics in games and social media analytics
- __Cluster 4__: Topics of image recognition, robotics, and social media analytics
- __Cluster 5__: Topics of linear programming and search
- __Cluster 6__: Papers on reasoning-based models
- __Cluster 7__: Papers on application of data sciences in social graphs and other online mediums
- __Cluster 8__: Topics ranging in knowledge graphs
- __Cluster 9__: Papers concentrating on game theory and data security

__Our findings:__ <br/>

- Some clusters had overlapping terms; for instance, clusters 1 and 5 had “search” as the overlapping term.
- This is not good, as we want to remove the overlap to make the cluster keywords and characteristics as distinctive as possible.
- As there were so many overlapping terms in my clusters, I decided to drop the idea of using kmeans and found some other algortihm to deal with this problem.

2. __Bayesian Gaussian Mixture__
(if one want to read about bayesian Gaussian Mixture they can go to this  [Link](https://www.analyticsvidhya.com/blog/2019/10/gaussian-mixture-models-clustering/) 

- The whole reaosn to select Bayesiian Gaussian Mixture was that it was able to decide on its own the right number of clusters required for a given problem.
- Thus we dont need to evaulate the cluster required just like kmeans.
- When I fit my matrix dataset using Bayessian Gaussan Mixture, this is the result I get:<br/>



|Cluster|Observations|
|-------|----------|
|`Cluster 1`| 299|
|`Cluster 2`| 117|
|`Cluster 3`| 50|

- We can clearly see that more than 50% of the observations lie in cluster 1.
- Well its not a problem untill unless the keywords are not overlapping, so lets check the keywords in each distributions.<br/>

!['Alt Text](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/output_49_0.png)

After looking at Figure above, we can define the three clusters as follows:

- __Cluster 1__: Papers discussing in depth game theory and social media analytics.
- __Cluster 2__: Papers discussing in depth model optimization and models’ learning.
- __Cluster 3__: Topics on linear programming, knowledge graphs, and reasoning-based models.

## __Final Conlusion__
- Well, I think the result we achieved from Bayessian gaussian mixture certainy prevails the result we achieved from KMeans.
- After going through the whoe case I think we were able to get finite clusters with distinct characteristics.
- In addition I think its best to drop the output of k-means and go forward with the segments defined by the Bayesian Gaussian mixture model because clusters made by Bayesian Gaussian mixture made more intuitive sense, and second, that it was smart enough to find the optimal number of clusters all on its own.
- So in a nutshell, we can target these three components from the Bayesian Gaussian mixture model to fuel our marketing strategies.

