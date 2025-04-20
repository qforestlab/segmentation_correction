# Segmentation preperation
## 1. Select trees within AOI (40x90m)
For this step run all scripts in order from the [plot_selection repository](https://github.com/qforestlab/plot_selection).

## 2. Import pointclouds in RiSCAN PRO.
### 2.a Open RiSCAN PRO and click "New Project".
![image](https://github.com/user-attachments/assets/047abe2c-e552-45ec-9283-60cea157a84c)
Save the project locally with an appropriate name.
![image](https://github.com/user-attachments/assets/f5c60b46-2ea7-4a8c-9e5d-451cb18ab3d9)

### 2.b Adjust the CRS
Click the project name on the left, go to Edit>Attributes>Coordinate Reference Systems.
Open the NQLD.gfx file in GeoSysMnnager database file and click "yes". The file will be on the shares
![image](https://github.com/user-attachments/assets/b094947c-3642-48bc-86ea-2c8c7ddf38f4)
Set the settings to this:
![image](https://github.com/user-attachments/assets/49655251-ec08-4177-ba84-a049ed6d42db)

### 2.c Import the pointclouds
Right click Objects>Pointclouds and click on "import".
Select all the individual trees and the leftover pointcloud.
![image](https://github.com/user-attachments/assets/56e13ee1-590f-47d9-8419-dd91619e98a7)
Make sure to select WGS84 / UTM zone 55S as a CRS and toggle off "combine files".
![image](https://github.com/user-attachments/assets/f3d04ae8-6210-431d-9c71-d55dfcdadf77)

It might take some time importing all pointclouds, you can continue with the next step while this is running.

## 3. Make hull map of individual trees.
### 3.a Make a map of the crown hulls of the individual trees.
For this step, you have to run the Get-shape-file-crowns.Rmd file (on the shares). 
Change the folder paths to where all the individual tree pointclouds are.

### 3.b Open the shapefile in QGIS
You will have to set the layer-CRS to UTM ZONE 55S.
Your map should look simple like this:
![image](https://github.com/user-attachments/assets/94a60f0b-de5d-492d-b1c6-e26bc2833be7)

We will now change some settings to make the segmenting easier.

Go to attribute table, toggle the edit button and select "add field". 
Now add a column called "Segmented" and make it boolean.
![image](https://github.com/user-attachments/assets/7463e8b3-0818-434f-8d9d-39df96e7b14a)

All trees should automatically have value NULL, that's fine you can leave it like this.
![image](https://github.com/user-attachments/assets/de5a331c-5d9e-4a6f-bfab-dcfe368c6544)

Click save and toggle the edit button off again.
Close the attribute table and double click the layer to open it's settings.

Set the symbology to "categories", select "segmented" as it's value and click "classify".
Now set the colours for False and other to red and true to green. Set the opacity to 50%.
![image](https://github.com/user-attachments/assets/4a4f6498-9f6c-497a-8a09-9b500c3dbdce)

You get something like this when in the process of segmenting:
![image](https://github.com/user-attachments/assets/6b4051b5-b756-4c28-9885-7c6b333409b5)

Now go to labels and set them to the following settings (or whatever is readable for you):
![image](https://github.com/user-attachments/assets/875acf6d-3ded-4fba-8815-6fe6a6d5792b)

Now you have a top view of the trees and you can easily figure out which tree is which while you are segmenting. Whenever a tree is segmented, you toggle the attribute table to true to change it's colour.

