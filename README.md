# __Determination-of-Short-Tail-Keywords-for-Marketing__
 
<br/>

## 1. __Case Overview__
  
- The client has some data containing several research papers scrapped from the web and they want our help to organise all of them and group the papers by keywords or groups.<br/>
- This inturn would help them to run separate ads on social media and use SEO to target the respective keywords within them.<br/>
- One thing has to be kept in mind which is to make minimal numbers of cluster as there are distinct values within keywords and group features, thus they would result in many clusters of SEO keywords. <br/>

## 2. __Approach To solve this problem__

- The given problem required us to build a unsupervised clustering model which can group different keywords under similar groups.

- As per the requirement, we have to look after these three question and anlyse their solutions properly:<br/>
  
  - How many clusters would be optimal from the data provided?
  - How many clusters would be optimal from the data provided?
  - How should he visually present the data and, ultimately, the findings?  
  
### 2.1 Data Transformation for Modeling
  
- For our model we converted the “groups” feature into Boolean, such that a research paper that falls within a group will have 1 marked next to it, and 0 otherwise.<br/>
  
- After transform the data will look something like this:<br/>
!['Transformed Data'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/png%201.PNG)

#### 2.2 Modeling the data Using Clustering Algorithms
(I wont go in to the funtioning of K-means infact I would just show the results )

1. __K-menas Clustering__

Applying Elbow Method  on Data Matrix 
!['Alt Text'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/elbow%201.png)
__Observations:__
- As per the figure above we can deduce the elbow to occur at k=9.<br/>
Applying Variance Explained  on Data Matrix
!['Alt Text'](https://github.com/akhilkapil/Determination-of-Short-Tail-Keywords-for-Marketing/blob/main/elbow%202.png)
- We can observe that the gradient to start smoothing from k = 9, similar to what he had observered with the Elbow method.
