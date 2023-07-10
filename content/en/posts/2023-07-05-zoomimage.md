---
title: "How to draw archaeological map using ArcGIS 10.5"
date: 2023-07-05
author: Fangyuan Sheng
slug: cfa
draft: false
toc: false
tags:
  - English
---
{{<block class="note">}}

My mannual book to draw archaeological map using ArcGIS 10.5 based on introductory course of [Dr. Li Wei](https://archsci.fudan.edu.cn/40/cf/c16260a409807/page.htm) (Fudan University). 

{{<end>}}

{{<figure src="https://hellenshengfy.github.io/gis (2).png">}} 

**Step 1. Download DEM files from Geospatial Data Cloud website (www.gscloud.cn)**

  In order to illustrate prehistorical sites in Shanghai on the map, we need to download 5 datasets.

  {{<figure src="https://hellenshengfy.github.io/gis (3).png">}} 

  {{<figure src="https://hellenshengfy.github.io/gis (4).png">}} 

##  Import all files into ArcMap (click “Add data” - select files needed)

  {{<figure src="https://hellenshengfy.github.io/gis (5).png">}} 


##  Merge files into one complete map (click "ArcToolbox" - "Data Management Tools" - "Raster"- "Raster Dataset" - "Mosaic")

  Input rasters: files to be merged (you can select all the layers and then drag it into the bar to be filled) 

Target raster: the base file to be merged on. Here I choose ASTGTMV003_N30E120_dem.tif as the target.

Mosaic operator is the most important option. This operator will determine the method to mosaic overlapping areas. You can find different methods in [ArcGIS official document](https://desktop.arcgis.com/en/arcmap/latest/tools/data-management-toolbox/mosaic-to-new-raster.htm) : 

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

Tip: you can also create a new layer to save the complete map (click "ArcToolbox" -  "Data Management Tools" - "Raster"- "Raster Dataset" - "Mosaic to New Raster" ). This method will not disturb the original file and is more convenient in most cases. But in my case, there are annoying white lines on the margin of the images, so I simply use the "Mosaic" instead of "Mosaic to New Raster". Below is the demonstration of "Mosaic to New Raster". 

(1) There is no base files to be selected anymore as this method will treat each files equally.

(2) You need to type in output location and file name with extension(eg: shanghai.tif). 

(3) Reference to be GCS_WGS_1984. 

(4) You can find the Pixal type and Number of bands of your files by right click one of the file layers and select "properties". Generally speaking, number of bands is 1.

  {{<figure src="https://hellenshengfy.github.io/gis (7).png">}} 
  
  {{<figure src="https://hellenshengfy.github.io/gis (8).png">}} 

{{<end>}}

This is what complete map looks like after mosaic. Rename the layer as "shanghai_merge"

  {{<figure src="https://hellenshengfy.github.io/gis (9).png">}} 
  
  **ZooMS**: Zooarchaeology by mass spectrometry
  
  **PMF**: Collagen peptide mass fingerprinting
  
  **MALDI-TOF MS**:  Matrix-assisted laser desorption/ionization time-of-flight mass spectrometry

  **COL1**: type I collagen

  **PTM**: Posttranslational modification


{{<figure src="https://hellenshengfy.github.io/zoom1.png">}}

{{<figure src="https://hellenshengfy.github.io/zoom2.png">}}

{{<figure src="https://hellenshengfy.github.io/zoom3.png">}}

{{<figure src="https://hellenshengfy.github.io/zoom4.png">}}


Lewis Morgan brought up the idea of "Savagery-Barbarism-Civilization" stages in his *Ancient Society*. 

| Periods | Divisions |Conditions|
|---------|---------|---------|
|Savagery |I. Lower Status of Savagery|	 Infancy of the Human Race |
|Savagery |II. Middle Status of Savagery|	Acquisition of a fish subsistence and a knowledge of the use of fire|
|Savagery |III. Upper Status of Savagery|	Invention of the Bow and Arrow|
|Barbarism |IV. Lower Status of Barbarism|	Invention of the Art of Pottery|
|Barbarism| V. Middle Status of Barbarism|	Domestication of animals on the Eastern hemisphere, and in the Western from the cultivation of maize and plants by Irrigation, with the use of adobe-brick and stone|
|Barbarism |VI. Upper Status of Barbarism|	Invention of the process of Smelting Iron Ore, with the use of iron tools|
|Civilization| VII. Status of Civilization|	Invention of a Phonetic Alphabet, with the use of writing|

During savergery and barbarism stage, Lewis Morgan further defined 4 organizations of society.

(1) **Gens**: a body of consanguinei having a common gentile name
  
(2) **Phratry**: an assemblage of related gentes united in a higher association for certain common objects
  
(3) **Tribe**: an assemblage of gentes, usually organized in phratries, all the members of which spoke the same dialect
  
(4) **Confederacy of tribes**: members spoke dialects of the same stock language. It resulted in a gentile society (*societas*), as distinguished from a political society or state (*civitas*). 

## Elman Service and Kwang-chih Chang 

Lewis Morgan believed that social members were equal before the civilization stage, which was later disproved by other ethnographic evidence. 

Elman Service came up with chiefdom stage based on new evidence in his *Primitive Social Organization* where chiefdom is the stage when social inequality emerged.
  
  
Kwang-chih Chang applied this theory into the discussion of Chinese society in his discussion of Chinese bronze age.

| Name | Stage 1 |Stage 2|Stage 3|Stage 4|
|---------|---------|---------|---------|---------|
|Service |Bands| Tribes| Chiefdoms |States |
|Kwang-chih Chang |Paleolithic & Mesolithic| *Yangshao* Culture| *Longshan* Culture |*Xia*|


## Su Bingqi
  
Based on archaeological materials in China, Su Bingqi proposed 'Three Stages' theory. Later, three models for the formation of states in China (Su 1994: 132-4) are formed:
  
(1) **Original Model** of northern pattern: **early states (guguo)**: marked by the ritual complex of the Hongshan culture - **regional states (fangguo)**: the proto-Great Wall of the Xiajiadian lower level culture - **empire (diguo)**: the Great Wall of China and the remains of Qin palaces;
  
(2) **Secondary Model** of the Central Plains: the Taosi culture, the Xia/Shang/Zhou dynasties and the unification of the Qin;
  
(3) **Extended Model**: the period of migration and integration of different peoples after the end of the Qin Empire.

Unfortunately, terms in three stages and three models are not well defined and sometimes contradictary to each other. I jot a rough table for comparison with Kwang-chih Chang based on my understanding, which might not be appropriate.
  
  ### A comparison between Kwang-chih Chang and Su Bingqi
  
| Name | Stage 1 |Stage 2|Stage 3|Stage 4|Stage 5|
|---------|---------|---------|---------|---------|---------|  
|Kwang-chih Chang |Bands: Paleolithic & Mesolithic| Tribes: *Yangshao* Culture|Chiefdoms: *Longshan* Culture |States: *Xia*| -- |
|Su Bingqi |Early cultures (guwenhua) |Early cities (gucheng) | Early states (gucheng): *Hongshan* Culture  |Regional states (fangguo): the proto-Great Wall of the Xiajiadian lower level culture| Empire (diguo): Qin Empire|

 
  Reference:
  (1) Morgan L H, White L A. Ancient society[M]. Belknap Press of Harvard University Press, 1964.
  (2) Hong-Yan Z.From "Chiefdom" to "Original State":the Review for the 20th Century Theories and Patterns about the Origin of the Chinese Civilization[J].Journal of Northwest University(Philosophy and Social Sciences Edition), 2013.
  (3) Su, Bingqi. Zhongguo wenming qiyuan xintan中國文明起源新探 (new investigation of the rise of Chinese civilization). Hong Kong: Shangwu yinshuguan, 1997.
  (4) https://courses.lumenlearning.com/suny-culturalanthropology/chapter/political_anthropology/
  (5)張光直.中国青铜时代[M].生活・讀書・新知三联书店,1999.
