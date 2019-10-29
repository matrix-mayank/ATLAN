## Identifying commercial centers using Points of Interest (POI) data

Brief documentation on the identification of commercial centers/markets in the city chosen, New Delhi (and the steps undertaken by me for the task)

## Step 1 - Installing relevant Python libraries

Installing necessary python libraries for GIS analysis. These included **shapely, fiona, pyproj, rtree** (and their binary wheels for Windows), followed by installation of **geopandas**. Additionally, to extract OSM data, **overpy** was installed.

## Step 2 - Understanding basic GIS concepts

a) Understanding how to create a point, line string and polygon using shapely. \
b) Importing latitude, longitude data for New Delhi followed by exploration of geodataframes and shapefiles.\
c) Understanding and implementing GIS Projections (EPSG:3035 and EPSG:4326) and selection of the most suitable projection.

## Step 3 - Importing OSM Data for New Delhi

a) Understanding basic OSM concepts like nodes, ways and relations. \
b) Understanding multiple querying in OSM using overpass turbo (map features- amenities & shops identified from OSM Wiki: https://wiki.openstreetmap.org/wiki/Map_Features) \
c) Querying the relation New Delhi (https://www.openstreetmap.org/relation/1942586) for the most important POIs and storage of location data in python lists.\
d) Creating a basemap file for New Delhi.

## Step 4 - Plotting OSM data

a) 

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
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
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/matrix-mayank/ATLAN/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
