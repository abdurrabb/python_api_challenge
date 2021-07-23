# python_api_challenge

Lots of learning in this challenge!

# WEATHERPY
# Import dependencies
Beginning with imports. I made the fatal error of pushing my api_key into public view on git because I forgot to update my git ignore file with the correct naming. After an 11:30pm email alert from git and google that my api had been used for some density api look-ups, I quickly set restrictions and remedied the error.


# Get list of random latitudes and longitudes
I spent the most time learning how to do this. First, I attempted geopy. Later, citipy. Still, learning how to use the random.uniform method to arrange the coordinates involved relearning that latitude runs -90 to 90 degrees and longitude runs -180 to 180 degrees. 

# Zip lat & lng into tupled list
Straightforward process

# Convert random coordinates into list of cities + details
Stored values in empty lists and set for loop through zipped list of coordinates with append the populate each empty list with the proper files

# Convert list to df

# Clean df of repeat cities
Removed duplicate cities from dataframe with .drop_duplicates method. Also, double check a reduction in dataframe size.

# Perform API Calls
This took the second-longest. Setting up the empty lists went quickly. Remembering how to arrange the requests.get within an iterrows [not a for-loop] with parameters within a concatenated string was... a tough. It took so long, Open Weather revoked my api request. Sean (instructor) shared a time.sleep(1) code that reduced the likelihood I'd be dinged for too many calls.

AskBCS helped me figure out that I was getting an error because the last city in my truncated practice dataframe of five cities was not found. So, URLs were printed but the json response also returned an error when I tried to print it. I combed through the Open Weather list of cities to confirm this.

Lining up the try/except required me to review the previous assignment. Sean always says that we're not expected to memorize these things; I took some comfort in that.

# Convert Raw Data to DataFrame
I zipped the now filled lists into a dataframe and assigned columns names. 

# Purge data of duplicates


# Export the city data into a .csv.
This step involved learning the simple .to_csv command. Lovely!

# Get the indices of cities that have humidity over 100%.
A loc method with a condition for all rows with >= 100 humidity solved this requirement. I stored those rows into a variable; then called the .index on the variable

# Make a new DataFrame equal to the city data to drop all humidity outliers by index.
Used .drop with the .index variable resolved this requirement. I also learned that passing inplace=False is another way to create a copy of the data frame. 

# Plotting the Data
Largely skills practiced in the MatPlotLib homework. Key takeaways include: 
 This scatter plot is a verticle slice of Planet Earth. The x ("Temperature) axis marks the temperature of cities around the world. Traveling our y "Latitude" axis north (80) to the equator (0) then south (-60), the temperature increases and peaks around 20-0 degrees. 

 Cities closer to the equator generally have higher temperatures. The reason temperatures peak at 20-0 degrees, instead of 0 degrees is due to the tilt of the earth's axis by about 23 degrees.

 There is no meaningful relationship between latitude and humidity, wind speed, or cloudiness. 


# VACATIONPY
# Import dependencies
Once again, imports were an unusual challenge. This time, gmaps. To config or not to config? This answer here was not to config. Instead, pip installing widgets then launching into jupyter notebook instead of jupyter lab was the answer.

# Load the csv exported in Part I to a DataFrame
pd.read_csv is a skill from several weeks ago that proved useful here. 

# Store latitude and longitude in locations

# Fill NaN values and convert to float

# Plot Heatmap
This was a time I had to look up the code and apply it with little understanding of what was happening behind the scenes. Despite lots of reading through Google's extensive documentation, I came away more confused about how all their apis work. Big thanks to Felipe (TA) for guiding me through the necessary installs. Also thanks to John (classmate) for offering another solution. 

Once the map loaded, I played with the params to get an understanding of how they influenced the map visual. 

# Narrow down the cities to fit weather conditions.
# Drop any rows will null values.
Determining my ideal weather conditions was fun. This list will be useful once I'm making more money! Narrowing the weather_df into the ideal list of required .loc and plenty of ampersands. Resetting the index was also useful. The ideal list was trimmed from over five hundred to 74 cities. San Patricio sounds cool. 

# Store into variable named hotel_df
Added "Hotel Name" and "Hotel Rating" columns to the dataframe by creating a copy of the ideal_cities dataframe, then adding the two empty columns. 

# Set parameters to search for hotels with 5000 meters.


# Use the Google Places API for each city's coordinates.


# Store the first Hotel results into the DataFrame.
This one, I had to look up. I'm still not entirely sure why this .loc[index, "xyz"] = resp... method works, but I was running out of time to research.

# Plot markers on top of the heatmap.
Thankfully, this was either written by me above or written in the starter pack. fig.add_layer(marker) was the only innovation here. 

# Note
My notebook never served the info box when I hovered on markers. Would appreciate a comment from the grader on why that is. 