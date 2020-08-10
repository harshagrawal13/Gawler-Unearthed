
# Understanding the Data

![](https://media.giphy.com/media/kMM3vtBEgSsLu/giphy.gif)

Welcome back! In this chapter, we'll be taking a good look into the Data that we have to deal with.

When we first began, it was quite confusing for us (some of it still is) but don't worry; I've broken down each and everything to explain everything.

> P.s - We know data pre-processing is a little cumbersome at times. Don't worry, you can also skip up to the end and  simply download the processed files to train your models on!

## What Types of Data do we have?
To understand what types of data we are dealing we need, we will first try to divide the data into categories.


### 1. One the basis of Geological Methods
On the basis of the methods used to obtain the data, we can broadly classify the data into two categories ->

> Note - We won't dive into the definitions and theory but just cover relavant grounds. You can always refer to this tutorial to read more!

#### A. GeoPhysical Methods
This includes Data such as Gravity, Magentics, Radiometrics, Seismic Data, Elevation Data as well as more advanced data such as Magentotellurics or Electrical Resistivity etc.

![]([https://media.springernature.com/lw785/springer-static/image/chp%3A10.1007%2F978-94-017-9924-9_16/MediaObjects/299730_1_En_16_Fig1_HTML.gif](https://media.springernature.com/lw785/springer-static/image/chp%3A10.1007%2F978-94-017-9924-9_16/MediaObjects/299730_1_En_16_Fig1_HTML.gif))

A majority of this type of data is present in the form of ***gridded or visual rasters.***

To simply put, a raster consists of a *matrix of cells* (or pixels) organized into *rows and columns* (or a grid) where ***each cell contains a value*** representing information, such as Elevation or Temperature. 

![https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/GUID-6754AF39-CDE9-4F9D-8C3A-D59D93059BDD-web.png](https://desktop.arcgis.com/en/arcmap/10.3/manage-data/raster-and-images/GUID-6754AF39-CDE9-4F9D-8C3A-D59D93059BDD-web.png)

Rasters are also broadly of two types -> 

**1. Gridded or Rasters containing Raw Data**

These raster files are those files in which every cell contains the actual (raw) value collected at that GeoSpatial Location. 

In the case of Temperature, every cell in a raw raster will contain the temperature recorded at every position. 

> ToDO - Add an example of raw raster here

Gridded Rasters are present as `.ers` files or `.asc` files generally. They can also be encoded in `.tif` files but that is generally more common in Visual Rasters.

**2. Pseudocoded or Visual Rasters**

While the Gridded Raster files contain very precise details of every position, it is somehow a little difficult for us to read and find correlations.

![](https://media.giphy.com/media/S79NL9AGw9Cye65fhn/giphy.gif)
 
To better read and understand raw rasters, _we pseudocode them_. 

*Eg. we would color the cells containing high temperatures to Red, the cells containing low temperatures to Blue and everything else in between the spectrum.*

>ToDO - Add tif here.

Visual Rasters are mostly present in the format of **GeoTiff** Files with `.tif` extension. Though as I mentioned above, some GeoTiff's also contain raw data.

### Which one should we use?
![](https://media.giphy.com/media/Uni2jYCihB3fG/giphy.gif) 

Honestly, you can use both. But, we'll proceed with the raw rasters as it has two major benefits over Visual ones:
* Even though raw rasters are hard to interpret by humans, it doesn't pose an issue when it comes to machines. (They are pretty expert in reading raw & confusing data).
* Colored Rasters contain *pixel data* in **RGB Channel**; so for every raster we use, we would need to have *three features per raster* which is unnessarily adding more complexity to our model.

The gridded raster files we will be using are ->

1. Gravity (`GRAV`)
2. Gravity 1-Verical Derivitive (`GRAV_1VD`) 
3. Digital Elevation Modelling (`DEM-9s`)
4. The 9 Second Flow Direction Grid (`D8-9S`)
5. Total Magnetic Intensity (`TMI`) 
6. TMI Variable Reduction to Pole (`TMI_VRTP`)

> Note - **Radiometrics & Spectroscopy** have not been included as features due to smaller and/or incomplete size of their raster files.

You can download the desired raster files and save them in a folder from [here](https://drive.google.com/drive/folders/1UeIjRgbplXuFtBWvHCybflYqzFk6upmf?usp=sharing). Note - There are three seperate zip files - DEM, GRAVITY & TMI. After extracting you'll find all the 6 six rasters in them accordingly along with some other files.



#### B. Geochemical Methods
There is a lot of GeoChemical data provided by the Australian Government. It contains details for every mine and mineral location including -
- Which Minerals were found in that site.
- Which methods were used for analysis.
- Size & Depth of sites.
- Precise details about Lithology & Surface Geology & much more.

Most of data is present in the form of `.csv` files (Delimitted Text Files) and can be easily interepreted and viewed using Python & other GeoSpatial Softwares.

The Geochemical files we'll be using are ->
- `sarig_rs_chem_exp.csv` (**~11 GB**)
- `sarig_dh_details_exp.csv` 
 
 You can find both the files along with a dozen other Geochem files in the zip file [here](https://drive.google.com/file/d/14XXWV_Ewf4Y4jzUr0wipjxOoFn9Yl3QR/view?usp=sharing).


### How do we use them?
Now that we know and understand the data, let's dive into how will we be using them.

There are several ways to do so but the best and easiest way is to **sample rasters based on vector points.**

Let's understand what that means - 

1. Suppose we have the raster file of Digital Elevation which looks something like this ->
![Grav](https://github.com/Xavian-Brooker/Gawler-Unearthed/blob/master/res/d8-9s.jpeg)

2. Here, we want to know the exact values of gravity at certain points of interests which I obtain from my Geochemical data. *Let's say I have a csv with locations stating if they have mineralization or not.*  

3. What we will do is first import the raster in QGIS by simply clicking on it from the location manager.

4. Then we'll include the `.csv` file containing the vector data by selecting Delimited Text Layer and then finding the desired file.

5. If both the layers have the same CRS then the Vectors will properly overlay over the rasters. It will look something like this :
![Overlayed](https://github.com/Xavian-Brooker/Gawler-Unearthed/blob/master/res/sampling_overlayed.jpeg)

6. Then by using the Sampling Tool ([Install it]() if you don't have already), you can very easily select the features you want and sample the raw values at the desired points and save to a csv.

You can always read more about Point Sampling [Here](https://www.qgistutorials.com/en/docs/sampling_raster_data.html).

Now that we have a good understanding about the data and how to use it, let's proceed with the code!
