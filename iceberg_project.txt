# Open the file from the working directory
# All files should be saved under same working directory
f = open('iceberg_project.py')
   

# Importing all modules needed for the project

# Import module to show plot
import matplotlib.pyplot
# Import module to read csv file
import csv
# Import time module to test run time
import time

# Testing run time efficiency of code

# Start timing execution of code from here:
start = time.time() 

# Assigning values to all labels used in the project

# Attach value 300 to label "height"
height = 300
# Attach value 300 to label "width"
width = 300

# Create empty lists to attach coordinates to
above_sea = []
berg_height = []
ice_coordinates = []

# Importing lidar_data

# Create lidar_data - as an empty list
lidar_data = []
# Open the white1lidar file
with open('white1lidar.txt', newline='') as f:
    # Read the file
    reader = csv.reader(f, quoting=csv.QUOTE_NONNUMERIC)
    # For the row
    for row in reader:
        # Create list called "rowlist"
        rowlist = []
        # For the value in row:
        for value in row:
            rowlist.append(value)
        # Creates environment from values in white1lidar file
        lidar_data.append(rowlist)
      
# Importing radar_data

# Create radar_data - as an empty list
radar_data = []
# Open the white1lidar file
with open('white1radar.txt', newline='') as f:
    # Read the file
    reader = csv.reader(f, quoting=csv.QUOTE_NONNUMERIC)
    # For the row
    for row in reader:
        # Create list called "rowlist"
        rowlist = []
        # For the value in row:
        for value in row:
            rowlist.append(value)
        # Creates environment from values in white1lidar file
        radar_data.append(rowlist)
    
# Creating and displaying the graph 

# Create a plot in the range (0, 299) y and x axis
matplotlib.pyplot.xlim(0, 299)
matplotlib.pyplot.ylim(0, 299)


# Show the lidar data on the plot
matplotlib.pyplot.imshow(lidar_data)
# Show the radar data on the plot
matplotlib.pyplot.imshow(radar_data)
# Show the plot
matplotlib.pyplot.show()
# Can see the raster graph from both lidar and radar files

# Finding length height and width from lidar and radar files (using for loops)

# Looping through lidar data to find height 
# In the range of the y axis
for y in range(height):
    # And in the range of the x axis 
    for x in range(width):
        # If the value for lidar data is greater than 0 (sea level)
        if lidar_data[y][x] > 0:
            # Attach the values to lust "berg_height"
            berg_height.append(y)
            # Print all values for berg height (turned off for efficiency)
        #print(berg_height)
        # Output shows all values - shows code works

# Print the list of the length of the list from the lidar data
print("Length of berg_height list = ", len(berg_height)) 
# Output shows 994 - checks data is imported        
  
# Looping through radar data to find coordinates where there's ice
# To find length and width (m*2)

for y in range(height):
    for x in range(width):
        # If there is ice that is above sea level 
        if radar_data[y][x] >= 100 and lidar_data[y][x] > 0:
            # Attach the coordinates to ice_coordinates list
            ice_coordinates.append([x,y])
        #print(ice_coordinates)
            
# Calculating volume of iceberg 1 above sealevel
# Volume = length * width * height 
# Volume = radar_data * (lidar_data / 10) 

print("max ice coordinate", max(ice_coordinates)) 
# Output shows [165, 165]
print("min ice coordinate", min(ice_coordinates))
# Output shows [135, 135]

print("Length of ice_coordinates list = ", len(ice_coordinates))
# Output shows 961 - checks data is imported

# Getting relevant heights for each coordinate where there is ice

# Define a function to return the height at each coordinate where there's ice
def height():
    # For the coordinates in ice_coordinates (where there is ice)
    for coordinates in ice_coordinates:
        # Return the corresponding values for the height (from lidar)
        return (berg_height)
    
# Print the values of the height to the output (Turned off for efficiency)
#print(height())
# Output shows the height of each coordinate where there's ice

# Print the sum of the height / 10 to get height in m
print(sum(height())/10) 

# Attatch this value to height_one
height_one = (sum(height())/10) 

# Check the function works by checking how many values for height there is
print("Number of values for height = ", len(height()))
# Output shows 994 which is same as the length of berg_height (code works)

# Length and width of each coordinate representd an area of 1m*2
# Volume is equal to the height of each 1m*2 area hence "*1 *1"
volume_one = height_one *1 *1

# Print volume to output 
print("Total volume of iceberg above sealevel = ", volume_one, "m*3")

# Calculate total mass of iceberg 1 above sealevel

# Mass = 900kg x volume (900 as this is the density of ice)
mass_above_sea = 900 * volume_one

# Print total mass amove sea level to output
print("Total mass of iceberg above sea level = ", mass_above_sea, "kg/m3")  

# Calculate total mass of iceberg 1 above and below sea level

# 10% of mass is above sea level so * mass above by 10
total_mass_one = mass_above_sea * 10

# Print total mass to output
print("Total mass of iceberg = ", total_mass_one, "kg")

# Calculate total volume of iceberg 
total_volume = total_mass_one / 900

# Print total volume to output
print("Total volume = ", total_volume, "m*3")

# Print to output whether we can move it out the way in time using "if else"

# If the total mass of the iceberg is greater than 36million kg then
if total_mass_one > 36000000:
    # Print to output that we can't move it
    print("Iceberg can NOT be moved out the way in time!")
# If the total mass is not greater than 36million kg then
else:
    print("Iceberg CAN be moved out of the way in time!")
    
# End timing code execution time from here
end = time.time()

# Print the execution time 
print("Time code took to run = " + str(end - start))

# Close the file
f.close()
