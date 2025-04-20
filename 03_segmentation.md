# Segmentation correction
## Open the project and QGIS map you made in 02_ 
Put all the pointclouds (individual + leftover) in the view and put on single color mode.
Put the leftover pointcloud in a colour, that is clearly visible to you (e.g. dark maroon colour that is not used in the single color mode or color the points based on height above ground).

Click on the bird symbol to view the pointclouds from the top. You can now easily compare the view to the QGIS map. Based on this, it's easy to find out which tree is which.

## Select the tree
Select an area around the tree, that involves the tree itself and all missing parts. Click show selected.
In object inspector, lock your tree, this will not do anything but helps you to find back the tree of your selection easier in latter steps.
Now go to pointclouds in object inspector, right click and select hide all. Everything dissapeared.
Now go back to your tree (easy to find due to the golden lock symbol), unlock it, right click on the pointcloud and click show.
Using the selection tool, select the tree. 
Go back to object inspector>pointclouds, right click and choose show all.

Now you see your selected area, with only the tree that you are segmenting corrected.

## Select missing pieces
Use the height filter, to show parts of the tree and it's surrounding area from the bottom to the top. 
You can easily select the parts that are missing using the filter. Add back in parts of the tree trunk, large missing branches, larger stem growth. 
If you want to work faster, feel free to ignore floating points or small branches. Just make sure that everything that can make a significant difference in tree height or crown area is added back in.
When you went through the entire tree from bottom to top, click "show selected". 
Now check for any mistakes; floating points, branches that do belong to other trees... I have found that it is easier to add back to much and delete what not belongs to the tree again in this step.

## Save the new pointcloud
Now that you have the original pointcloud together with it's missing pieces, select everything using the selection tool. 
Click the copy selection with filter settings (cloud symbol, drop down)
toggle "move to" NOT "copy to"
Change the pointcloud name to the correct name
select all the data options
click save
click show all 

Don't forget to toggle the segmented attribute in the QGIS map.

You can now start over with the next tree.


## Export all pointclouds
If you managed to go over an entire plot.
Check the leftover pointcloud for any large branches. If everything looks good, select all the newly made pointclouds in the project manager and export them.
