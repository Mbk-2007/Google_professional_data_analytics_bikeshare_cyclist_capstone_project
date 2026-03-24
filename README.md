# Google_professional_data_analytics_bikeshare_cyclist_capstone_project
This is the final capstone project "How does a bike-share navigate speedy success?" case study that is needed to completed in order to finish the google professional data analytics certificate offered at coursera. Inorder to finish by final project, I used the data analysis process, 1. Ask 2. Prepare 3. Process 4. Analayze 5. Share 6. Act.

# Scenario
I am working as a junior data analyst in the marketing team at Cyclistic, which is a bikeshare company in Chicago. Cyclistic is responsible for a fleet of 5824 bikes which are geotracked and locked into a network of 692 stations across Chicago. Chicagos finance analaysts have drawn the conclusion that annual members bring in more profits then casual riders. Lily Monero, our stakeholder and manager, also the director of marketing, is the key figure behind the development of campaigns. Monero believes that rather then simple advertisment and campaigning, we must prioratize understanding the differences between casual riders and annual members, so that we may be able to convert the casual rider into an annual member. It is my responsibilty to analyze from the data given, key differences between these two groups and from the data, draw insights on how to convert them from casuals to members.

# The data analysis Process


# 1. Ask
**Business Task**: Using the data provided to determine how the annual member compares with the casual rider, and using the data given to make a data-driven conclusion on how to convert the casual rider into an annual member.

**Stakeholders:** 
1. Lily Moreno, director of the marketing team and my primary stakeholder.
2. Cyclistic executive team.
3. Cyclistic marketing Analytics team.
   
**Leading questions:**

How do ride patterns differ between members and casual riders? 

What times of day/week do each group prefer? 

What bike types do each group use?

 How do trip durations compare? 
 
Where do each group start/end their trips?

 How does usage vary by month/day?

# 2. Prepare:

I downloaded the public Cyclistic trip data, around 6 months of of the data, from July 2025 to December 2025.

I verified if the data meets the **ROCCC (Reliable, Original, Comprehensive, Current, Cited) criteria**:

1.	Firstly, its reliable as it comes from a reliable source. Data comes directly from Divvy, Chicago's official bike-share system operated by the Chicago Department of Transportation (CDOT). As it is operated by the government, it follows strict data collection protocols and government agencies are considered reliable.
2.	It is original as it comes from their direct website and has first party data making it a primary source.
3.	It is comprehensive as it has all the essential fields needed to determine the difference between casual and member riders.
4.	It is current, the data collected is vast and less then an year old, with it starting from July which was 8 months ago and ending at December which was 3 months ago.
5.	Lastly it is citied, as it is present directly and accessible through https://divvy-tripdata.s3.amazonaws.com/index.html . It has proper licenses too which adds to credibility. (https://www.divvybikes.com/data-license-agreement is the license).

   ---

I downloaded the raw data as a CSV file, through excel I first checked if the data was properly formatted, the started_at and ended_at column cell valus were missing dates, only showing time in minutes and seconds, as it was incorrectly formatted. I fixed the formatting by;

1. Selecting the entire column
   <img width="1651" height="987" alt="image" src="https://github.com/user-attachments/assets/60d6a502-c1e2-4a32-97e2-e124f14f678d" />

2. Right clicking it and then left clicking fomat cells
 <img width="1911" height="989" alt="image" src="https://github.com/user-attachments/assets/d8381f3b-69f3-441c-950b-c888c92213b7" />
 
3. Going to custom then setting the data type too "DD/MM/YYYY hh : mm : ss'
<img width="1916" height="982" alt="image" src="https://github.com/user-attachments/assets/b949ee0a-6837-492e-9674-692f0eb9ac3c" />.

4. After the data was finally correctly formatted, I did some initial pre cleaning analysis, by checking the ride duration by creating a new column "trip_length", under which I wrote the formula "=D2 - C2" and auto filled it.

<img width="1914" height="827" alt="image" src="https://github.com/user-attachments/assets/90f66479-1e6f-4346-94bd-17ee84aec6f6" />

5. Since it was incorrectly formatted, I clicked format cell, then went to numbers, then custom, then fixed it by setting its data type to 'hh: mm : ss'. 
<img width="1919" height="975" alt="image" src="https://github.com/user-attachments/assets/c7b145b7-1bf4-4581-9447-9518669aff74" />

6. I proceeded to create one more column called "day_of_week", I created it using the formula =WEEKDAY(C2, 1)
   <img width="1917" height="980" alt="image" src="https://github.com/user-attachments/assets/5c302681-6556-411d-b2e9-0a6376ac1135" />
7. I then saved it by going to file > Save as > Documents > (month name.csv).
8. I repeated for all the 6 months.
9. I uploaded the data to Google cloud storage.
10. I created a new dataset called "bikeshare" in BIGQUERY.
11. I uploaded each of the file into a different table as per month and named each table after the month.

---


I checked each cells, data type to make sure it was correctly formatted.
<img width="1577" height="811" alt="image" src="https://github.com/user-attachments/assets/1203b08b-70c9-45c1-9b1f-92777b54f29d" />

<img width="1596" height="849" alt="image" src="https://github.com/user-attachments/assets/bfd817cb-1d79-4ad3-a4bb-128e9e596d89" />



.I proceeded to check the consistency of all the tables https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/Table%2C%20Column%20Consistency 

. I inspected each month/table to account for **total trips/rows**, **total valid station names** and **% of missing values** in station names, and **number of unique rider type** numbers per table (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/data%20validation)

<img width="1435" height="279" alt="Screenshot 2026-03-23 135405" src="https://github.com/user-attachments/assets/4a7f289f-1396-4780-be59-6b5913df6782" />





# 3. Process

**Combining tables into one:**
I first combined all the tables into one table and named it all (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/combining_tables_into_one)

**Number of Duplicates:**
. I then checked for number of **duplicates** in ride_id. (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/num_of_duplicates)

**Number Of nulls:**
.I then checked for **number of null** values (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/num_of_nulls)

**Removing duplicates:**
I created a new table where I would perform all my cleaning, and to remove the duplicates (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/Duplicate_removal)

**Removing Nulls:**
I removed all the nulls from the new table (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/null_removal)

**Adding new month and hour_of_day columns:**
In order to analyze my data, I first had to make sure I had all the data I needed, so I created two new columns called "month" and "hour_of_day" (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/month%2Bhour_of_day%20column%20added)


**Filling the month and hour_of_day columns**
I then filled the new values of these two tables (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/filling_month%2Bhour_of_day)

# 4. Analysis

**Bike Preference:**
I analyzed the different bike type preferences of casual and member riders. (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/Bike_preference_analysis)


**Station Preference:**
I analyzed which stations where primarily prefered by casual riders and by annual riders.
(https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/station_preference_casual)
(https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/station_preference_members)

**Ride_Duration_Analysis:**
I analyzed the max, min and average ride duration of both casual and member riders by month
(https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/Ride_duration_analysis).

**Ride_Pattern_day_of_week:**
I calculated the amount of trips casual and member riders make through out the week (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/ride_pattern_day%20of%20week)

**Ride_pattern_hour_of_day:**
I calculated the amount of trips casual and member riders make through out the day (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/ride_pattern_through%20hours%20of%20day)

**Ride_pattern_months:**
I caluclated the total trips of riders over the months (https://github.com/Mbk-2007/Google_professional_data_analytics_bikeshare_cyclist_capstone_project/blob/main/ride_pattern_over%20the%20months)


# 5. Share

**- Bike Preference:**

<img width="585" height="679" alt="Bike Preference" src="https://github.com/user-attachments/assets/e1d066e3-4576-4412-a2e8-150e69e70472" />

We can deduce that Members prefer classic bikes:
Classic: 745,296
Electric: 652,396
While Casual riders slightly prefer electric bikes:
Electric: 421,929
Classic: 407,112

Interpretation:

Members may favor classic bikes for routine, cost-effective use.
Casual riders may lean toward electric bikes for convenience or leisure.


What We Can deduce is that
Membership programs are effective at driving higher usage.
Electric bikes are a strong attraction for occasional users.
There’s potential to:
Convert casual users → members (especially electric bike users)
Promote electric bikes more to members.

---


**- Station Preference**

<img width="489" height="679" alt="Popular_station_casual" src="https://github.com/user-attachments/assets/3a3dbb42-a3af-4fca-b214-5b2ebd0f9910" />
<img width="489" height="679" alt="Popular station member" src="https://github.com/user-attachments/assets/dfbc230c-6223-4320-88e3-edf94f851088" />


**1. Casual Riders – Station Preferences**

Top stations (by ride count):

1. Navy Pier
2. DuSable Lake Shore Dr & Monroe St 
3. Michigan Ave & Oak St 
**Pattern:**
 Casual riders strongly prefer tourist and recreational locations
 These stations are:
- Near waterfronts 
- Popular attractions
- Scenic / leisure areas

👉 This suggests casual users ride mostly for:

- Sightseeing
- Leisure trips
- Occasional outings

**2. Member Riders – Station Preferences**

Top stations:

1. Kingsbury St & Kinzie St
2. Clinton St & Washington Blvd
3. Clinton St & Madison St 
📌 Pattern:
Members prefer business district / downtown stations
These locations are:
- Close to offices 🏢
- Transit hubs
- Daily commute routes

👉 This suggests members ride mostly for:

- Work commuting
- Daily transportation
- Routine travel

---

  **- Ride_Duration_Analysis**

  
  <img width="706" height="679" alt="Ride Length Analysis (1)" src="https://github.com/user-attachments/assets/635afc63-e86e-40b0-8ec5-8378617dc562" />

 Key Insights 
🚴‍♂️ 1. Casual riders ride MUCH longer than members
Casual Avg: ~19.81 minutes
Member Avg: ~12.13 minutes

👉 Casual riders ride ~63% longer than members on average.

Insight:

Casual users treat rides more like leisure/experience
Members use bikes more for commuting or routine travel
📉 1. Strong seasonal decline (especially for casual riders)
Casual Riders:
Peak: August (~23.8 min)
Lowest: December (~13.7 min)
Drop: ~10 minutes decrease
Members:
Peak: July (~12.94 min)
Lowest: December (~11.45 min)
Drop: very small (~1.5 min)

👉 Casual riders are highly seasonal, members are stable

🌦️ 2. Summer vs Winter Behavior
Summer (July–August):
Casual rides are longest (~23–24 min)
Winter (Nov–Dec):
Casual rides drop sharply

---


**- Ride_Pattern_day_of_week:**

<img width="1393" height="359" alt="Rides Throughout The Week" src="https://github.com/user-attachments/assets/0f66d54d-2695-419b-8f94-092267c3d969" />

Here’s a clear, breakdown



📊 **Key Insights from “Rides Throughout The Week**

 1. Overall Usage Difference

* **Members:** 1,397,692 total rides
* **Casual users:** 829,041 total rides

👉 **Conclusion:**
Members take **~68% more rides** than casual users overall.



 2. Average Daily Usage

* **Members:** ~199,670 rides/day
* **Casual users:** ~118,434 rides/day

👉 **Insight:**
Members are consistently **more active and frequent riders**, indicating habitual/commute-based usage.



 3. Weekly Behavior Patterns

🚴 Casual Riders (Leisure Pattern)

* **Peak day:** Saturday (171,127 rides)
* **Second highest:** Sunday (143,088 rides)
* **Lowest:** Monday (92,334 rides)

👉 **We can determine:**
Casual users ride mostly on **weekends**, suggesting:

* Leisure
* Tourism
* Social/outdoor activities


🚴‍♂️ Members (Routine Pattern)

* **Peak day:** Wednesday (230,030 rides)
* High usage: Tuesday–Thursday (very consistent)
* **Lowest:** Sunday (150,250 rides)

👉 **We can determine:**
Members ride mostly on **weekdays**, indicating:

* Work commutes
* Daily routines
* Structured usage patterns



4. Weekday vs Weekend Contrast

| Group  | Weekdays Behavior | Weekend Behavior |
| ------ | ----------------- | ---------------- |
| Casual | Low               | High 🔥          |
| Member | High 🔥           | Lower            |

👉 **Key Takeaway:**
There is a **clear behavioral split**:

* Casual = **Weekend riders**
* Members = **Weekday riders**

---
  

**- Ride_pattern_hour_of_day:**

<img width="1393" height="679" alt="hour_of_day" src="https://github.com/user-attachments/assets/f095a8d8-fff8-461e-9899-9cc066145dcd" />


Key Insights from Hour-of-Day Analysis
⏰ 1. Peak Usage Time (Most Important Insight)
Both casual riders and members peak at 5 PM (17:00)
At this hour:
Members: 152,846 rides (highest overall)
Casual: 78,095 rides

👉 Interpretation:

This strongly suggests evening commute + leisure overlap
5 PM is the most critical business hour



🌙 2. Lowest Activity (Off-Peak Hours)
Members lowest: 3 AM (~2,216 rides)
Casual lowest: 4 AM (~2,589 rides)

👉 Interpretation:

Very low demand overnight
Opportunity to:
Reduce operations costs
Schedule maintenance



 3. Behavioral Difference: Members vs Casual
Members:
Show strong commute behavior
Gradual rise in morning → peak in evening
More consistent throughout the day
Casual Riders:
More leisure-oriented
Lower early morning usage
Sharper increase in afternoon/evening

👉 Key takeaway:

Members = routine users (work/commute)
Casual = flexible users (leisure/social)



 4. Daily Usage Pattern
Early morning (12 AM – 5 AM): Very low usage
Morning (6 AM – 10 AM): Steady increase (commute begins)
Afternoon (11 AM – 4 PM): Moderate-high activity
Evening (5 PM – 7 PM): Peak zone
Night (8 PM onward): Gradual decline

---

**- Ride Pattern over the months**
<img width="723" height="679" alt="Ride Pattern Over The Months" src="https://github.com/user-attachments/assets/59cd0d57-bb5c-4cb8-8c4f-5cb366767dbc" />

Key Findings – Ride Pattern Analysis (July to December)
Overall Ride Activity Trend
The dataset shows a clear seasonal pattern in bike usage.
Ride activity is highest during summer months and declines steadily toward winter.
August recorded the highest number of rides, while December had the lowest.
The total number of rides drops significantly after October, indicating that colder weather likely reduces bike usage.

This suggests that weather and seasonal conditions strongly influence riding behavior.

Seasonal Usage Pattern

Ride activity gradually decreases as the year progresses.

July and August show the strongest demand for bike rides.
September and October still maintain relatively high activity but begin to decline.
November shows a sharp drop in ridership.
December has extremely low usage compared to previous months.

This pattern suggests that the bike-sharing service experiences peak demand during warm months, followed by a significant seasonal slowdown.

Differences Between Members and Casual Riders

The analysis reveals distinct behavioral differences between member riders and casual riders.

Members consistently account for the majority of rides each month.
Casual riders represent a large portion during summer months, but their usage decreases quickly as winter approaches.
By December, members make up the vast majority of rides, while casual rider activity becomes minimal.

This indicates that members rely on bikes more consistently, while casual riders appear to use the service mainly during favorable weather conditions.

Casual Rider Behavior

Casual rider activity shows strong seasonal dependence.

Key observations:

Casual ridership peaks during summer, particularly in July and August.
After August, casual rider activity drops steadily every month.
By December, casual ridership has declined dramatically.

This suggests that casual riders likely use bikes for:

leisure activities
tourism
outdoor recreation
occasional trips

Their usage appears highly influenced by weather and seasonal factors.

Member Rider Behavior

Member riders show more stable and consistent usage throughout the months.

Important observations:

Members maintain relatively high ride counts during summer and early fall.
Although their activity also decreases toward winter, the decline is much less dramatic compared to casual riders.
By late fall and winter, members represent the dominant share of riders.

This pattern suggests that members likely use bikes for regular transportation needs, such as commuting or daily travel.

Major Decline in Ridership

One of the most significant changes occurs between October and November.

Ridership experiences a large drop during this transition period.
This likely reflects seasonal weather changes, shorter daylight hours, and colder temperatures.

This period represents the start of the low-demand season for bike usage.

Shift in Rider Composition Over Time

Another important trend is the increasing proportion of member rides over time.

During summer months, the share of casual riders is relatively high.
As the year progresses, casual riders decrease faster than members.
By winter, members dominate the majority of total rides.

This indicates that casual riders are more sensitive to seasonal conditions, while members maintain more consistent usage patterns.

## 6. Act

From the Analysis and findings from above, here are some of my business suggestions:
1. Target Electric Bike Users First by offering a “First Month Membership Discount” after 2–3 electric rides

. Show in-app message:
“You’ve taken 3 electric rides—save 30% with membership!”
Catch them when they’re already engaged.

2. Make casual users realize how much they are spending by showing a real-time comparison e.g. “You spent $18 this week. Membership would cost $12.”
 Make the benefit obvious and immediate.

4. Since casuals like electric bikes:
Offer limited free electric ride minutes for new members e.g. “Upgrade to membership and get 50 e-bike minutes free”
5. Build more bikes near tourist hotspots → attract casual riders.
6. Casual users already show strong engagement on weekends, convert them into members by offering weekday discounts and Promoting cost savings of membership
7. Increase bike availability on Weekends for casual users and on Weekdays for members.
8. Promote evening rides.
9. Increase resource availibility around peak hours, such as 5pm, prioratize Evening > Afternoon > Morning > Night.
10. Since casual riders are high in summer offer membership discounts during peak months like June, July, August, September
11. During winter months focus on member retention by providing incentives like:
. discounted renewals
. loyalty rewards
