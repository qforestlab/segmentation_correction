# Overview

We have individual tree point clouds for all 16 plots from Sylvera, generated using RayCloudTools for instance segmentation and QAed by an external company. Our goal is to use these segmented tree point clouds to extract trees from our own full-plot point clouds. This will give us:

- Filtered, individual tree point clouds formatted to our specifications  
- A remaining “leftover” point cloud of non-tree points

# Methods

## 1. Prepare the Point Clouds

### 1.a Select the Plot (20 m Buffer, 1 cm ds)
Follow [Part 4 of the general RiSCAN PRO manual](https://github.com/qforestlab/riscan-general/blob/main/4_select_plot_point_cloud.md) to create a 20 m buffered plot at 1 cm downsampling.

### 1.b Import Point Clouds into RiSCAN PRO
1. In the RiSCAN PRO project of the plot, navigate to `SCANS` and right click on it. Create a new scanposition, you can call it `sylvera_trees` for example.
![image](https://github.com/user-attachments/assets/7335a523-32a0-407e-b389-c74169a4dd4d)
2. Import the desired point clouds (one or multiple) into this scanposition. `Scanposition>Pointclouds` --> right click and **import**.
3. Ensure you select the correct Coordinate Reference System (CRS) during import.
 ![CRS](https://github.com/user-attachments/assets/73a96c07-4030-4fd1-ba09-77db1902fb43)


### 1.c Align Sylvera’s Point Clouds to Our Plot
1. Use Sylvera’s SOP matrix (transformation matrix as a .DAT file) to align their point clouds to our plot. Import the matrix by navigating to the scanposition SOP attributes, right click the matrix and select import. (There is also a lot of info on this in the general RiSCAN PRO manual).
2. Verify the alignment visually. If it is incorrect:  
   - Run automatic registration with the `on failure` setting on.
   - Adjust the pointclouds manually on failure, until the fit is satisfactory
   - After the automatic registration, also run MSA and MSA2 for ultimate precision.
3. Once one (or a few) point cloud(s) is(are) correctly aligned, export the validated SOP matrix.
4. Import all point clouds and apply this SOP matrix for batch alignment.  
5. Finally, export all aligned point clouds with the correct positions.

## 2. Run the Propagation Script

1. Clone or navigate to the [treeseg_propagation repository](https://github.com/qforestlab/treeseg_propagation).  
2. Review the instructions in the README.  
3. The script you need for this propagation is `tree_extraction.py` ([source link](https://github.com/qforestlab/treeseg_propagation/blob/master/tree_extraction.py)).  
4. Set up a Python virtual environment and install the required packages.
5. Run the script.
6. Expect the process to take **1–2 hours** for one plot.

---
