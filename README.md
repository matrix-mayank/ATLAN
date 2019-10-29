## **Identifying commercial centers using Points of Interest (POI) data**

Brief documentation on the identification of commercial centers/markets in the city chosen, New Delhi (and the steps undertaken by me for the task)

## Step 1 - Installing relevant Python libraries

Installing necessary python libraries for GIS analysis. These included **shapely, fiona, pyproj, rtree** (and their binary wheels for Windows), followed by installation of **geopandas**. Additionally, to extract OSM data, **overpy** was installed.

## Step 2 - Understanding basic GIS concepts

a) Understanding how to create a point, line string and polygon using shapely. 
b) Importing latitude, longitude data for New Delhi followed by exploration of **geodataframes** and **shapefiles**.
c) Understanding and implementing GIS Projections (**EPSG:3035** and **EPSG:4326**) and selection of the most suitable projection. 
d) Creating a **basemap file** for New Delhi.

## Step 3 - Importing POI OSM Data for New Delhi

a) Understanding basic OSM concepts like **nodes**, **ways** and **relations**. 
b) Understanding multiple querying in OSM using **overpass turbo** (map features- amenities & shops identified from OSM Wiki: https://wiki.openstreetmap.org/wiki/Map_Features) 
c) Querying the relation New Delhi (https://www.openstreetmap.org/relation/1942586) for the most important POIs and storage of location data in python lists.

## Step 4 - Plotting OSM data

a) OSM lists converted to geodataframes and then to shapefiles, followed by plotting.

## Step 5 - Clustering 

Clustering is the task of partitioning the dataset into groups, called clusters. The goal is to split up the data in such a way that points within a single cluster are very similar and points in a different cluster are different.

The two main clustering techniques in focus - **K-Means Clustering** and **DBSCAN Clustering**. Let us compare them one by one.

- **K-Means Clustering** - It tries to find cluster centers that are representative of certain regions of the data and alternates between two steps: assigning each data point to the closest cluster center, and then setting each cluster center as the mean of the data points that are assigned to it. The algorithm is finished when the assignment of instances to clusters no longer changes.

- **DBSCAN Clustering** - DBSCAN is a clustering method that is used in machine learning to separate clusters of high density from clusters of low density. Given that DBSCAN is a density based clustering algorithm, it does a great job of seeking areas in the data that have a high density of observations, versus areas of the data that are not very dense with observations.

*Advantages of DBSCAN Clustering over K-Means Clustering -*
1. DBSCAN does not require one to specify the number of clusters in the data a priori, as opposed to k-means.
2. DBSCAN can find arbitrarily shaped clusters. It can even find a cluster completely surrounded by (but not connected to) a different cluster. 
3. DBSCAN has a notion of noise, and is robust to outliers.

Hence is it more beneficial to use DBSCAN Clustering for spatial clustering of geo-data. The algorithm is as follows:
### The DBSCAN Clustering Algorithm

1. The algorithm starts with an arbitrary point which has not been visited and its neighborhood information is retrieved from the ϵ parameter. 
2. If this point contains MinPts within ϵ neighborhood, cluster formation starts. Otherwise the point is labeled as noise. This point can be later found within the ϵ neighborhood of a different point and, thus can be made a part of the cluster. Concept of density reachable and density connected points are important here. 
3. If a point is found to be a core point then the points within the ϵ neighborhood is also part of the cluster. So all the points found within ϵ neighborhood are added, along with their own ϵ neighborhood, if they are also core points. 
4. The above process continues until the density-connected cluster is completely found. 
5. The process restarts with a new point which can be a part of a new cluster or labeled as noise.
```markdown
*Parameters used in DBSCAN Clustering*
1. *MinPts* - The minimum number of points in each cluster. We set it to 3.
2. *Epsilon* - Starting with an arbitrary point, it's ε-neighborhood is retrieved, and if it contains sufficiently many points, a cluster is started. Otherwise, the point is labeled as noise. We set it to 0.110 kms.
```
### Why use the Haversine Metric over Euclidean Distance?
The haversine formula determines the great-circle distance between two points on a sphere given their longitudes and latitudes. Since the Earth is not flat, clustering based on the Euclidean Distance would provide innacurate results. As a result, we use the Haversine Metric. Point to be noted: the value of ε must be defined in radians as the Haversine Metric uses data in radians. For reference, 1 radian = 6371.0088 km

## Step 6 - Eliminating noise and plotting the shapefile clusters

a) Points indicated by noise are labeled as -1 by the DBSCAN Algorithm. 
b) We remove the noise points and store the resulting polygon file in shapefile format for plotting.


## Step 7 - Cluster Analysis

a) **Silhouette Coefficient** - The silhouette score is calculated utilizing the mean intra-cluster distance between points, AND the mean nearest-cluster distance. For instance, a cluster with a lot of data points very close to each other (high density) AND is far away from the next nearest cluster (suggesting the cluster is very unique in comparison to the next closest), will have a strong silhouette score. A silhouette score ranges from -1 to 1, with -1 being the worst score possible and 1 being the best score. Silhouette scores of 0 suggest overlapping clusters. _Our clustering results in a silhouette score of 0.252._

b) **Eliminating clusters with number of points lesser than the average number of points in clusters** - We calculate the number of points in each cluster, find it's average and then eliminate the clusters having number of points less than the average number of points. These clusters are visualised in the following bar graph:

c) **Eliminating clusters with area lesser than the average area of clusters** - We calculate the area of each cluster, find it's average and then eliminate the clusters having area less than the average cluster area. These clusters are visualised in the following bar graph:

d)**Brute-force identification and naming of the most significant clusters** - From the top clusters in both categories, we look up the geographical coordinates on Google Maps to find out which are the 4 most significant clusters. As shown in visualization, these are Connaught Place, Saket, Malviya Nagar and Lajpat Nagar.

[Link](url) and ![Image](src)
