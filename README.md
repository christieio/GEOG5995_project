# GEOG5995_project
Independent Project Assignment

This respository of code contains the python code for the independent project as part of the Leeds GEOG5995 module. The code follows the 'White Star Line' project. This project is part of an introductary course in order to learn the python programming language. This particular project is independent and the code has been written by myself following the guidelines for the White Star Line project.

What the model does:
The model pulls in and reads two files: lidar and radar data that show the height and area of an iceberg respectively. The model uses this data creates a visual plot that shows the coordinates and corresponding heights at each coordinate when hovered over with a mouse. 

The model loops through the files to return all the coordinates where there is ice above sea level and the corresponding heights for each coordinate. Each coordinate represents a m*2 area. The model calculates the total volume of ice that is above sea level. This volume is then used to calculate the mass of the iceberg above sea level. As the instructions informs us that 10 percent of the icebergs mass is above water, the model is able to calculate the total mass of the iceberg by * the result by 10. 

The model returns to the output whether the iceberg can or can not be moved out of the way in time using an if else statement. This particular data returns that the iceberg cannot be moved out of the way in time. The model also prints the total mass and volume of the iceberg. 

The model should work as follows:

1. The model imports all the relevant modules needed for the code to run
2. Empty lists are created in order for values to be added to the lists throughout the code. The height and width of the plot are set to 300 to represent 300m*2 of area.
3. The lidar and radar data files are read into python and their values are appended to the lists "radar_data" and "lidar_data" to represent the coordinates where there are ice and the corresponding height of the ice.
4. A plot of the iceberg in the sea is displayed on a GUI using the matplotlib.pyplot module. 
5. For loops are used to loop through the datasets to find out the coordinates where there is ice above sea level and the height.
6. A function is defined in order to pull out the height of the iceberg at each coordinate.
7. The total volume and mass is then calculated for above sea level and in total.
8. An if else statement is used to print the outcome of the model to the output.
