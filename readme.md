# Assignment 8 - Clustering

## Group Members

- Allan Bo Simonsen, cph-as484
- Jean-Poul Leth-Møller, cph-jl360
- Nina Lisakowski, cph-nl163

## Tasks

### Task 1, Work through the book – build your own K Means cluster function and carry out the modelling done in the book.
We followed the guide in chapter 20 of the Data science from scratch book. The results can be seen in the jupyter notebook.
### Task 2, Write a brief description of the use cases for K Means and DBSCAN algorithms.
#### K-means Use cases
Since K-means is a clustering algorithms its use cases are primarily finding similarity in the data.  
This means that we can use it when processing pictures.  
Both for changing(scaling, pixel colors) the image or finding other similiar pictures in a search engine.     
It also used alot in document classification. To find similarities in documents by converting the text into vectors.   
Lastly it can be used in market segmentation and can be used to group customers into clusters and use this information in marketing or product recommendations.
#### DBSCAN use cases
DBSCAN, also known as Density Based Spatial Clustering of Applications with Noise, is a clustering algorithm for unsupervised learning problems.     
It is used to find the density of data and does this very well with seperating the low density from the high density.     
It also works extremely well with finding outliers and when working with irregular shaped clusters.
The DBSCAN algorithm can be used to find associations and structures in data that are hard to find manually but that can be relevant and useful to find patterns and predict trends. 

### Task 3, Thinking about these two algorithms provide a formal definition of clustering
Clustering is a technique used in machine learning to group data together. Usually, if the algorithm is used correctly, data with similiar characteristics(features) will be grouped together. And likewise data with dissimiliar characteristics should not be grouped together. These groupes are referred to as clusters.


### Task 4, Describe with examples of plotting two ways of selecting the value of K for K-means clustering
#### Elbow method
The elbow method uses the sum of squared errors(between each point and the mean of its cluster) to find the optimal K. The higher K you use the lower error rate you will get. However we also don't want to many clusters as we then lose any meaning in grouping the data together. Usually we will see an elbow in the graph, after this point higher K values will only result in small improvements in the error value. Therefore we want to choose the K value that is just at the Elbow point.

![Elbow Method taken from the Walkthrough in the book](https://user-images.githubusercontent.com/21145015/163997780-e0f2ea14-8b56-4aec-a3eb-bec2292cb878.jpg)

#### Silhouette method
The silhouette method uses the seperation distance between clusters. The measurement is between -1 & 1, where 1 is preffered. With a higher score the values in the clusters are well seperated, whereas negative values mean that the clusters are very close together and might indicate that values have been assigned to a wrong cluster. That means the optimal K value will be the one with the highest silhouette score. However we might also consider the size of each cluster and decide another "worse" K value where the clusters are more evenly distributed.

The following screenshots are from the Sklearn documentation. In this example (depending on the use case) K=4 is the better option, even though 2 has a higher silhouette value, because the clusters are much more evenly distributed with K=4 than with K=2.
![Silhouette with K2](https://user-images.githubusercontent.com/21145015/164001923-6c0bb60d-d148-48d8-8f0b-378fb598c055.jpg)
![Silhouette with K4](https://user-images.githubusercontent.com/21145015/164001928-f500b389-c2bf-41b8-96ab-f83696746056.jpg)
![Results from 2-6 K values](https://user-images.githubusercontent.com/21145015/164001927-3dc5a8ae-a435-4f15-93b6-990cdf771ad7.jpg)


Reference: [SKlearn Doc](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html)


### Task 5, Which algorithm is good for large datasets and which one is good for regions of high density 
The K-Means algorithm is good for large datasets, even though one might think otherwise as it will be slower because the algorithm has to run multiple times. But it wouldn't actually be that slow.
The DBSCAN algorithm is the one to use for regions of high density as it is a density-based clustering algorithm. It forms dense clusters and leaves out the outliers meaning the low-density areas. It is also good to use because it works well with odd shaped clusters and therefore knows when an outlier is an outlier compared to K-Means which can have some difficulties with it.

### Task 6, What does ‘high density mean’ in DBSCAN
DBSCAN stands for Density Based Spatial Clustering of Applications with Noise. High-density means that there are many datapoints close to eachother in a cluster. When datapoints aren't high-density they are low-density which means that they are outliers to this cluster and therefore categorised as noise. The purpose in DBSCAN is to identify clusters of data as high-density and seperate outliers which is seen a low-density .

### Task 7, Describe with an example how the initialization of K-Means can affect the inertia value and the quality of the model.
The problem with the initialization of K-Means is placing the initial cluster centers as close to the optimal center as possible. However the optimal center is not known, that is after all what we are trying to find. In most k-means algorithms the start positions are randomly chosen and the centers are then improved with each iteration. However these randomly chosen start points can vary alot and can result in more iterations needed and therefore longer runtime.  
There are other initialization methods such and k-means++ and naive sharding that aim to get better start positions for the center points, resulting in fewer iterations and better runtime. The preferred method in Sklearn library is "K-means++" that is build around pushing the start position centers as far away from eachother.
The following illustration show k-means iterations to find the centeriod for K=3. [Reference](https://towardsdatascience.com/the-5-clustering-algorithms-data-scientists-need-to-know-a36d136ef68)

![Iterating the K-Means algorithms to find the best K Value](https://miro.medium.com/max/480/1*KrcZK0xYgTa4qFrVr0fO2w.gif)

### Task 8, Prepare a model using K Means for the Olivetti data set from scikit learn
See the notebook file for a walkthrough of clustering and preprocessing with the Olivetti dataset.
