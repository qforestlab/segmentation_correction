# Overview

In this step, we correct any missing points in each individual tree point cloud in RiSCAN PRO using the QGIS crown‐hull map. The process covers:

- Loading your project and QGIS map  
- Identifying and isolating a single tree point cloud  
- Adding missing trunk or branch points  
- Saving the corrected tree point cloud  
- Exporting all corrected point clouds at the end

---

# Methods

## 1. Load the Project and QGIS Map

1. Open your RiSCAN PRO project and the QGIS project you created in **02_prep**.  
2. In RiSCAN PRO, display **all** point clouds (individual trees + leftover) in single‑color mode.  
3. Color the leftover cloud in a distinct hue (e.g., dark maroon or height‑based coloring) so it stands out.  
4. Click the “bird” (top‑down) view icon to align your screen with the QGIS map.  
   ![RiSCAN PRO view](https://github.com/user-attachments/assets/4e29cedc-a930-47e9-a9a0-32bc3971afdc)  
5. Based on the QGIS map and the point clouds, select your target tree. In the following example the green tree was chosen as the target tree. Thanks to the QGIS hull map, it was easy to figure out that it is tree number 369460_8074920_08.  
   ![RiSCAN target tree](https://github.com/user-attachments/assets/a9bd0f49-5fb5-4827-a345-daa5a6c7383c)  
   ![QGIS map](https://github.com/user-attachments/assets/88194c10-0911-4135-8fb8-0ddb544c6352)  
6. If necessary, change the colours of the point clouds for good visibility. In this example, the leftover point cloud colour was changed to height‐above‐ground (blue shades) and the target tree to bright yellow.

## 2. Isolate a Single Tree

1. **Select** an area that fully encloses the target tree (including any missing bits).  
  
2. Now you have two options:
   - **_(NEW!)_** **Lock** the target tree (the lock icon) and click **Show Selected** (arrow on image). ![Selection area](https://github.com/user-attachments/assets/48a5680a-4583-4378-8be3-afe94ccafa99) It will show only the selected area while the locked tree will stay selected (red colour). 
   - Other option:
      - Click **Show Selected** (arrow on image), alas, you forgot to lock the tree beforehand... :(
      - In the Object Inspector, **lock** the target tree (the lock icon)—this won’t affect the next steps but makes it easy to re‑find the tree.
      - Go to **Point Clouds** in the Object Inspector, right‑click and choose **Hide All**. Everything will disappear from the view.
      - Find your locked tree (golden lock icon), unlock it, then click the cloud symbol to **Show** it.
         ![Show single tree](https://github.com/user-attachments/assets/94c84807-45f9-495b-9843-0af99b6c9741)
      - Use the selection tool to select the target tree.
      - Once done, in Object Inspector, right‑click **Point Clouds → Show All** to show the surrounding area again.  
 
> Now the target tree is selected, with its surrounding area visible.  
![Isolated tree view](https://github.com/user-attachments/assets/0916bb65-342f-43f9-a358-01f481ef1939)

## 3. Add Missing Pieces

1. Apply the **Height Filter** (image below, indicated with red arrows).  
2. Starting at the bottom of the target tree, go through the tree looking for missing parts.  
   <img width="3827" height="2088" alt="435991877-7e837ddd-c839-4328-823a-898f9082a0b8" src="https://github.com/user-attachments/assets/c4ff6073-c13c-4212-a637-9e934bfa0f4d" /> 
3. Select the missing trunk sections, large branches, or stem growth features.  
   - You can skip isolated floating points or very small twigs unless they affect height or crown area.  
   - For example: The darker red branches were missing and selected.  
     ![Select missing branches](https://github.com/user-attachments/assets/06389ec4-ace8-4a23-94c7-f5396da48261)  
4. When finished scanning from bottom to top, click **Show Selected**.  
5. Inspect your selection for mistakes (e.g., stray points from neighboring trees).  
   - It’s often faster to include extra points and then remove outliers in this step.  
   - For example: the points circled in red will be removed later.  
     ![Remove outliers](https://github.com/user-attachments/assets/d822a88f-8655-4947-a9e3-d2f60cba3472)

## 4. Save the Corrected Tree Point Cloud

1. Once finished, select the full tree.  
   ![Full-tree selection](https://github.com/user-attachments/assets/b50dbbce-902e-4473-b96e-1de5ae2ca3da)  
2. With your full‑tree selection active, click **Copy Selection with Filter Settings** (cloud icon dropdown).  
3. In the dialog:  
   - **Enable** “Move to new file” (not “Copy To”)  
   - **Enable** “Combine data”  
   - Rename the point cloud to the correct tree ID (output name)  
   - Ensure **all point attribute options** are selected  
   ![Copy settings](https://github.com/user-attachments/assets/a3fd19c9-7060-4719-b7a6-d9b1f41d95e3)  
4. Click **OK**, then **Show All** to restore the full project view.  
   ![Restore view](https://github.com/user-attachments/assets/66fec52d-449e-4bad-a208-5a7bc1a99dee)  
5. In your QGIS map, toggle the tree’s `Segmented` attribute to **True**.  
   ![Toggle segmented](https://github.com/user-attachments/assets/b566e314-5415-4c1c-9e5c-e893f20b3b01)

## 5. Repeat for Each Tree

Repeat steps 2–4 for every tree in the plot until all individual clouds are corrected. 
To make sure no work is lost if you work locally, save the individual point clouds along the way by moving on to step 6.2 and 6.3.

## 6. Export All Point Clouds

Once you’ve corrected every tree in the plot:

1. Inspect the **leftover** point cloud for any large stray branches—add them back to the correct individual tree point cloud if needed.  
2. In RiSCAN PRO’s Project Manager, select **all** corrected tree clouds.  
3. Export them: create a folder `Exports/Pointclouds` in the RiSCAN project, then save the point clouds as LAS files with the following settings:  
   ![Export settings](https://github.com/user-attachments/assets/6dd63e4e-0af2-486e-a8c5-10a3b2c4ff36)

---
