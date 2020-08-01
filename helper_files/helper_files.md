
# Helper Files

Now, a lot of times, we try to use the standard way of doing things but they may throw an error or our system might not computationally support it. And so we've also compiled a few helper files ->  

![](https://media.giphy.com/media/1qchCIQZBxQJZpbfZ2/giphy.gif)

> This documentation is just a brief explanation of the uses of the helper files. A detailed insight into the code & functionality is written properly in the notebook itself.

  

### 1. CSV to SHP (Jupyter-Notebook)

Now, if you've completed the part of sampling vector points from rasters using CSV files then you might have sometime faced an issue of CRS mismatch.

> To know and understand more about CRS, visit [here](https://www.earthdatascience.org/courses/earth-analytics/spatial-data-r/intro-to-coordinate-reference-systems/)

The major reason behind it is that the CRS of the Vector File & the Raster File *might be different*. Sometimes, the CRS of the vector file might be 0 (Unknown). This is because when we use Delimited Text to use a vector layer for co-ordinates, ***a specified CRS is absent***.


This is the reason, a shapefile (`.shp`) is preferred over a `.csv` file. This notebook will allow you to transform a CSV file containing any pair of coordinates (you must know the CRS of it though) to a shapefile of any other CRS you want to reproject it as.

***You might need to use this for sampling points for the TMI & TMI_VRTP Raster***

> Note - It might take 15-20 minutes to run for points more than 1 million for CSV to SHP notebook.

  

### 2. CSV Merger Tool (Jupyter Notebook)

This tool allows you to merge two or more CSV files containing vector wise raster information based on one/multiple common column(s).

This is helpful in combining any number of csv files that you obtain after sampling once you have them individually.

This comes under help if your system can't sample multiple rasters at one go. And so you sample every raster individually keeping one column (eg. SAMPLE_NO) as common and then use this to merge all of it together.


### 3. Plot-me (Jupyter Notebook)

One of the most import part of Data science is understand and visualize data. Though, when the complexity of data increases, it becomes more and more challenging about how to plot it and thus we've included our `plot_me.ipynb` file that will help you with Geospatial plotting. 

You can do the same in any GIS application (eg. - QGIS or ArcGIS) as well but it's easier in python. (p.s - there is a lot of further customization here as well).


 