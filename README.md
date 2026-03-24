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

  

**Ride_Pattern_day_of_week:**

<img width="1393" height="359" alt="Rides Throughout The Week" src="https://github.com/user-attachments/assets/0f66d54d-2695-419b-8f94-092267c3d969" />

Here’s a clear, breakdown

---

📊 **Key Insights from “Rides Throughout The Week**

 1. Overall Usage Difference

* **Members:** 1,397,692 total rides
* **Casual users:** 829,041 total rides

👉 **Conclusion:**
Members take **~68% more rides** than casual users overall.

---

 2. Average Daily Usage

* **Members:** ~199,670 rides/day
* **Casual users:** ~118,434 rides/day

👉 **Insight:**
Members are consistently **more active and frequent riders**, indicating habitual/commute-based usage.

---

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

---

🚴‍♂️ Members (Routine Pattern)

* **Peak day:** Wednesday (230,030 rides)
* High usage: Tuesday–Thursday (very consistent)
* **Lowest:** Sunday (150,250 rides)

👉 **We can determine:**
Members ride mostly on **weekdays**, indicating:

* Work commutes
* Daily routines
* Structured usage patterns

---

4. Weekday vs Weekend Contrast

| Group  | Weekdays Behavior | Weekend Behavior |
| ------ | ----------------- | ---------------- |
| Casual | Low               | High 🔥          |
| Member | High 🔥           | Lower            |

👉 **Key Takeaway:**
There is a **clear behavioral split**:

* Casual = **Weekend riders**
* Members = **Weekday riders**

