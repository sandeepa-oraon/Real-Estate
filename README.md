# Real-Estate
# Real-Estate Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/bd63a5d8-3eed-4685-9a6e-6fdaa17a0cc4/a11468e8b8a0cae630a4?experience=power-bi

## Problem Statement

This dashboard on real estate is a tool designed to provide an interactive and insightful interface for analysing and visualizing real estate data. Real estate, being one of the most dynamic and impactful industries globally, plays a critical role in economic growth and individual investment decisions. With the increasing digitization of industries, real estate data analytics has emerged as a vital area for innovation, enabling stakeholders to make informed decisions based on comprehensive and real-time insights.

In recent years, technology has changed the way people access and use real estate information. Buyers searching for properties and investors analysing market trends now rely more on data-driven tools. Traditional methods of studying real estate markets are often slow, rigid, and don’t provide helpful insights. Dashboards have become popular because they can bring together, process, and display large amounts of data in an easy-to-understand way.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a xlsx file.
- Step 2 : Open power query editor 
- Step 3 : Also since by default, xlsx file will be opened for 20 rows so you need to select "column based on your requirrement".
#### Data pre-processing
- Step 4 : There were no empty or null values in the data sets so we don't need to perform data pre-processing for null values.
- Step 5 : From the dataset 'sqft_lot15', 'sqft_living15', 'long', 'lat', 'zipcode', 'sqft_basement', 'sqft_above', 'grade', 'view', 'sqft_lot', 'sqft_living', and 'id' were removed from the dataset by selecting these columns, right click on them and click on 'remove columns'. Now, we have the columns 'Property location', 'price', 'bedrooms', 'floors', 'waterfront', 'Condition', 'yr_built', and 'yr_renovated'.
- Step 6 : By using 'bedrooms' column we have created a new column 'Bedrooms Status' and for cells take refrence from 'bedrooms', use the value_Bedroom(s). Do the same for the 'Floors Status', 'waterfront Status', 'Condition Status' columns.
- Step 7 : Now we create 'Renovated' column. From  'yr_built' and 'yr_renovated' column we find the 'Renovated' by substracting

        = [yr_built]-[yr_renovated]
    
in custom column formula tab. For 'Renovated Status' we create a conditional column with codition if value is greated than 0, value in column will be 'Renovated' else 'Not Renovated'
- Step 8 : Create different queriy for all the columns with no duplicate value having index. Merge these queries table in main query table with index values.
#### Creating Dashboard
- Step 9 : Dashboard containes of 4 pages. 'main', 'overview', 'Location', and 'about'. Dashboard contain properties such as:

    (a) Waterfront Status(Has waterfront)

    (b) Waterfront Status(Has no waterfront)

    (c) Renovated Status(Has Renovated)

    (d) Renovated Status(Has not Renovated)

    (e) Bedrooms contained in the properties
    
    (f) Floor Contained in the properties
    
    (g) Condition Status wise Properties
    
    (h) Properties by Year Built
    
    (i) Floor Location
    
    (j) Floor Status & Bedroom Status
    
    (k) Properties Info & Contact us

In 'main' & 'overview' page,
- Step 10 : Cards were added for four fields named Waterfront Status with 'Has waterfront' and 'Has no waterfront', and Renovated Status with 'Has Renovated' and 'Has not Renovated'.
for Waterfront Status with 'Has Waterfront' formula used is: 

    Waterfront Status Yes = CALCULATE([Total Properties], FILTER('Dim_Waterfront', 'Dim_Waterfront'[Waterfront Status]="Yes"))
for Waterfront Status with 'Has no Waterfront' formula used is: 
        
    Waterfront Status No = CALCULATE([Total Properties], FILTER('Dim_Waterfront', 'Dim_Waterfront'[Waterfront Status]="No"))
for Renovated Status with 'Has Renovate' formula used is: 

    Renovated Status Yes = CALCULATE([Total Properties], FILTER('Dim_Renovated', 'Dim_Renovated'[Renovated Status]="Renovated"))
for Renovated Status with 'Has not Renovate' formula used is: 

    Renovated Status No = CALCULATE([Total Properties], FILTER('Dim_Renovated', 'Dim_Renovated'[Renovated Status]="Not Renovated"))
- Step 11 : Since the data contains various Bedrooms and Floors, thus in order to represent bedrooms and floors, a new visual was added using the stacked bar chart in the visualizations pane in report view.
- Step 12 :  As for 'Condition status wise Properties', cards and Donut chart had been added for visualizations. And for 'Property by Year Status' Line chart had been used.
for card value of very good, good and bad formulas are:

    VeryGood Condition = CALCULATE([Total Properties], FILTER('Dim_Condition', 'Dim_Condition'[Condition Status]="Very Good"))
    Good Condition = CALCULATE([Total Properties], FILTER('Dim_Condition', 'Dim_Condition'[Condition Status]="Good"))
    Bad Condition = CALCULATE([Total Properties], FILTER('Dim_Condition', 'Dim_Condition'[Condition Status]="Bad"))
- Step 13 : Filter panel were added to filter values according to 'yr_built', 'Renovated Satus', and 'Property location'.
In 'Location' page,
- Step 14 : Map were added for visualizing location and according to the location, table had been added to displays 'floor status' and 'bedroom status' in 'very good', 'good', and 'bad' condition.
In 'about' page,
- Step 15 : 'Properties Info' table had been added to dispaly all the informations of properties and mode of contacting admin or owner had been added.   
- Step 16 : New measure was created to find total properties.

Following expression was written for the same,
        
        Total Properties = COUNTROWS('fact data') 
        
 ![TotalProperties](https://github.com/user-attachments/assets/823d4cc4-d63f-4262-af53-96f8627bdde0)

A card visual was used to represent count of customers.      
- Step 17 : New measure was created to find  % of Waterfront & Renovated Status,
 
 Following expression was written to find % of Waterfront with Renovated and no renovated status,
 
        % of waterfall status yes = DIVIDE([Waterfront Status Yes],[Total Properties],0) 
        % of waterfall status No = DIVIDE([Waterfront Status No],[Total Properties],0) 

- Step 18 : The report was then published to Power BI Service.
  ![uploaded](https://github.com/user-attachments/assets/033ef378-f6dc-48a3-88ab-3886f30e9c1a)

 
# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Properties = 22K

   Number of satisfied Customers (Male) = 28159 (21.68 %)

   Number of satisfied Customers (Female) = 28269 (21.76 %)

   Number of neutral/unsatisfied customers (Male) = 35822 (27.58 %)

   Number of neutral/unsatisfied customers (Female) = 37630 (28.97 %)


           thus, higher number of customers are neutral/unsatisfied.
           
### [2] Average Ratings

    a) Baggage Handling - 3.63/5
    b) Check-in Service - 3.31/5
    c) Cleanliness - 3.29/5
    d) Ease of online booking - 2.88/5
    e) Food & Drink - 3.21/5
    f) In-flight Entertainment - 3.36/5
    g) In-flight service - 3.64/5
    h) In-flight Wifi service - 2.81/5
    i) Leg room service - 3.37/5
    j) On-board service - 3.38/5
    k) Online boarding - 3.33/5
    l) Seat comfort - 3.44/5
    m) Departure & arrival convenience - 3.22/5
  
  while calculating average rating, null values have been ignored as they were not relevant for some customers. 
  
  These ratings will change if different visual filters will be applied.  
  
  ### [3] Average Delay 
  
      a) Average delay in arrival(minutes) - 15.09
      b) Average delay in departure(minutes) - 14.71
Average delay will change if different visual filters will be applied.

 ### [4] Some other insights
 
 ### Class
 
 1.1) 47.87 % customers travelled by Business class.
 
 1.2) 44.89 % customers travelled by Economy class.
 
 1.3) 7.25 % customers travelled by Economy plus class.
 
         thus, maximum customers travelled by Business class.
 
 ### Age Group
 
 2.1)  21.69 % customers belong to '0-25' age group.
 
 2.2)  52.44 % customers belong to '25-50' age group.
 
 2.3)  25.57 % customers belong to '50-75' age group.
 
 2.4)  0.31 % customers belong to '75-100' age group.
 
         thus, maximum customers belong to '25-50' age group.
         
### Customer Type

3.1) 18.31 % customers have customer type 'First time'.

3.2) 81.69 % customers have customer type 'returning'.
       
       thus, more customers have customer type 'returning'.

### Type of travel

4.1) 69.06 % customers have travel type 'Business'.

4.2) 30.94 % customers have travel type 'Personal'.

        thus, more customers have travel type 'Business'.
