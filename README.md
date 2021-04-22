# Accessing and Analyzing Temperature Data Using SQL and Python

# Overview

Here we are accessing a SQLite database including temperature informtion in Oahu. Our goal is to utilze Python's functionality to aquire specific information from specific time periods, so we can display our findings/conduct an analysis.

# Explanation 
After importing the necessary Python dependencies/SQL tools to start a session, we want to acquire the temperature data specifically for the months of June and also December.

We Write this query to access the information from the SQLite file ("6" being the numberical month):
```
june_temps = session.query(Measurement).filter(extract('month', Measurement.date) == 6)
```
Followed by a for loop:
```
june_temps_list = []
for d in june_temps:
    values = d.tobs 
    print(values)
    june_temps_list.append(values)
```
Repeat this process the month of December, then we have the information we need:
![image](https://user-images.githubusercontent.com/79726572/115754092-df689a00-a369-11eb-8776-71d6125d371d.png)
![image](https://user-images.githubusercontent.com/79726572/115754129-e7283e80-a369-11eb-95f4-e7e0af661eae.png)

# Results
- We find that the two months from different times of the year don't vary much in temperature in Oahu, we see this as the standard deviation for both muchs is small and relatively close to one another (aprox. 3.25/3.75)
- In the month of December (assumed to be the coldest month of all) the minimum temperature of a 1500 + count dataset is not far off from the averages, which also tells us there really aren't any outliers of it being freezing cold at any point when it's assumed to be the coldest
- The 3 percentiles of data for both months is roughly the same, which further clarifies that even the averages of averages produce relevant/consistent information

# Summary
We can summarize that Oahu is a great destination for people to be in terms of temperature in a Tropical region of the world. However with the information we have access to it would be worth querying more data to further our analysis. This can be done by running similar code on humidity, as this is a factor to consider with tourism. Another potential analysis is to bin the temperatre data by time of day, and extract such info by certain days of a month, to see if there are any fluctations/key periods of temperature change, and to further justify the accuracy f the data previously collected.
