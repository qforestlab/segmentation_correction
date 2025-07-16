# Overview

We’re preparing our individual tree point clouds for segmentation by:

- Importing all point clouds into RiSCAN PRO with the correct CRS  
- Generating crown‐hull shapefiles for each tree  
- Configuring the shapefile in QGIS for manual segmentation

# Methods

## 1. Import Point Clouds into RiSCAN PRO

### 1.a Create a New Project

1. Open **RiSCAN PRO** and click **New Project**.  
   ![Create new project](https://github.com/user-attachments/assets/047abe2c-e552-45ec-9283-60cea157a84c)  
2. Save the project **locally** under a descriptive name.  
   ![Save project](https://github.com/user-attachments/assets/f5c60b46-2ea7-4a8c-9e5d-451cb18ab3d9)

### 1.b Set the Coordinate Reference System

1. In the project manager, select your project name.  
2. Navigate to **Edit → Attributes → Coordinate Reference Systems**.  
3. In the GeoSysManager database, open **NQLD.gfx** and confirm. (You can find the NQLD.gfx file on the australia shares (called `qfl_australia_tls`), if you are working on a different region and using this manual as a guide, make a `.gfx` file for your own UTM Zone by following the steps [here](https://github.com/qforestlab/riscan_registration/blob/main/1.GeoSysManager.md).)
   ![Open NQLD.gfx](https://github.com/user-attachments/assets/b094947c-3642-48bc-86ea-2c8c7ddf38f4)  
4. Apply these settings:  
   ![CRS settings](https://github.com/user-attachments/assets/49655251-ec08-4177-ba84-a049ed6d42db)

### 1.c Import the Point Clouds

1. Right‑click **Objects → Point Clouds** and choose **Import**.  
2. Select **all individual tree point clouds** plus the **leftover** point cloud. (The point clouds can also be found on the qfl_australia_tls shares)
3. Set CRS to **WGS 84 / UTM zone 55 S** (or a different UTM zone, if not Australia), and **disable** “Combine files.”  
   ![Import point clouds](https://github.com/user-attachments/assets/56e13ee1-590f-47d9-8419-dd91619e98a7)  
   ![CRS and combine settings](https://github.com/user-attachments/assets/f3d04ae8-6210-431d-9c71-d55dfcdadf77)

> **Tip:** While the import runs (which can take several minutes), move on to step 2.

## 2. Generate Crown‐Hull Map of Individual Trees

### 2.a Create the Shapefile

1. Open `Get-shape-file-crowns.Rmd` (on the qfl_australia_tls shares, under the folder "scripts").  
2. Update the folder paths to point at the individual‐tree point‐cloud directory (make sure the full plot point cloud is not in the same folder).  
3. Run the RMarkdown in RStudio to produce a shapefile of each tree’s crown hull.

### 2.b Configure the Shapefile in QGIS

1. Open the new shapefile in **QGIS**.  
2. Set the layer CRS to **WGS 84 / UTM zone 55 S** (or a different UTM zone, if not Australia).  
   ![Layer CRS](https://github.com/user-attachments/assets/94a60f0b-de5d-492d-b1c6-e26bc2833be7)

#### 2.b.i Add a “Segmented” Field

1. Open the **Attribute Table**, click **Edit** (pencil symbol), then **Add Field**.  
2. Name the field `Segmented` and choose **Boolean**. 
   
   Some versions of QGIS do not have the option Boolean (see screenshot). In that case, work with an integer and use 0 and 1 for false and true.
   <img width="1588" height="969" alt="image" src="https://github.com/user-attachments/assets/14d34217-8c06-431f-acd6-66aa8ada9ae5" />
3. Also add a field `Notes` and choose **Text** as the type.
4. Save edits and exit editing mode by clicking the pencil symbol again.
   ![Add Segmented field](https://github.com/user-attachments/assets/7463e8b3-0818-434f-8d9d-39df96e7b14a)  
   ![Field values](https://github.com/user-attachments/assets/de5a331c-5d9e-4a6f-bfab-dcfe368c6544)

#### 2.b.ii Style by Segmentation Status

1. In **Layer Properties → Symbology**, choose **Categorized** and select the `Segmented` field.  
2. Click **Classify**, then assign **False/NULL** to red and **True** to green. Set opacity to 50%.  
   ![Symbology settings](https://github.com/user-attachments/assets/4a4f6498-9f6c-497a-8a09-9b500c3dbdce)  
   ![Interim view](https://github.com/user-attachments/assets/6b4051b5-b756-4c28-9885-7c6b333409b5)

#### 2.b.iii Label Trees for Easy Identification

1. In **Layer Properties → Labels**, enable labeling by tree ID.  
2. Adjust font size and placement so labels are legible.  
   ![Label settings](https://github.com/user-attachments/assets/875acf6d-3ded-4fba-8815-6fe6a6d5792b)

You now have a clear top‐down view where each tree is color‑coded by segmentation status and with it's name as label. As you segment a tree, toggle its `Segmented` attribute to **True** to update its color (make sure edit is toggled on as well).  

---
