# python_api_challenge

This challenge involves two different Python scripts for the two parts of the challenge.  The first part examines weather data for a random selection of at least 500 cities, and the second part uses the city data from the first part to create a list of desired vacation locations, then collect and map hotel information for each of those.

Because the Juptyer notebook displays the maps beautifully with hover-over pop-ups when running, but the maps do not show when the notebook file is uploaded (repeatedly), screen prints of the two maps were
added to the VacationPy folder.  This does not display the hover-over information, as running the screen capture software removes the focus from the hover, but running the notebook will show that working.

#-----------------------------------
#  Installation and setup
#-----------------------------------

These two scripts use api keys that are stored in a config.py on the platform where they are run.  The config.py file is part of the .gitignore, and is not pushed to the git repository with the other code.  To run these scripts, it will be necessary to create an "api_keys.py"
file in the main folder for the project, and to generate api keys for the OpenWeatherMap API and the Geoapify API using information on how to do so from their web pages.  This process requires a little time for the API key to be generated after it is requested, and then also it is
neccessary to confirm the email used before the API key can be used.   

The scripts require that Juypter notebook, Pandas, json, requests, numpy, and random be installed in the environment that will be running the code.  In addition, the geoview, cartopy, and pyproj packages must be installed.  This can be done most easily with "conda install -c pyviz", geoviews"conda install -c anaconda pyproj", and "conda install -c conda-forge cartopy".

The scripts are in two subfolders, WeatherPy and VacationPy.  The first script reads input from a subfolder called "Resources," and outputs a .csv file of city data which is used by the VacationPy script, to a subfolder called "output_data."  It also outputs ten map images, four global, four for the northern hemisphere, and four for the southern hemisphers, to the subfolder "output_data."  The files will be created if they do not exist and overwritten if they do exist when the script is run, but the "output_data" folder must exist before the script is run.

#-----------------------
#  Part 1:  Weather Data, WeatherPy
#-----------------------

The "WeatherPy.ipynb" script, in the subfolder "WeatherPY," has two parts for its two requirements.  The first part generates a random set of coordinates for at least 500 cities, and collects weather data for those cities using the OpenWeatherMap API.  

The code then examines temperature vs. latitude, humidity vs. latitude, cloudiness vs. latitude, and wind speed vs. latitude, globally, and creates scatter plots for those relationships.  

For the second part, the code divides the cities data into dataframes for the northern and southern hemispheres, calculates linear regression values and the linear regression line for each relationship, for each hemispehre.  It then creates a scatter plot showing the data points, the linear regression line, and the equation for the line.   

After both northern and southern hemispheres have been plotted for one of the four weather values compared to latitude, the Jupyter notebook contains an analsyis comparing the correlation between the values in the two hemispheres.
 
The code to generate the random cities was provided in the project requirements.  ChatGPT, Stack Overflow, and Geeks to Geeks, as well as the API documentation pages, were used for various details about configuring the plots.

The regression correlation is calculated unsing one function, linRegress, that returns the regression values and the regression equation.  The regression scatter plots are drawn using another function, plotRegress, which calls the linRegress function to get the regressoin line and equation that it uses on the plot.

#-----------------------------------
#  Part 2:  Choosing Vacation Locations, VacationPY
#----------------------------------

The "VacationPy.ipynb" script, in the subfolder "VacationPY", uses the output file 'cities.csv" in the "WeatherPy/output_data" folder for its input.  It maps all of the randomly-selected cities, with points varying in size to show the city's humidity.  The script then gets hotel data for a subset of cities that rae selected by limits on the weather values, and uses Geoapify API to get hotel information for those cities.  Finally, it uses GeoViews, cartopy, and hvplot to display those cities on a map, again using point size to show humidity, but also displaying city names.  

Both maps have popups on hover, with the vacation map popup also showing hotel and country information.

The geoapify API documentation pages and the mapplotlib documentation pages were consulted for getting hotel data and configuring the maps.