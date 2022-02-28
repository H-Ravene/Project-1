# Project-1
# Using information about the details of particular flights in order to perform analysis to compare the arrival delays for the two airlines.

import pandas as pd

#Reading the flight information from the csv file into pandas
airline_data=pd.read_csv(r"C:\Users\Sixpm\OneDrive\Pictures\DATA PROJECT 1.csv")

#Checking validity of the data. 
airline_data.head()


# Calculating the percentage of Alaska Airline flights that were delayed for each of the 5 destinations. 

airline_data['Total_Alaska_Flights'] = airline_data['ALASKA_AIRLINES_ON_TIME'] + airline_data['ALASKA_AIRLINES_DELAYED']

airline_data['Alaska_Airlines_Percentage_Delayed']= (airline_data['ALASKA_AIRLINES_DELAYED'] / airline_data['Total_Alaska_Flights']) * 100

airline_data['Alaska_Airlines_Percentage_Delayed']

#Calculating the percentage of AM West flights that were delayed for each of the 5 destinations. 


airline_data['Total_AMWest_Flights'] = airline_data['AM WEST_AIRLINES_DELAYED'] + airline_data['AM WEST_AIRLINES_On_Time']

airline_data['AMWest_Percentage_Delayed'] = (airline_data['AM WEST_AIRLINES_DELAYED'] / airline_data['Total_AMWest_Flights']) * 100

airline_data['AMWest_Percentage_Delayed']


# Comparing the delays of the two airlines at each of the 5 destinations. From these results we can conclude that AM airlines had a greater percentage of its flights delayed at each destination. 

airline_data[['Alaska_Airlines_Percentage_Delayed', 'AMWest_Percentage_Delayed']]

for index, row in airline_data.iterrows():
    if row["Alaska_Airlines_Percentage_Delayed"] > row["AMWest_Percentage_Delayed"]:
        airline_data.loc[index, 'Most_Delayed_Airline'] = 'Alaska'
    else:
        airline_data.loc[index, 'Most_Delayed_Airline'] = 'AMWest'

airline_data['Most_Delayed_Airline']
airline_data
