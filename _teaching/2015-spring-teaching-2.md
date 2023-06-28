---
title: "Machine learning"
collection: teaching
type: "Teaching Practice section"
permalink: /teaching/2015-spring-teaching-1
venue: "Osnabrück university, Cognitive sceince, Computer vision group"
date: 2023-01-01
location: "Osabrück, Germany"
---

In this course, we had different topics in machine learning:
- Concept learning
- Decision Tree
- Basics of Data Mining
- Clustering
- Dimension Reduction
- Neural Network
- Classification
- Reinforcement learning
  
Clustering
======

<!-- #region nbgrader={"grade": false, "grade_id": "h00", "locked": true, "schema_version": 3, "solution": false} -->
Osnabrück University - Machine Learning (Summer Term 2023) - Prof. Dr.-Ing. G. Heidemann, Ulf Krumnack, Leila Malihi
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "heading", "locked": true, "schema_version": 3, "solution": false} -->
# Exercise Sheet: Clustering
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "intro", "locked": true, "schema_version": 3, "solution": false} -->
## Introduction

In the following tasks we will be relying on numpy. Using the following import we expect it to be in global scope as `np`. Therefore we can, after executing the following cell, use stuff like `np.array` and `np.sqrt`. Check out the [NumPy Reference](http://docs.scipy.org/doc/numpy/reference/index.html) and especially search it using e.g. [Google Site Search](https://www.google.de/search?q=array+site%3Adocs.scipy.org%2Fdoc%2Fnumpy)! You can also try `np.lookfor('keyword search docstrings')` to get help.

# Assignment 1: Distance Measures for Clusters 
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "1_ax", "locked": true, "schema_version": 3, "solution": false} -->
## a) Point and cluster distances

Explain the difference of point and cluster distances and their relation to each other. Give examples.
<!-- #endregion -->

<!-- #region nbgrader={"grade": true, "grade_id": "cell-64b9b3273be847ac", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false} -->
Clusters are collections of points. The distance of two clusters can be derived from the distance of the points they contain. This requires that distances between points can be measured, i.e., the points are from some metric space. 
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "cell-efa27e859e56e6dd", "locked": true, "schema_version": 3, "solution": false, "task": false} -->
## b) Mean and centroid distance

* Describe how the cluster metrics *mean distance* and *centroid distance* work.
* What formal requirements do they have?
* What is their computational complexity (use the [Big O notation](https://en.wikipedia.org/wiki/Big_O_notation))? 
* Give a numerical example of clusters (with cluster size at least 2), where they lead to (a) the same result and (b) different results.
<!-- #endregion -->

<!-- #region nbgrader={"grade": true, "grade_id": "cell-d8619b5b4e63d573", "locked": false, "points": 2, "schema_version": 3, "solution": true, "task": false} -->
The $D_{\text{centroid}}$ first computes the center of each cluster and then computes the distance of these centers. Hence it can only be applied to clusters that allow to compute such a center (e.g. clusters of points in a euclidean space), while the $D_{\text{mean}}$ metric can be applied to clusters of points in a general metric space (where it is possible to measure the distance of datapoints, but not necessarily to obtain a cluster center). 



Numerical example (in the euclidean space $\mathbb{R}^2$): Cluster $X=\{\begin{pmatrix}1\\1\end{pmatrix}, \begin{pmatrix}1\\4\end{pmatrix}\}$, and cluster $Y=\{\begin{pmatrix}5\\1\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\}$.

* (a) Euclidean norm:
    * Centroid distance
    
        The centroid of $X$ is 
        $$\bar{X} = \frac{1}{2}\sum_{x\in X}x = \frac{1}{2}\left[\begin{pmatrix}1\\1\end{pmatrix} + \begin{pmatrix}1\\4\end{pmatrix}\right] = \frac{1}{2}\begin{pmatrix}2\\5\end{pmatrix} = \begin{pmatrix}1\\2.5\end{pmatrix}$$
        and the centroid of $Y$ is 
    $$\bar{Y}=\frac{1}{2}\sum_{y\in Y}y= \frac{1}{2}\left[\begin{pmatrix}5\\1\end{pmatrix} + \begin{pmatrix}5\\4\end{pmatrix}\right] = \frac{1}{2}\begin{pmatrix}10\\5\end{pmatrix} = \begin{pmatrix}5\\2.5\end{pmatrix}$$

        Hence $$D_{\text{centroid}}(X,Y) = \|\begin{pmatrix}5\\2.5\end{pmatrix}-\begin{pmatrix}1\\2.5\end{pmatrix}\| = \|\begin{pmatrix}-4\\ 0\end{pmatrix}\| = 4$$

    * Mean distance

        $$D_{\text{mean}}(X,Y) = \frac{1}{2\cdot 2}\left[d\left(\begin{pmatrix}1\\1\end{pmatrix},\begin{pmatrix}5\\1\end{pmatrix}\right) + d\left(\begin{pmatrix}1\\1\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\right) + d\left(\begin{pmatrix}1\\4\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\right) + d\left(\begin{pmatrix}1\\4\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\right)\right]=\frac{1}{4}\left[4 + 5 + 4 + 5\right] = 4.5$$

    * So here $D_{\text{centroid}}(X,Y) \neq D_{\text{mean}}(X,Y)$


* (b) Take the same points but now use the maximum norm instead of the Euclidean norm (alternatively, you could also use a new dataset here).

    * Centroid distance

        The centroids stay the same (they are independent of the underlying norm) and the centroid distance is
        $$D_{\text{centroid}}(X,Y) = d_{\infty}\left(\begin{pmatrix}5\\2.5\end{pmatrix}, \begin{pmatrix}1\\2.5\end{pmatrix}\right) = \max\{|5-1|, |2.5-2.5|\} = \max\{4,0\} = 4$$

    * Mean distance

        $$D_{\text{mean}}(X,Y) = \frac{1}{2\cdot 2}\left[d_{\infty}\left(\begin{pmatrix}1\\1\end{pmatrix},\begin{pmatrix}5\\1\end{pmatrix}\right) + d_{\infty}\left(\begin{pmatrix}1\\1\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\right) + d_{\infty}\left(\begin{pmatrix}1\\4\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\right) + d_{\infty}\left(\begin{pmatrix}1\\4\end{pmatrix},\begin{pmatrix}5\\4\end{pmatrix}\right)\right]=\frac{1}{4}\left[4 + 4 + 4 + 4\right] = 4$$

    * So now $D_{\text{centroid}}(X,Y) = D_{\text{mean}}(X,Y)$.

<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "1_b", "locked": true, "schema_version": 3, "solution": false} -->
## c) Implemention of  mean and centroid distance

Now implement the $d_{mean}$ and $d_{centroid}$ distance from the lecture. Each function expects two clusters each represented by a 2-dimensional numpy array, where the number of columns $n$ reflects the dimensionality of the data space and has to agree for both clusters, while the number of rows $mx$ and $my$ can vary from cluster to cluster. The return value is the respective distance.  Use the Euclidean distance as underlying metric.

Hint: you may consider using the function `scipy.spatial.distance.cdist`. Consult the documentation to find out how to use it.
<!-- #endregion -->

   
    Args:
        cluster1 (ndarray): Points belonging to cluster 1 of shape (num_points, num_dimensions).
        cluster2 (ndarray): Points belonging to cluster 1 of shape (num_points, num_dimensions).
    
    Returns:
        float: The mean distance between the points in the two clusters.
    """
    ### BEGIN SOLUTION
    return cdist(cluster1, cluster2).mean()
    ### END SOLUTION


    Args:
        cluster1 (ndarray): Points belonging to cluster 1 of shape (num_points, num_dimensions).
        cluster2 (ndarray): Points belonging to cluster 1 of shape (num_points, num_dimensions).
    
    Returns:
        float: The distance between the centroids of two clusters.
    """
    ### BEGIN SOLUTION
    centroid1 = cluster1.mean(axis=0)
    centroid2 = cluster2.mean(axis=0)
    return np.linalg.norm(centroid1 - centroid2)
    ### END SOLUTION


```

<!-- #region nbgrader={"grade": false, "grade_id": "cell-1aa3a155692767cb", "locked": true, "schema_version": 3, "solution": false, "task": false} -->


## c) Linkage criteria

In the following you find implementations for single- and complete-linkage clustering. Take a look at the code  and answer the question posted below. You may of course change parameters and try it out on different datasets (`points.txt` & `clusterData.txt` are provided).

Note that for performance reasons the code differs from the lecture's pseudocode (ML-05 Slide 8), but in general it does the same.
<!-- #endregion -->


    
    Args:
        data (ndarray): Data points to be clustered in an array with shape (num_points, 2).
        k (int): Number of clusters.
        complete (bool): Whether to run complete linkage clustering.
        
    Returns:
        ndarray: The cluster labels for each data point. Shape is (num_points).
    """
    # Initially all points are their own cluster.
    labels = np.arange(len(data))

    # Calculate distance between all points.
    # Also removing half of the matrix because 
    # its symmetrical along the diagonal.
    dst = np.tril(cdist(data, data))

    while len(set(labels)) > k:
        # Get the lowest distance of two points which
        # do not have the same label.
        r, c = np.where(dst == np.min(dst[dst > 0]))
        
        # Ignore the case when there are multiple with
        # equally smallest distance.
        r = r[0]
        c = c[0]

        # The two points are now in the same cluster,
        # so they have a distance of 0 now.
        dst[r, c] = 0

        # Make the two clusters have the same label.
        labels[labels == labels[r]] = labels[c]

        # Check if we want to do complete linkage clustering.
        if complete:
            # Update the distances of the points which are not in the same cluster.
            for i in np.nonzero(dst[r, :] > 0)[0]:
                dst[r, i] = np.max(cdist(data[i, None], data[labels == labels[r], :]))

            # The distances to c are now the same as to r, so we can just
            # set them to zero - would be duplicates otherwise.
            dst[:, c] = 0

    return labels
```


# Assignment 3: Kmeans Clustering (5 points)
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "cell-b0db1893cc822d0c", "locked": true, "schema_version": 3, "solution": false, "task": false} -->
**a)** Perform K-means clustering to divide the following datset into 2 clusters by hand.

| x1 | x2 |x3 |
|----|----|---|
|  1 | 1  | 1 |
|  2 | 1  | 1 |
|  3 | 1  | 2 |
|  2 | 3  | 4 |
|  5 | 5  | 5 |
|  3 | 2  | 1 |

Start with the following centroids for the two clusters: $(1,1,1)$ and $(5,5,5)$.
<!-- #endregion -->

<!-- #region nbgrader={"grade": true, "grade_id": "cell-987bb819c6249404", "locked": false, "points": 3, "schema_version": 3, "solution": true, "task": false} -->
Step 1: Initialize the centroids for the two clusters randomly. Let's say we choose the following centroids:

Cluster 1 centroid = (1, 1, 1)
Cluster 2 centroid = (5, 5, 5)

Step 2: Assign each data point to the nearest centroid. We can calculate the distance between each data point and the centroids using the Euclidean distance formula.

The distances between each data point and the centroids are as follows:


| Data Point | Distance to Cluster 1 centroid | Distance to Cluster 2 centroid | Assigned Cluster |
|:----------:|:------------------------------:|:------------------------------:|:----------------:|
| (1, 1, 1)  | 0                              | 5.196                          | Cluster 1        |
| (2, 1, 1)  | 1                              | 4.899                          | Cluster 1        |
| (3, 1, 2)  | 1.414                          | 4.242                          | Cluster 1        |
| (2, 3, 4)  | 5.744                          | 1.732                          | Cluster 2        |
| (5, 5, 5)  | 7.071                          | 0                              | Cluster 2        |
| (3, 2, 1)  | 1.732                          | 4.899                          | Cluster 1        |

Based on the distances, we assign each data point to the nearest centroid. Data points (1, 1, 1), (2, 1, 1), (3, 1, 2), and (3, 2, 1) are assigned to Cluster 1, and data points (2, 3, 4) and (5, 5, 5) are assigned to Cluster 2.

Step 3: Recalculate the centroids for each cluster by taking the mean of all the data points in the cluster.

The new centroids for the two clusters are as follows:

Cluster 1 centroid = ((1+2+3+3)/4, (1+1+1+2)/4, (1+1+2+1)/4) = (2.25, 1.25, 1.25)
Cluster 2 centroid = ((2+5)/2, (3+5)/2, (4+5)/2) = (3.5, 4, 4.5)

Step 4: Repeat steps 2 and 3 until convergence is reached.

We can see that after one iteration, the assigned clusters have changed. Data points (1, 1, 1), (2, 1, 1), and (3, 1, 2) are now assigned to Cluster 2, and data points (2, 3, 4), (5, 5, 5), and (3, 2, 1) are assigned to Cluster 1.

We can now recalculate the centroids for each cluster:

Cluster 1 centroid = ((2+5+3)/3, (3+5+2)/3, (4+5+1)/3) = (3.33, 3.33, 3.33)
Cluster 2 centroid = ((1+2+3)/3, (1+1+1)/3, (1+1+2)/3) = (2, 1, 1.33)

After the second iteration, the assigned clusters do not change, so we have
<!-- #endregion -->

**b)** $k$-mean clustering of a given dataset can result in different outcomes (as can for example be witnessed in Assignment 4). Explain, at which point the algorithms is indeterministic and explain how to compare the quallity of different outcomes.

<!-- #region nbgrader={"grade": true, "grade_id": "cell-00ab43266b028866", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false} -->
The algorithm is indeterministic because of the initial choice of cluster centers.  All subsequent steps are fully deterministic. 

Different outcomes can be assessed by the cumulated distance of points to their respective cluster centers.  The smaller that distance, the better the clustering.
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "cell-ad9b9b0920004fe2", "locked": true, "schema_version": 3, "solution": false, "task": false} -->
**c)** The pseudocode for k-means algorithm on (ML-05, slide 27) uses as the termination condition ($\exists k \in[1,K]: \|\vec{w}_k(t)-\vec{w}_k(t-1)\|>\varepsilon$). Discuss this condition from a theoretical and practical perspective and name alternatives.
<!-- #endregion -->

<!-- #region nbgrader={"grade": true, "grade_id": "cell-d93c92396260c1f3", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false} -->
The conditions states that the algorithm should terminate when the cluster centers do not more than a given threshold.

It is not even clear, that the steps of the algorithm do decrease (is it possible to create a simple example demonstrating that idea?)
<!-- #endregion -->

<!-- #region nbgrader={"grade": false, "grade_id": "3", "locked": true, "schema_version": 3, "solution": false} -->
# Assignment 4: k-means Clustering (6 points)

## a) Implement k-means clustering. Plot the results for $k = 7$ and $k = 3$ in colorful scatter plots.

How could one handle situations when one or more clusters end up containing 0 elements? Handle these situtation in your code.
<!-- #endregion -->

```{python nbgrader={'grade': True, 'grade_id': '3_code', 'locked': False, 'points': 5, 'schema_version': 3, 'solution': True}}
import numpy as np
import matplotlib.pyplot as plt

from scipy.spatial.distance import cdist

def kmeans(data, k=3):
    """
    Applies kmeans clustering to the data using k initial clusters.
    data is expected to be a numpy array of size n*2, 
    n being the amount of observations in the data. This function returns
    the centroids and the labels for the clusters data (1,1,3,5,5,5,...)
    
    Args:
        data (ndarray): 2-dimensional numpy array
        k (int): Number of clusters
    
    Returns:
        labels (ndarray): Numpy array containing numbers (=labels) with the same order as the data points
        centroids(ndarray): vector representation of cluster centers of shape k*2
    """
    ### BEGIN SOLUTION
    # Initial centroids are k random samples from the data.
    centroids = data[np.random.randint(0, data.shape[0], k)]
    old_centroids = np.zeros(centroids.shape)
    
    # Initial labels are all.. something.
    labels = np.ndarray(data.shape[0])
    
    # Lets keep count of our iterations to avoid infinite loops.
    iterations = 0
    
    while np.any(np.abs(centroids - old_centroids) > np.finfo(float).eps) and iterations < 1000:
        # Keep count of iterations and remember current centroids for change calculation.
        iterations += 1
        # Copy the centroids and keep them for break condition check.
        old_centroids = np.copy(centroids)
        
        # Calculate new labels. Labels are the index of their minimal distance to any centroid.
        labels = np.argmin(cdist(centroids, data), axis=0)
        
        # Update centroids using the new cluster labels.
        for label in range(k): 
            # Check for empty clusters.
            if np.any(labels == label):
                # Cluster is not empty, move its centroid to new mean.
                centroids[label, :] = np.mean(data[labels == label], axis=0)
            else:
                # Cluster is empty, set its centroid to the furthest outlier.
                blacksheep = np.argmax(cdist(centroids, data), axis=0)
                centroids[label, :] = data[blacksheep, :]
    
    ### END SOLUTION

    return labels, centroids
```

```{python}
# %matplotlib inline

data = np.loadtxt('clusterData.txt')

# Test experiments with a different number of clusters and different 
# number of runs here.
# You can define the number of clusters and how often k-means is called
# allowing to investigate the inlfuenece of the number of clusters and 
# of the different random cluster initializations per run.
print(data.shape)

# Experiment 1: One run with k=2
experiment = ((2,1),)
# Experiment 2: One run with k=3, one run with k=7
#experiment = ((3,1),(7,1))
# Experiment 3: Five run with k=7
#experiment = ((7,5),)


for params in  experiment:
    k = params[0]
    for i in range(1, params[1]+1):
        labels, centroids = kmeans(data, k)
        
        assert isinstance(labels, np.ndarray), "'labels' should be a numpy array!"       
        assert isinstance(centroids, np.ndarray), "'centroids' should be a numpy array!"    
        assert labels.shape==(data.shape[0],), "Each data point needs a label!"
        assert centroids.shape==(k,data.shape[1]), ("k centroids with the same dimensionality "
            "as the data are needed!")
        
        kmeans_fig = plt.figure('k-means with k={}, i={}'.format(k,i))
        plt.scatter(data[:,0], data[:,1], c=labels)
        plt.scatter(centroids[:,0], centroids[:,1], 
                    c=list(set(labels)), alpha=.1, marker='o',
                    s=np.array([len(labels[labels==label]) for label in set(labels)])*100)
        plt.title('k = {}, i = {}'.format(k, i))
        kmeans_fig.canvas.draw()
        plt.show()   
```

<!-- #region nbgrader={"grade": false, "grade_id": "cell-fa945b11f93016c4", "locked": true, "schema_version": 3, "solution": false, "task": false} -->
## b) Why might the clustering for k=7 not look optimal? 
What happens if you run the algorithm several times?
<!-- #endregion -->

<!-- #region nbgrader={"grade": true, "grade_id": "cell-16925a76b18a76fe", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false} -->
K-Means works best for datasets in which clusters have the same circular shape and the same amount of datapoints per cluster. Opposed to a Mixture of Gaussians, in which the different distributions/clusters are weighted and the standard deviations may differ between distributions and also between different dimensions, in K-Means the variance is fixed and the same metric is used for all clusters. 

In this example inter- and intra cluster variance varies together with the number of datapoints per cluster.

Moreover, the outcome of K-Means is a local minima, depending on the random initialization of the cluster centers. This local minimal may not be the global optimum.
<!-- #endregion -->

Heading 2
======

Heading 3
======
