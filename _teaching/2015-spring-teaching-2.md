---
title: "Machine learning"
collection: teaching
type: "Graduate Courses"
permalink: /teaching/2015-spring-teaching-1
venue: " Osnabrück university, Cognitive sceince, Computer vision group"
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





## d) Linkage criteria

In the following you find implementations for single- and complete-linkage clustering. 

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


# Assignment 3: Kmeans Clustering
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

  


<!-- #region nbgrader={"grade": false, "grade_id": "cell-fa945b11f93016c4", "locked": true, "schema_version": 3, "solution": false, "task": false} -->
## b) Why might the clustering for k=7 not look optimal? What happens if you run the algorithm several times?
<!-- #endregion -->

<!-- #region nbgrader={"grade": true, "grade_id": "cell-16925a76b18a76fe", "locked": false, "points": 1, "schema_version": 3, "solution": true, "task": false} -->
K-Means works best for datasets in which clusters have the same circular shape and the same amount of datapoints per cluster. Opposed to a Mixture of Gaussians, in which the different distributions/clusters are weighted and the standard deviations may differ between distributions and also between different dimensions, in K-Means the variance is fixed and the same metric is used for all clusters. 
Moreover, the outcome of K-Means is a local minima, depending on the random initialization of the cluster centers. This local minimal may not be the global optimum.
<!-- #endregion -->


