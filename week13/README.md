# Week 13: Mapping Occurrence Data

This week, we're going to plot species occurrence data on a map to see where different frog species are found. **Occurrence data** are geographic coordinates in the form of latitude and longitude for locations where a particular species is recorded as being present.

There are many ways to interact with maps in Python. On the more complex end is Geographic Information Systems (GIS). This could probably be a whole course, and that's not really our scope here. We will use `geopandas` to make our maps. We'll also be using two other libraries to handle our data: `rasterio` for the base map image and `shapely` for the point occurrence data.

Much like the other plots we've worked with, we start with a blank canvas and build the map layer by layer.
1. Create the blank canvas
2. Create the background (raster image)
3. Specify the point data and map projection (CRS, or coordinate reference system), and create points dataframe
4. Use dataframe to add the points data to the map

## Files

Download the following files from Moodle and drag them into your repl:
- usa.tif
- frog_data.csv

## Import the libraries

First, at the top of our script, we should import all of the libraries we'll be using. For some of them (`pandas`, `pyplot`, `geopandas`), we'll use the standard abbreviations.

```
import pandas as pd
import matplotlib.pyplot as plt
import geopandas as gpd
from shapely.geometry import Point, Polygon
import rasterio
import rasterio.plot
```

## Create map background

Just plotting the occurrence data with no background isn't very helpful because we'd have no sense of where in geographic space those points actually are. Are they in Australia? Africa? the US? Which states? We need a map background so we can get our bearings.

We can't use just any image file, though. The image must be **georeferenced**, meaning the image has been tied to a coordinate system so that each pixel in the image has a known coordinate (latitude, longitude). The coordinate data is stored as part of the georeferenced image file. These image files are also known as **raster** files, and they're usually in the format **GeoTIFF**, using the extension **.tif**.

Georeferencing is beyond the scope of this course, so we'll use a map image that's already georeferenced: **usa.tif**

In the code below, we create the blank canvas and then import the background image (raster). The only part that you will need to change when using different input files is the filename of your raster image.

```
# Create blank canvas
# Create matplotlib figure and axis objects
fig,ax = plt.subplots()

# Create background
raster = rasterio.open("usa.tif")
rasterio.plot.show(raster, ax = ax)
```

## Create dataframe of occurrence points

Now, we need to import the occurrence data using `pandas`, set the map projection (CRS), and create a dataframe to map.

The **coordinate reference system (CRS)** defines specific map projections. This is another GIS concept that's beyond our scope here, and we're simply directly plotting unprojected latitude/longitude. So we'll use the standard coordinate system **EPSG:4326**, which is the coordinate system used by GPS.

```
# Import CSV data file
locs = pd.read_csv("frog_data.csv")

# Tie data to coordinate system
geometry = [Point(xy) for xy in zip(locs["longitude"], locs["latitude"])]
crs = {"init": "epsg:4326"}
```

Finally, in order to add this occurrence data to our map, we need to use `geopandas` create a **dataframe** of the points, CRS, and geometry we set above:

```
frogs_df = gpd.GeoDataFrame(locs, crs = crs, geometry = geometry)
```

## Plot occurrence data on map

Now, we add the dataframe to our map! As with the past couple of weeks, I don't know how to get repl to display the plot interactively, so let's go ahead and save it to a file using `pyplot` so we can look at it.

```
frogs_df.plot(ax = ax)

plt.savefig("frogs.jpg")
```

We can see the points on the map! But take a look at the CSV data file. The file actually contains occurrence data for two different frog species: _Hyla avivoca_ (bird-voiced tree frog) and _Hyla femoralis_ (pine woods tree frog). It would be more useful to color the points based on species. Looking at the file, you can see that the column with the species name has the heading "species", so that's what we will use to set the colors.

This time, instead of the 1 line in the above code with `frogs_df.plot()`, we will have two lines: 1 for each species.

```
frogs_df[frogs_df["species"] == "avivoca"].plot(ax = ax, color = "red")
frogs_df[frogs_df["species"] == "femoralis"].plot(ax = ax, color = "blue")

plt.savefig("frogs.jpg")
```

### Add legend

Now that we've plotted the occurrence data with point color based on species, we need to add a legend that shows which color indicates which species. You can change the number after "size" to change the size of the legend overlay on the image. In order for the legend to correspond to the points, we also need to add the argument `label` to the `.plot()` function.

```
frogs_df[frogs_df["species"] == "avivoca"].plot(ax = ax, color = "red", label = "Hyla avivoca")
frogs_df[frogs_df["species"] == "femoralis"].plot(ax = ax, color = "blue", label = "Hyla avivoca")

plt.legend(prop = {"size":10})
plt.savefig("frogs.jpg")
```

### Change plot visual features

There are a number of visual features we can tweak to make the plot look nicer. In particular, you may want to play around with the following arguments of `frogs_df.plot()`:
- `markersize` = number, size of point
- `color` = "string", fill color of point
- `edgecolor` = "string", outline color of point
- `linewidth` = number, width of outline of point
- `alpha` = number 0-1, transparency (1 = opaque)

```
frogs_df[frogs_df["species"] == "avivoca"].plot(ax = ax, markersize = 20, color = "red", edgecolor = "black", linewidth = 0.25, alpha = 0.7, label = "Hyla avivoca")

frogs_df[frogs_df["species"] == "femoralis"].plot(ax = ax, markersize = 20, color = "blue", edgecolor = "black", linewidth = 0.25, alpha = 0.7, label = "Hyla femoralis")

plt.legend(prop = {"size":10})
plt.savefig("frogs.jpg")
```
