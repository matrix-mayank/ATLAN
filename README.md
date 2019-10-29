## Identifying commercial centers using Points of Interest (POI) data

Brief documentation on the identification of commercial centers/markets in the city chosen, New Delhi (and the steps undertaken by me for the task)

## Step 1 - Installing relevant Python libraries

Installing necessary python libraries for GIS analysis. These included **shapely, fiona, pyproj, rtree** (and their binary wheels for Windows), followed by installation of **geopandas**. Additionally, to extract OSM data, **overpy** was installed.

## Step 2 - Understanding basic GIS concepts

a) Understanding how to create a point, line string and polygon using shapely. \
b) Importing latitude, longitude data for New Delhi followed by exploration of geodataframes and shapefiles.\
c) Understanding and implementing GIS Projections (EPSG:3035 and EPSG:4326) and selection of the most suitable projection. \
d) Creating a basemap file for New Delhi.

## Step 3 - Importing POI OSM Data for New Delhi

a) Understanding basic OSM concepts like nodes, ways and relations. \
b) Understanding multiple querying in OSM using overpass turbo (map features- amenities & shops identified from OSM Wiki: https://wiki.openstreetmap.org/wiki/Map_Features) \
c) Querying the relation New Delhi (https://www.openstreetmap.org/relation/1942586) for the most important POIs and storage of location data in python lists.

## Step 4 - Plotting OSM data

a) OSM lists converted to geodataframes and then to shapefiles, followed by plotting.

## Step 5 - Clustering (DBSCAN)

### The Algorithm

1) The algorithm starts with an arbitrary point which has not been visited and its neighborhood information is retrieved from the ϵ parameter. \
2) If this point contains MinPts within ϵ neighborhood, cluster formation starts. Otherwise the point is labeled as noise. This point can be later found within the ϵ neighborhood of a different point and, thus can be made a part of the cluster. Concept of density reachable and density connected points are important here. \
3) If a point is found to be a core point then the points within the ϵ neighborhood is also part of the cluster. So all the points found within ϵ neighborhood are added, along with their own ϵ neighborhood, if they are also core points. \
4) The above process continues until the density-connected cluster is completely found. \
5) The process restarts with a new point which can be a part of a new cluster or labeled as noise.
```markdown
```

Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)


For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/matrix-mayank/ATLAN/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
