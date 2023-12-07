# Big-Data-Processing_Parallelize-K-means
Implemented the parallelized version of k-means clustering algorithm in Spark and assess its efficiency using a real-world dataset. This repository contains code for performing K-means clustering on the RCV1 dataset using Spark. This README provides an overview of the code and its functionalities.

### Dependencies

The code requires the following libraries:

- sklearn
- numpy
- pandas
- pyspark
- matplotlib

### Data Preparation

1. **Download Data:** The code downloads the RCV1 dataset and creates chunks of compressed data for efficient processing.

2. **Parse Data:** Each data chunk is parsed using the `parse_file` function to extract features and labels for each document.

3. **Filter Data:** Documents with more than two labels or those where both labels don't belong to the same macro-label are filtered out.

4. **Convert to RDDs:** The filtered data is converted to Spark RDDs and persisted in memory for faster processing.

### Cluster Visualization

The `visualize_clusters_pop` function helps visualize the population of each cluster, providing an understanding of the distribution of documents across different clusters.

![288823828-a1643a8e-cac6-4476-bb2a-6e58769ee372](https://github.com/aj225patel/Big-Data-Processing_Parallelize-K-means/assets/63455759/770e7114-024a-4db3-a3e5-ca31858c2ef1)

### Filtering

The code offers two types of filtering:

1. **Cluster Filter:** Clusters with populations outside a specified threshold range are filtered out to ensure homogeneity within clusters. This is crucial for the effectiveness of the k-means algorithm.

2. **Feature Filter:** Features are filtered based on their importance using a cumulative sum threshold. This reduces dimensionality and focuses on the most relevant features for clustering.

### K-means Algorithm

The code includes UDFs for various tasks required for the k-means algorithm:

- `assign_cluster`: Assigns each point to a cluster based on minimum squared distance.
- `sum_points`: Sums sparse dictionaries.
- `compute_centroids`: Calculates centroids based on labelled documents.
- `compute_d2`: Computes the squared distance to the nearest centroid.

It also defines functions for different centroid initialization methods:

- `naive_init`: Initializes centroids randomly.
- `k_means_pp_init`: Initializes centroids using the k-means++ method.
- `k_means_ll_init`: Initializes centroids using the k-means|| method.

### Baseline Cost

The code calculates the baseline cost based on the human-assigned labels. This serves as a reference point for evaluating the performance of the k-means algorithm.

### Execution

The code allows you to run the k-means algorithm with various configurations. You can adjust the number of clusters (k), initialization method, and other parameters to optimize the results.

### Conclusion

**This repository provides a comprehensive implementation of K-means clustering on the RCV1 dataset using Spark. It includes data loading, visualization, filtering, and k-means execution with different initialization methods.**
