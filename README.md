# python-api-challenge
Module 6 Challenge Repository

All code for this challenge is in the WeatherPy Folder.
Output_data for Part 1 is in the output_data folder. 

All code in part 1 is my code.

Most code in part 2 is my code, however the following excerpt should be credited to Shannon Lloyd for helping me write it: 
}

# Iterate through the hotel_df DataFrame
for index, row in hotel_df.iterrows():

    # Add filter and bias parameters with the current city's latitude and longitude to the params dictionary
    params["filter"] = f"circle:{row['Lng']},{row['Lat']},{radius}"
    params["bias"] = f"proximity:{row['Lng']},{row['Lat']}"
    
    
    # Grab the first hotel from the results and store the name in the hotel_df DataFrame
    try:
        hotel_df.loc[index, "Hotel Name"] = name_address["features"][0]["properties"]["name"]
    except (KeyError, IndexError):
        # If no hotel is found, set the hotel name as "No hotel found".
        hotel_df.loc[index, "Hotel Name"] = "No hotel found"
        
    # Log the search results
    print(f"{hotel_df.loc[index, 'City']}, nearest hotel: {hotel_df.loc[index, 'Hotel Name']}")


    
