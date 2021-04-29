# Week 1

Data is a mean and the purpose of data analysis is to provide actionable recommendations to business issues that can be solved leveraging data.

How to become a Data-driven managers → Create value by making actionable recommendations based on data analysis to solve current business issues.

## Finding Groups within Data

The objective of finding groups within data is to find the right balance between similarities and differences: Treating similar cases similarly and different cases specifically.

- We want to treat similar cases in a similar way to benefit from economies of scale: efficiency.
- We want to treat different cases in a different way to improve action's: effectiveness.

The purpose fo finding groups within data is to maximize your business efficiency: It allows you to allocate your effort more efficiently. One by leveraging synergies within groups and two allocating specific capacities between different cases in order to maximize your effectiveness

## Hierarchical Clustering in Python


In statistics, the similarity is  often measured with the distance between observations.

- We may for instance take the euclidean distance:

    $$d(\textbf p,\textbf q) = d(\textbf q,\textbf p) = \sqrt{\sum_{i=1}^{n}{(q_i - p_i)^2}}$$

- This can be done with the `pdist()` function from `scipy.spatial.distance`
- However before computing the euclidean distance between observations  we need to make sure that our variables are comparable.
- What we can do in practice is to standardize the features in our data, this could be done with the function `scale()` from `sklearn.preprocessing`
    - To do this we first subtract to each value from each variable the average of this variable: This is called **mean-centering**
    - And then we divide by the standard deviation.
    - In doing so we make the distance along variables comparable.

Once we have our distance metrics from the scaled dataframe we can apply the `linkage()` function from `scipy.cluster.hierarchy`

- `linkage()` performs a hierarchical clustering given a distance metrics array. The `linkage()` function identify optimal clusters
- To plot the result of the clustering we could use the `dendrogram` method from `scipy.cluster.hierarchy`
- To decide how many clusters to define we should rely on:
    - common sense and
    - business criteria
    - While ensuring that clusters are still statistically relevant.
- Once we define the number of clusters we prefer we can use the `cut_tree(Z, n_cluster=)` from the `scipy.cluster.hierarchy` package

Once you get your clusters, you'll have to perform what I call a cluster profiling and put a label on each cluster. After all no manager cares about statistics.
It is also important to make sure that the actions you are planning to take are different from one clusters to another. 

This is important because since we want to reduce the effort needed to act effectively, it may be that in some cases some groups of observations, where some customers, even if slightly different, would actually be treated similarly. So, why should we consider them as different segments?  
Well, we shouldn't!

So in this case you need to come back and change the number of clusters in the `cut_tree()` function. It is a feedback loop based on actionable conclusions.
