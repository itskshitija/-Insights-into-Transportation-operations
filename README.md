# Insights into Transportation operations
### Domain:  Transportation & Mobility          
### Function: Operations 

## Table of Contents
- [Overview](#overview)
- [Data Summary and Understanding](#data-summary-and-understanding)
- [Relational Model View](#relational-model-view)
- [Building Metrics using DAX](#building-metrics-using-dax)

## Overview
Goodcabs, a cab service company established two years ago, has gained a strong foothold in the Indian market by focusing on tier-2 cities. Unlike other cab service providers, Goodcabs is committed to supporting local drivers, helping them make a sustainable living in their hometowns while ensuring excellent service to passengers. With operations in ten tier-2 cities across India, Goodcabs has set ambitious performance targets for 2024 to drive growth and improve passenger satisfaction. 

As part of this initiative, the Goodcabs management team aims to assess the company’s performance across key metrics, including trip volume, passenger satisfaction, repeat passenger rate, trip distribution, and the balance between new and repeat passengers. 

However, the Chief of Operations, Bruce Haryali, wanted this immediately but the analytics manager Tony is engaged on another critical project. Tony decided to give this work to Peter Pandey who is the curious data analyst of Goodcabs. Since these insights will be directly reported to the Chief of Operations, Tony also provided some notes to Peter to support his work. 

## Data Summary and Understanding
[Find Attached File Here](https://github.com/itskshitija/Insights-into-Transportation-operations/blob/main/meta_data.txt)


## Relational Model View
![image](https://github.com/user-attachments/assets/188c1d23-9774-43e0-a2c8-2a64048f8a4c)

## Building Metrics using DAX

<b>1.Total Trips</b>
```
Total Trips = CALCULATE(COUNT(fact_trips[trip_id]))
```

<b>2.Total Fare (Revenue)</b> 
```
Total Revenue = CALCULATE(SUM(fact_trips[fare_amount]))
```

<b>3.Total Distance Travelled</b>
```
Total Distance Travelled = CALCULATE(SUM(fact_trips[distance_travelled(km)]))
```

<b>4.Average Passenger Rating</b>
```
Average Passenger Rating = AVERAGE(fact_trips[passenger_rating])
```

<b>5.Average Driver Rating</b>
```
Average Driver Rating = AVERAGE(fact_trips[driver_rating])
```

<b>6.Average Fare Per Trip</b>
```
Average Fare per Trip = AVERAGE(fact_trips[fare_amount])
```

<b>7.Average Fare per km</b>
```
Average Fare Per km = DIVIDE(SUM(fact_trips[fare_amount]),SUM(fact_trips[distance_travelled(km)]),0)
```

<b>8.Average Trip Distance</b>
```
Average Trip Distance = CALCULATE(AVERAGE(fact_trips[distance_travelled(km)]))
```

<b>9.Min Trip Distance</b>
```
Min Trip Distance = CALCULATE(MIN(fact_trips[distance_travelled(km)]))
```

<b>10. Maximum Trip Distance</b>
```
Max Trip Distance = CALCULATE(MAX(fact_trips[distance_travelled(km)]))
```

<b>11.New Passengers</b>
```
New Passengers = CALCULATE(SUM(fact_passenger_summary[new_passengers]))
```

<b>12.Total Passengers</b>
```
Total Passengers = CALCULATE(SUM(fact_passenger_summary[total_passengers]))
```

<b>13.Repeated Passengers</b>
```
Repeated Passengers = CALCULATE(SUM(fact_passenger_summary[repeat_passengers]))
```

<b>14. Repeat Passenger Rate (RPR%)</b>
```
RPR% = DIVIDE([Repeated Passengers],[Total Passengers])
```

<b>15.Trips Target Achievement Rate(TTAR%)</b>
```
TTAR% = DIVIDE([Total Trips],SUM(monthly_target_trips[total_target_trips]),0)
```

<b>16.New Passenger Target Achievement Rate(NPTAR%)</b>
```
NPTAR% = DIVIDE([New Passengers],SUM(monthly_target_new_passengers[target_new_passengers]),0)
```

<b>17.Average Passenger Rating Target Achievement Rate (APRTAR%)</b>
```
APRTAR% = DIVIDE([Average Passenger Rating],AVERAGE(city_target_passenger_rating[target_avg_passenger_rating]),0)
```
