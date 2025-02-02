---
title: "Introduction to QGIS"
subtitle: <h4 style="font-style:normal">CRD 150 - Quantitative Methods in Community Research</h4>
author: <h4 style="font-style:normal">Professor Noli Brazil</h4>
date: <h4 style="font-style:normal">March 9, 2020</h4>
output: 
  html_document:
    toc: true
    toc_depth: 3
    toc_float: true
    theme: cosmo
    code_folding: show
---


<style>
p.comment {
background-color: #DBDBDB;
padding: 10px;
border: 1px solid black;
margin-left: 25px;
border-radius: 5px;
font-style: italic;
}

.figure {
   margin-top: 20px;
   margin-bottom: 20px;
}

h1.title {
  font-weight: bold;
  font-family: Arial;  
}

h2.title {
  font-family: Arial;  
}

</style>


<style type="text/css">
#TOC {
  font-size: 13px;
  font-family: Arial;
}
</style>
\



In this guide you will learn how to use QGIS to make a map.  The objectives of the guide are as follows

1. Gain familiarity with the QGIS interface
2. Load vector and text delimited data into QGIS
3. Joining shapefile and attribute data in QGIS
4. Creating and saving maps in QGIS


<div style="margin-bottom:25px;">
</div>
## **What is QGIS?**
\

QGIS (or Quantum GIS) is an open source geographic information system, meaning that it can be downloaded and installed on your desktop free of charge. It runs on Windows, Mac OS X, and Linux. If you have used ArcGIS before, which all UC Davis affiliates have [free access to](https://itcatalog.ucdavis.edu/service/arcgis-geographic-software), QGIS is very similar except that it has less functionality but is free for everyone and can be used on a Mac without having to rely on a virtualization software program like [Parallels](https://en.wikipedia.org/wiki/Parallels_(company)).  QGIS is not like R in that its data processing and analysis capabilities are more limited.  But, QGIS is, in my opinion, a better program for making a map.  It is quicker to make a map in QGIS compared to R, allows more user efficiency and control over mapping aesthetics, and produces nice looking maps with relatively little cost in time, effort and learning curve.  This is not to say that you **should not** use R for mapping.  If you master spatial R, you can make some really [cool](https://www.r-spatial.org/r/2018/10/25/ggplot2-sf.html) [maps](http://zevross.com/blog/2018/10/02/creating-beautiful-demographic-maps-in-r-with-the-tidycensus-and-tmap-packages/) with R.  But, if you need to **quickly** make a nice looking map, QGIS is a great tool to have in your back pocket.

<div style="margin-bottom:25px;">
</div>
## **Downloading QGIS**
\

You can download QGIS from its official developer [website](https://qgis.org/en/site/forusers/download.html). I generally recommend using the most recent Long Term Release over the most recent version of QGIS.  Long term releases might not have the newest features, but has fewer bugs and is less glitchy than the most recent release. The current long-term release is 3.10. For Windows, this will be labelled **QGIS Standalone Installer Version 3.10**.  For Mac, this will be labelled **QGIS macOS Installer Version 3.10**. 

This tutorial is based on QGIS version 3.10 for Windows.  The guide's instructions should not significantly differ across Mac and PC versions.  However, installation instructions do have some key differences. 

**Windows users**: You will need to choose between the 32-bit or 64-bit versions based on your particular operating system. If you don’t already know which one you have, you can [figure it out](https://support.microsoft.com/en-us/help/15056/windows-7-32-64-bit-faq#1TC=windows-7). 

Installation is pretty simple. Follow these steps:

1. From the QGIS download site, click on the appropriate 32- or 64-bit **QGIS Standalone Installer Version 3.10**

2. Click on the downloaded .exe file.

3. The installation wizard window below should pop up. Click Next.

<center>
![Figure 1: Windows QGIS Installation Wizard](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic1.JPG)

</center>

4. A License Agreement window will pop up.  Click on I Agree.

5. Choose an appropriate location on your hard drive to save QGIS. The default (Program Files) should be fine.

6. Don't alter anything on the Choose Components page.  Just click on Install. Wait a bit for it to install.   A final window will pop up. Click on Finish and you're all good.


**Mac users**: The method for downloading QGIS on a Mac will depend on the version of the operating system (OS) that your computer is running on. To find out your current Mac OS, click on the Apple icon located at the top left of your screen and then select About This Mac.  A window should pop up giving your Mac's current OS.  

If you are running High Sierra (10.13) or newer, follow these simple directions:

1. From the QGIS download site, click on **QGIS macOS Installer Version 3.10** and save the file in an appropriate location.

2.  Click on the downloaded .dmg file

3. Next screen, click on Agree

4. The funky looking screen below should pop up. Click and drag the QGIS3.10 icon to the Applications folder.  After that, you should be all good.

<center>
![Figure 2: Mac QGIS Installation Window](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic2.png)

</center>

If you have an earlier Mac OS version, you'll have to download an earlier version of QGIS. If possible, update to a more recent Mac OS version, as QGIS [no longer fixes](https://blog.qgis.org/2019/03/09/end-of-life-notice-qgis-2-18-ltr/) any bugs for its older versions. However, if you're afraid of updating your OS, click [here](https://qgis.org/downloads/macOS/) to download an older version of QGIS.   You should see all previous versions of QGIS. If your computer is super old, download QGIS 2.18.28.  

Unfortunately, installation for older versions of QGIS is not as simple. Before you run the installer, you’ll need to make sure you can add new software to your Mac. Go to your System Preferences (under the Apple menu), and click on “Security & Privacy”. Click the lock icon in the bottom left to make changes. For the section titled “Allow apps downloaded from:”, Check the “Anywhere” radio button. Now you are ready to install. When you open the disk image that you downloaded, you’ll see the following files. 


<center>
![Figure 3: Mac QGIS Download package](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/image1.png)

</center>

First thing to do is to read the Read Me.rtf file.  You must install Python, GDAL, and QGIS in that order. Installing separate components like this can seem a bit weird if you’re not used to installing open source software.  For 3.4 and later versions, QGIS packaged all of these installations into one quick download. 


<div style="margin-bottom:25px;">
</div>
## **Download Lab Files**
\

We'll be working with Sacramento county tracts in this lab.  Go to the Week 10 Canvas folder and download the zip file qgisdata.zip onto a convenient place on your hard drive that you can readily access. Unzip the folder. The folder will contain the following shapefiles and csv files.

* Sacramento_County_Tracts.shp
* tract_demographics.csv

<div style="margin-bottom:25px;">
</div>
## **QGIS Interface**
\

Open up QGIS.  You should see an interface similar to Figure 4.

<center>
![Figure 4: QGIS Interface.](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture2.jpg)

</center>

The components of the interface are as follows

1. *Main Menu*: Provides access and functions of the applications in a standard pull down menu format.  
2. *Toolbars*: Buttons that provide one click access to many of the features and functions found in the Main Menu. Toolbars are movable and can be docked or free floating. You can also customize what toolbars to show by right clicking (on a Windows machine) or Ctrl + clicking (on a Mac laptop) on one of the toolbars and selecting/deselecting from the menu.
3. *Browser Panel*: Shows a listing of files on your computer. You can drag and drop GIS files into the Layers Panel (4) to view them.  
4. *Layers Panel*: Shows a listing of map layers and data files that are in your current project.  Layers can be turned off and on, change drawing order, etc.  Think of this as a Table of Contents.
5. *Map Display Panel*: Shows a geographic display of GIS layers in the Layers panel.
6. *Status Bar*: Shows the current scale of the map display, coordinates of the current mouse cursor position, and the coordinate reference system (CRS) of the project.  In this guide, we won't worry too much about this bar.

<div style="margin-bottom:25px;">
</div>
## **Bringing in a shapefile**
\

Let's bring in the shapefile of Sacramento county tracts.  This is like `st_read()` in R. You can bring in a shapefile in one of the following ways.

1. Select Layer in the Main Menu panel and scroll over Add Layer. You'll find the various types of files you can bring into QGIS.  Clicking on Add Vector Layer... to add a shapefile.
2. Select Layer in the Main Menu panel and select Data Source Manager.  This will bring up a screen (Figure 5) that will allow you to add files.
3. You can bring up the Data Source Manager by also clicking on ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture3.jpg) typically located in the Toolbars menu.
4. You can add a shapefile by clicking on the ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic4.JPG) button, typically located in the Toolbars menu.

Let's use the Data Source Manager approach. When you open up the Data Source Manager, you should get the following window

<center>
![Figure 5: Data Source Manager](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic3.JPG)

</center>

We want to bring in a shapefile showing Census tracts in Sacramento county.  Tracts are polygon or areal data, also known as Vector data. From the Data Source Manager window, follow the steps outlined below.

1. Select  ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture5.jpg) on the left panel. This should bring a screen shown in Figure 6.

<center>
![Figure 6: Adding Vector Data](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic6.JPG)

</center>

2. Under Source and next to Vector Dataset(s), click on ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture17.jpg) at the far right.  
3. Navigate to the folder containing the files you downloaded from Canvas.  Select the file "Sacramento_County_Tracts.shp".  To be clear, you will see a bunch of files named "Sacramento_County_Tracts".  Double click on the one highlighted in red in Figure 6.  
\

<center>

![Figure 6: Click on the shapefile](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture18.jpg)

</center>


4. Click on the Add button ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture7.jpg) and close the Data Source Manager.  You should see tracts in Sacramento county pop up (Figure 7). It may have come in as a different color. 

<center>
![Figure 7: Sacramento county tracts](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic7.JPG)

</center>

<div style="margin-bottom:25px;">
</div>
## **Bringing in a csv file**
\

We got a shapefile into QGIS. Hooray for us! Let's now map a variable by bringing in some data to map. Bring up the Data Source Manager and follow the steps below to bring in a csv file into QGIS.  This is like `read_csv()` in R. The file contains tract-level percent Hispanic (phisp) and percent poverty (ppov).

1. Click on ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture9.jpg).  The window shown in Figure 8 should pop up on the right of your screen.

<center>
![Figure 8: Adding data window](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic8.JPG)

</center>

2. Click on ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture17.jpg) located at the far right next to the File Name box. We are going to bring in a csv (comma delimited) file containing tract-level percent Hispanic and percent poverty for the United States.  These data are located in the file tract_demographics.csv.  Navigate to the folder containing that file and double click on it.  
3. Leave all the default settings alone.  However, click the arrow for Geometry definition and make sure the radio button next to No geometry (attribute only table) is checked.  Your final setup should look something like Figure 9.

<center>
![Figure 9: Bringing in a csv file](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic9.JPG)

</center>

4. Click on Add and then Close.  The file tract_demographics should pop up in your Layers panel above Sacramento_County_Tracts like in Figure 10.

<center>
![Figure 10: Layers panel](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture11.jpg)

</center>

<div style="margin-bottom:25px;">
</div>
## **Joining a csv to a shapefile**
\

We now want to join (merge) the csv data (tract_demographics) to the shapefile (Sacramento_County_Tracts).  This is `left_join()` in R. To do this, follow the steps below.

1. Right click on the Sacramento_County_Tracts file in the Layers panel.  You should get a menu like in Figure 11.

<center>
![Figure 11: Right click on a layer](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture12.jpg)

</center>

2. Click on Properties. 
3. Click on the Joins button ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture13.jpg).  A window should pop up that looks like Figure 12.  


<center>
![Figure 12: Layer properties](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic10.JPG)

</center>

4. Click on ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture14.jpg) located at the bottom.  The Add Vector Join window below should come up.

<center>
![Figure 13: Add Vector Join](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic11.jpg)

</center>

5. From the Join layer pull down menu, select tract_demographics (if it isn't already selected for you).  
6. Under Join field, select GEOID.
7. Under Target field, select GEOID. We are joining the data from tract_demographics to Sacramento_County_Tracts using a common ID field - named GEOID in tract_demographics and GEOID in Sacramento_County_Tracts.  
8. Check the Custom field name prefix box - a white box should pop up underneath - delete the text (tract_demographics_).  If we did not do this, the variables phisp and ppov will be named tract_demographics_phisp and tract_demographics_ppov in the Sacramento_County_Tracts file, which are too long.  By deleting it, we'll keep the names to phisp and ppov.

9. The Add Vector Join window should look like Figure 14.  Click OK. Click OK again in the next screen.

<center>
![Figure 14: Add Vector Join Settings](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic12.jpg)

</center>

To verify that the join worked, you can open up the attribute table for the shapefile. An attribute table consists of rows representing spatial features (census tracts), and columns representing properties or characteristics of the spatial feature (e.g. percent Hispanic). It's a nonspatial dataset attached to the spatial dataset. To bring up the attribute table, you can either

1. Right click on Sacramento_County_Tracts and select Open Attribute Table or  
2. Select Sacramento_County_Tracts. From the Toolbars menu, click on the Layers panel and then select Open Attribute Table

The table should pop up and contain 317 rows corresponding to the 317 tracts we have displayed on the map screen. See Figure 15. Scroll all the way right - you should see the variables we added from tract_demographics: ppov (percent poverty) and phisp (percent Hispanic).

<center>
![Figure 15: Attribute table](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture16.jpg)

</center>

<div style="margin-bottom:25px;">
</div>
## **Saving a shapefile**
\

Joining data to the shapefile is not permanent.  If you close QGIS, reopen it, and bring in Sacramento_County_Tracts, you will find that phisp and ppov are no longer in the attribute table.  You will need to save a new shapefile to make this join permanent. This is like `st_write()` in R.  To save a shapefile, follow the steps below.

1. Right click on Sacramento_County_Tracts
2. Select Export and then select Save Features As. A Save Vector Layer as... window should pop up.  
3. For Format, select ESRI Shapefile.  
4. For File name, select ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture17.jpg) and navigate to the folder you want to save the new shapefile.  Give your new file the name "Sacramento_County_Tracts_Dems.shp". Click Save.
5. Keep everything else the same.  You should have a window that looks like Figure 16. Click OK.  

<center>
![Figure 16: Saving your shapefile](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic13.jpg)

</center>

6. The window Coordinate Reference System Selector may pop up next.  It will ask you to select the appropriate Coordinate Reference System (CRS).  Under Coordinate reference systems of the world, there should be a window in which you can scroll through to find an appropriate CRS.  The CRS NAD_1983_2011_UTM_Zone_10N should already be selected because that is the CRS for the original shapefile Sacramento_Country_Tracts.  No need to change, so just select OK.

You should see Sacramento_County_Tracts_Dems pop up in your Layers panel. It should also pop up in the Map Display window in a different color. Because we only need this shapefile moving forward, remove tract_demographics and Sacramento_Country_Tracts by right clicking on each from the Layers panel and selecting Remove Layer. You can also click on the layer you want to remove and select ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic32.jpg), which is located top right of the Layers panel. 

<div style="margin-bottom:25px;">
</div>
## **Making a map**
\

Let's map percent poverty at the tract level for the county of Sacramento. This is like `tm_shape()` or `ggplot()` in R.  The first thing to do is to symbolize the map based on percent poverty.   

1. Right click on Sacramento_County_Tracts_Dems and select Properties.  
2. Select the Symbology button ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture23.jpg) on the left panel.   
3. From the top pull down menu, select Graduated (the default should be Single symbol). A graduated map relates values to color gradients on a map; each color gradation corresponds to a specific interval of  values.  
4. We want to map percent poverty. From the Value pull down menu, select ppov
3. Leave Symbol alone. In Legend Format, reduce the precision down to 2 (this will show percent poverty in two decimal points in the legend)
5. You can select whatever color scheme you would like using the pull down menu from Color ramp.  I kept it at the default - a graduated color scheme of white to dark red.
6. The Mode near the bottom of the window tells QGIS how to break up the values.  Remember from Lecture that you can easily distort your data by choosing different break values.  Select Quantile (Equal Count) and keep Classes to 5. This will break up the values by quintile (bottom 20%, 20% to 40%, 40% to 60%, 60% to 80%, and top 20%).  Click on Classify.
7. The final setup should look like Figure 17. Click OK.

<center>
![Figure 17: Symbology setup](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic14.jpg)

</center>

You should get something that looks like Figure 18.  

<center>
![Figure 18: Map showing percent poverty in quintiles](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic15.jpg)

</center>

<div style="margin-bottom:25px;">
</div>
## **Using Map Layout Manager**
\

We've symbolized our map, but now we want to create and save a map for presentation purposes. QGIS has a powerful tool called Layout Manager that allows you to take your GIS layers and package them to create and save pretty maps.  Why do we need this tool?  A GIS map file is not an image. Rather, it saves the state of the GIS program, with references to all the layers, their labels, colors, etc. So for someone who doesn’t have the data or the same GIS program (such as QGIS), the map file will be useless.

To create a map, follow the steps below.

1. From the Main Menu go to Project and click on New Print Layout.  A dialog box will pop up asking you for a title - type in "Percent Poverty by Census Tract in Sacramento County". Click OK.

<center>
![Figure 19: Map title](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic16.jpg)

</center>

You should see a screen that looks like Figure 20 pop up.  This is the Map Layout screen.

<center>
![Figure 20: Map layout screen](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic17.jpg)

</center>

Let's go through each component of the Layout screen

1. *Main menu*: Provides access and functions of the applications in a standard pull down menu format.
2. *Toolbars*: There are toolbars located at the top and the left of the screen.  These toolbars provide buttons to perform various functions.  Right click to choose which toolbars to show
3. *Map window*:  This is where your map will be displayed.  This includes legends, labels, titles, scale bars, north arrows, and other map accouterments.
4. *Items and History*: This window provides two basic pieces of information: (1) what items are on your map (for the items you can add to your map, look at the menu Add Item from the main menu).  Think of this as a table of contents.  (2) all the actions you've done to your map.   This can be simple actions like moving the legend around.  
5. *Layout and properties*: This window provides the properties of a selected item on your map.  This is where you can change the appearance of any item on your map.  For example, you can change the size of your legend font.  The item whose properties you are viewing is listed at the top of this window - for example, if you are adjusting the legend, it will say Legend at the top of this panel.  
\

6. To add our map, select Add Item from the Main Menu of the new screen and select Add Map.  

7. Nothing should happen.  However, your mouse cursor should look like a black cross.  Move your cursor to the top left corner of the white canvas and drag it to the bottom right corner to create a rectangle.  See Figure 21.

<center>
![Figure 21: Adding your map](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic18.jpg)

</center>

The map of Sacramento county maps should pop up.  With the map now displayed, you can

* Move the map by clicking and dragging it around
* Resize it by clicking and dragging the boxes in the corners
* Add map details such as a legend and title.


8. The scale and extent of the map shown in the Map Layout will match what is shown in the main interface. The extent controls movement West, East, North and South.  Scale controls zooming in and out. Toggle back to the main QGIS interface. If you want to make the map bigger or smaller in the Map Layout window, you can change the scale from the Status bar in the main interface.  For example, the current scale I have in the main interface is ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture26.jpg).  I can zoom in a little more - I can do this by using the ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture27.jpg) tool or just type a scale in directly to the scale box.  I do the latter by typing in, for example, 1:300000 and pressing enter.

9. Toggle to the Map Layout window. You will notice that nothing has changed. The scale in the Map Layout window will **not** update - you will have to do it manually.  Click anywhere on your map in the Map Layout window. On the right  panel of the window, click  Item Properties, click on the button ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/qgisextent.png).  See Figure 22. 

<center>
![Figure 22: Set to map canas extent](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic19.png)

</center>

If you move the position of Sacramento West, East, North or South in the main interface, you update the Map Layout by clicking on the Set Map Extent to Match Main Canvas Extent button ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/mapextent.png)

10. You should see Sacramento county fills up the page a little more.  See the figures below for the difference.  If your map is still too small or became too large, change the scale again.  Higher values mean the map zooms out.

<center>
![Figure 23: Scale of 1:350912](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic20.jpg)

</center>

<center>
![Figure 24: Scale of 1:300000](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic21.jpg)

</center>

<div style="margin-bottom:25px;">
</div>
### **Add a legend**
\

A legend is an essential feature in a map.  To add a legend, follow the steps below.

1. Click on Add Item from the Main Menu of the Map Layout window  
2. Click on Add Legend.  
3. A cross cursor will pop up, which means you'll need to click, hold and drag to the place where you want to place the legend. See Figure 25.

<center>
![Figure 25: Adding a legend](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic22.jpg)

</center>


If you want to customize the legend, click anywhere on the legend, and in the right panel under Item Properties a window named Legend should now be there.  The panel provides different settings that you can alter to customize how the legend looks.  For example, double click on Sacramento_County_Tracts_Dems under Legend items. 

<center>
![Figure 26: Legend items in Layout screen](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture32.jpg)

</center>

This should bring up a little dialog box which allows us to give the legend a more descriptive title.  Delete the current title "Sacramento_County_Tracts_Dems" and type in a more descriptive title, such as "Percent Poverty".  You can change the font size and color by altering the properties under Fonts. 

<div style="margin-bottom:25px;">
</div>
### **Add a scale bar**
\

A scale bar is an important component of a map because it gives the viewer a visual indication of the size of features, and distance between features, on the map.  To add a scale bar

1. Click on Add Item from the Main Menu of the Map Layout window  
2. Select Add scale bar.  
3. Click, hold and drag to place your scale bar, usually somewhere in the bottom right or left of the map.  

Similar to legend, the scale bar properties should pop up in the bottom right panel.  You can change its properties, for example going from Kilometers to (the US centric) miles and adding more segments. Here are a few changes we can implement:

1. Change kilometers to miles by selecting Miles under the Scalebar units menu.  
2. Add additional segments to lengthen the bar by increasing "right 2" to "right 4" under Segments. 
3. Make sensible scale breaks by typing in 10 next to Fixed width. 

So far, here's what the map looks like.

<center>
![Figure 27: Map with legend and scale bar](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic23.jpg)

</center>

<div style="margin-bottom:25px;">
</div>
### **Add a North arrow**
\

Adding a north arrow improves many maps, especially large-scale maps that show a smaller area in great detail and maps that are not oriented with north at the top.  To add a north arrow

1. Click on Add Item from the Main Menu of the Map Layout window  
2. Select Add North Arrow  
3. Click, hold and drag to place the arrow, usually in one of the corners.  
4. Just like with the map, legend and scale, you can modify the picture's properties from the panel on the right of the Map Layout window. From this panel. scroll down a little until you see Search directories - click on the arrow and you should see some preloaded images pop up (Figure 28)

<center>
![Figure 28: Picking a north arrow](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture34.jpg)

</center>

5. If you don't like the default arrow, select your favorite image.  

After selecting it, you can customize as you see fit.  For example, I kept the default arrow ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic24.jpg) but altered the properties to make it look like ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/Capture39.png)

How did I make the arrow look like this? 

1. Under Main properties, I selected Middle in the Placement pull down menu to center the arrow.  
2. I selected black in the pull down menu next to Fill color under SVG Parameters to make the arrow black.  

<div style="margin-bottom:25px;">
</div>
### **Add a title**
\

You can't have a map without a descriptive title.  Let's add one.

1. Under Add Item from the Main Menu of the Map Layout window, select Add label.  
2. Click, hold, drag a rectangle across the top of the map.  
3. Very tiny text will pop up - it says "Lorem ipsum", a common [placeholder text](https://en.wikipedia.org/wiki/Lorem_ipsum).  In the right panel, under Item Properties, a Label panel should have popped up.  Under Main properties, delete the text "Lorem Ipsum" from the white text box and add an appropriate title (I used "Tract Percent Poverty in 2016, Sacramento County").  

As with all features, you can customize the title as you see fit. For example, staying in Item Properties, under Appearance, I 

1. Clicked on the Center radio button under Horizontal alignment and the Middle radio button under Vertical alignment to center the title. 
2. Clicked on the pull down menu directly under Appearance and increased the font size to 25. You might have to increase the title box to show the title now that you've increased its size.

If you need room at the top to fit the title, you'll need to adjust the scale or extent from the main interface.  My map now looks like Figure 29. Looks nice, right? Of course.

<center>
![Figure 29: Map with the accoutrements](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/qgisfinalmap1.jpeg)

</center>

<div style="margin-bottom:25px;">
</div>
### **Add a basemap**
\

Right now, it looks like Sacramento county is floating in space. There's nothing necessarily wrong with this - check this gallery of [QGIS maps](https://www.qgis.org/en/site/about/screenshots.html) or even do a basic Google search of Sacramento poverty map and you'll find plenty of maps without context.  But, we can provide some context to the map by adding a background.  We can do this by adding a base map.

A base map provides geographical context to a region of interest. For example, a base map might help viewers orient themselves to a specific county by displaying the surrounding counties. QGIS  has a few preinstalled basemaps that you can add to your map. Let's add an [OpenStreetMap](https://www.openstreetmap.org) basemap.  OpenStreetMap is a free editable crowdsourced map of the world.  

In the Browser window  on the main interface, click on the arrow next to XYZ Tiles. The option OpenStreetMap should show up. 


<center>
![Figure 30: Selecting OpenStreetMap basemap](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic31.jpg)

</center>


Double click on OpenStreetMap.  The OSM basemap should pop up both in the Map and Layout views. You'll see that these tracts are obscuring the Sacramento_County_Tracts_Dems layer.  Change the layer order by clicking, holding and dragging the OpenStreetMap layer below Sacramento_County_Tracts_Dems in the Layers panel (or move the Sacramento_County_Tracts_Dems layer above).  

<center>
![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic27a.png)

</center>

<center>
![Figure 31: Changing the ordering through the Layers panel](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/pic26a.png)

</center>


You should see your symbolized map of Sacramento county tract poverty pop up.  

Go back to the Map Layout window. You will notice that the OpenStreetMap layer was added to the legend. To take it out

1. Click on the legend. This should bring up the Legend properties on the right panel. 
2. Scroll down to Legend Items and unclick Auto Update ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/autoupdate.png).  
3. In the Legend Items window, click on the OpenStreetMap layer. 
4. Below the Legend Items window, click on ![](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/legenddelete.png). The OpenStreetMap layer should no longer be in the legend.

You can further customize the map as you see fit.  I ended up with the map shown in the figure below.

<center>
![Figure 32: Map with OpenStreetMap basemap](/Users/noli/Documents/UCD/teaching/CRD150/Lab/crd150.github.io/qgisfinalmap.jpeg)

</center>

You can add other freely available basemaps like Google Maps. For more details on how to do this, read this informative [blog post](https://geogeek.xyz/how-to-add-google-maps-layers-in-qgis-3.html).

<div style="margin-bottom:25px;">
</div>
## **Saving your map**
\

Ultimately, you'll want to share this map with others.  You usually do this by sharing it as a jpeg or pdf. If you save it as a jpeg, you can paste it into a word document or PowerPoint presentation. To export your map

1. Select Layout from the Main Menu of the Layout view. 
2. Select either Export as Image or Export as PDF. 
3. Save the file with an appropriate name in the appropriate folder.  

<div style="margin-bottom:25px;">
</div>
## **Saving your project**
\

When saving a project you are not saving actual data files.  That is, you are not saving Sacramento_County_Tracts_Dems.  Project files do not contain maps, instead they contain information on where original shapefiles are stored and what processes are needed to recreate a map. A saved project file includes information about the path to each data layer included as well as your choices about symbology, labels, and layer order.  Before closing QGIS, users should save their progress in a Project file so it can be used and edited in the future. It is important to note that all shapefiles associated with the map must stay in the same location when you first created the map. If they are moved, QGIS will not be able to locate the files and rebuild the map.  To save a project

1. From the Main Menu of the main interface, select Project
2. Select Save
3. Navigate to the folder that contains the data you've uploaded into your current project. Type in an appropriate name and select Save.

The project file will be saved as a `.qgz`, which can be only opened in QGIS.

<div style="margin-bottom:25px;">
</div>
## **More Resources**
\

This tutorial scratches the surface of what you can do with QGIS.  You can get more practice by using the official QGIS training manual [here](https://www.qgis.org/en/docs/index.html).  They also have a more [Gentle Introduction to QGIS](https://docs.qgis.org/testing/en/docs/gentle_gis_introduction/)


Because QGIS is open source like R, this means users can create and add to QGIS' basic functionality.  These additions come in the form of plugins.  A list of all available QGIS plugins can be found [here](https://plugins.qgis.org/).  

To add a plugin

1. Select Plugins from the main menu
2. Select Manage and Install Plugins.  
3. In the text box at the top of the window that pops up, type in a search keywords, plugins matching your search will pop up below.  
4. Click on the plugin and hit Install.  

And by now, most of you are aware of StackExchange, a network of Q&A communities.  QGIS has its own StackExchange community, which you can find [here](https://gis.stackexchange.com/questions/tagged/qgis)

***

<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.


Website created and maintained by [Noli Brazil](https://nbrazil.faculty.ucdavis.edu/)
