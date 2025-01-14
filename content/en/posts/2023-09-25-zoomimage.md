---
title: "How to draw archaeological map and rectify your map using GIS"
date: 2023-09-25
author: Fangyuan Sheng
slug: cfa
draft: false
toc: false
tags:
  - English
---
{{<block class="note">}}

My mannual book to draw archaeological map using ArcGIS 10.5 based on introductory course of [Dr. Li Wei](https://archsci.fudan.edu.cn/40/cf/c16260a409807/page.htm) (Fudan University).)

{{<end>}}

Please click [here](https://hellenshengfy.github.io/GISrectify.pdf) to get the PDF of "How to rectify your map in GIS"


{{<figure src="https://hellenshengfy.github.io/gis (2).png">}} 

**Step 1. Download DEM files from [Geospatial Data Cloud](https://www.gscloud.cn/#page1/4)**

  In order to illustrate prehistorical sites in Shanghai on the map, we need to download 5 datasets.

  {{<figure src="https://hellenshengfy.github.io/gis (3).png">}} 

  {{<figure src="https://hellenshengfy.github.io/gis (4).png">}} 

**Step 2. Import all files into ArcMap (click “Add data” - select files needed)**

  {{<figure src="https://hellenshengfy.github.io/gis (5).png">}} 
  

**Step 3. Merge files into one complete map (click "ArcToolbox" - "Data Management Tools" - "Raster"- "Raster Dataset" - "Mosaic")**


Input rasters: files to be merged (you can select all the layers and then drag it into the bar to be filled) 

Target raster: the base file to be merged on. Here I choose ASTGTMV003_N30E120_dem.tif as the target.

Mosaic operator is the most important option. This operator will determine the method to mosaic overlapping areas. You can find method descriptions in [ArcGIS official document](https://desktop.arcgis.com/en/arcmap/latest/tools/data-management-toolbox/mosaic-to-new-raster.htm) : 

   -   FIRST — The output cell value of the overlapping areas will be the value from the first raster dataset mosaicked into that location.
   
   -   LAST — The output cell value of the overlapping areas will be the value from the last raster dataset mosaicked into that location. This is the default.
   
   -   BLEND — The output cell value of the overlapping areas will be a horizontally weighted calculation of the values of the cells in the overlapping area.
   
   -   MEAN — The output cell value of the overlapping areas will be the average value of the overlapping cells.
  
   -   MINIMUM — The output cell value of the overlapping areas will be the minimum value of the overlapping cells.
  
   -   MAXIMUM — The output cell value of the overlapping areas will be the maximum value of the overlapping cells.
  
   -   SUM — The output cell value of the overlapping areas will be the total sum of the overlapping cells.
  
I choose the BlEND method because it gives me the best image for my files.

  {{<figure src="https://hellenshengfy.github.io/gis (6).png">}} 
  
{{<block class="info">}}

You can also create a new layer to save the complete map (click "ArcToolbox" -  "Data Management Tools" - "Raster"- "Raster Dataset" - "Mosaic to New Raster" ). This method will not disturb the original file and is more convenient in most cases. But in my case, there are annoying white lines on the margin of the images, so I simply use the "Mosaic" instead of "Mosaic to New Raster". Below is the demonstration of "Mosaic to New Raster". 

(1) There is no base files to be selected anymore as this method will treat each files equally.

(2) You need to type in output location and file name with extension(eg: shanghai.tif). 

(3) Reference to be GCS_WGS_1984. 

(4) You can find the Pixal type and Number of bands of your files by right click one of the file layers and select "properties". Generally speaking, number of bands is 1.

  {{<figure src="https://hellenshengfy.github.io/gis (7).png">}} 
  
  {{<figure src="https://hellenshengfy.github.io/gis (8).png">}} 

{{<end>}}

This is what complete map looks like after mosaic. Rename the layer as "shanghai_merge"

  {{<figure src="https://hellenshengfy.github.io/gis (9).png">}} 

**Step 4. Adjust the color of image**

You can choose a color ramp and then go to ("Windows"- "Image Analysis") to adjust Gamma r and other parameter.

{{<figure src="https://hellenshengfy.github.io/gis (10).png">}} 


**Step 5. Draw the boundary of Shanghai City**

Import shp file "市" which is a file of all cities of China (I get the file from Dr.Li Wei). Select Shanghai area after clicking "select features" on the bar.

{{<figure src="https://hellenshengfy.github.io/gis (11).png">}} 

Export the feature by right clicking layer "市" - "Data"- "Export Data". I name this new shp file as "mask" since I could later use this as a mask if I want to focus on map of Shanghai city only. 


{{<figure src="https://hellenshengfy.github.io/gis (12).png">}} 

Click the square under the mask layer, and set it as hollow. Then it will be the boundary of SH.


{{<figure src="https://hellenshengfy.github.io/gis (13).png">}} 


**Step 6. Draw rivers in SH**


(1) Import river shp file "River4_polyline" and "River5_polyline". These two files contain river info in China.

{{<figure src="https://hellenshengfy.github.io/gis (14).png">}} 
 

(2) Clip river by mask (click "ArcToolbox" -  "Analysis Tools" - "Extract"- "Clip") . *Here we use Analysis tools instead of "Data Mgt Tools" because rivers are features instead of datasets.*

Import features is the feature you want to clip while the clip features is the mask you create. 


{{<figure src="https://hellenshengfy.github.io/gis (15).png">}} 
 

Rename the output as "river1" and "river2" and set the line type as "river" by clicking the line below the layer. 


{{<figure src="https://hellenshengfy.github.io/gis (16).png">}} 

**Step 7. Draw prehistoric sites in SH**

(1) Import sites csv file 

(2) Right click the layer - "Display XY data"

{{<figure src="https://hellenshengfy.github.io/gis (17).png">}} 

(3) Set symbology in "Layer properties". 

Eg: there is area (m2) info in the csv file and I use this value to differentiate sites and thus use different symbol sizes. You can also change color of circle according to categories. 

{{<figure src="https://hellenshengfy.github.io/gis (18).png">}} 



**Step 8. Cut the map**

Because the whole map seems to be too large for me, I think it would be better to focus on the surrounding area. Then I need to cut the map using my DIY mask.

(1) Create a new shapefile named "clip". Feature type to be polygon.

{{<figure src="https://hellenshengfy.github.io/gis (19).png">}} 


(2) Click "Editor" on the bar - "Start editing" -select "clip" layer - "Create Features"- select "clip" layer and Rectangle - draw a rectangle on the area I want to focus on - "Stop editing" -save.

{{<figure src="https://hellenshengfy.github.io/gis (20).png">}} 

{{<figure src="https://hellenshengfy.github.io/gis (21).png">}} 


Here you may not be able to save the file in the location you want (you may see a "fail" prompt). If this happened, just save the file with the default name and default location. 


(3) Extract the target area (click "ArcToolbox" -  "Spatial Analyst Tools" - "Extract by Mask")


{{<figure src="https://hellenshengfy.github.io/gis (22).png">}} 
    

(4) After extraction, you may need to adjust the color again (repeat the step 4) 

**Step 9. Add Legend, North arrow, Scale bar and Grid** 


Switch to layout view (the second button in the lower left corner)  

{{<figure src="https://hellenshengfy.github.io/gis (23).png">}} 

 -  Legend, North arrow, Scale bar:  click "insert" on the bar

 -  Grid: Select the border of the image and then right click "properties" -"grid"

{{<figure src="https://hellenshengfy.github.io/gis (24).png">}} 
    


**Step 10. Final adjustment of the layout by zooming out and zooming in the area** 

Adjust all other things for better illustration.


{{<figure src="https://hellenshengfy.github.io/gis (1).png">}} 


