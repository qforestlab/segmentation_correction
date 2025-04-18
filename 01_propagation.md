# Overview
We have individual tree pointclouds for all 16 plots that we got back from Sylvera. They used Raycloudtools for instance segmentation.
We will use the pointclouds we got from them to extract the trees from the full plot pointcloud. That way we have the individual tree pointclouds that are filtered the way we prefer, as well as a leftover pointcloud.

# Methods
## 1. Prepare the pointclouds
### 1.a Select the plot with 20m buffer & 1cm ds
Look at [part 4 of the general RiSCAN PRO manual](https://github.com/qforestlab/riscan-general/blob/main/4_select_plot_point_cloud.md) for this.

### 1.b Import the pointclouds
In RiSCAN PRO, make a new scanposition in which you import a few or all of the pointclouds. Make sure to import in the correct CRS. 

### 1.c Align pointclouds from Sylvera with our plot
You can use the transformation matrix Sylvera gave us for this. However, make sure to check if this is correct. If not, align the pointclouds using MSA and manually adjust on failure.
If you worked with some of the pointclouds for clearer view, you should now have a correct SOP matrix which you can export. Now load all pointclouds and use the correct SOP matrix to align all the pointclouds. 

Now you can export all the pointclouds with the correct position.

## 2. Run the propagation

