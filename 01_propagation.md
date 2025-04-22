# Overview

We have individual tree point clouds for all 16 plots from Sylvera, generated using RayCloudTools for instance segmentation and QAed by an extarnal company. Our goal is to use these segmented tree point clouds to extract trees from our own full-plot point clouds. This will give us:

- Filtered, individual tree point clouds formatted to our specifications  
- A remaining “leftover” point cloud of non-tree points

# Methods

## 1. Prepare the Point Clouds

### 1.a Select the Plot (20 m Buffer, 1 cm ds)
Follow [Part 4 of the general RiSCAN PRO manual](https://github.com/qforestlab/riscan-general/blob/main/4_select_plot_point_cloud.md) to create a 20 m buffered plot at 1 cm downsampling.

### 1.b Import Point Clouds into RiSCAN PRO
1. In RiSCAN PRO, create a new scanposition.  
2. Import the desired point clouds (one or multiple) into this scanposition.  
3. Ensure you select the correct Coordinate Reference System (CRS) during import.

### 1.c Align Sylvera’s Point Clouds to Our Plot
1. Use Sylvera’s SOP matrix (transformation matrix) to align their point clouds to our plot.  
2. Verify the alignment visually. If it is incorrect:  
   - Run MSA 
   - Adjust the SOP matrix manually on failure, until the fit is satisfactory  
3. Once one point cloud is correctly aligned, export the validated SOP matrix.  
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
