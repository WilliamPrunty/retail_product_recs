## XXXXXXXXXX Sales Analysis

### BACKSTORY  
In our XXXXXXXXXXX Stores, our employees are trained in what is called “4 on the Floor”. When a customer asks to try on a shoe, the employee goes to the back room and is expected to bring the shoe that the customer wants to try on and an additional 3 pair of shoes to try to sell to them. Typically, this is the same shoe in a different color, a shoe that just came in, and a shoe that is on sale. In the real world, only those who are very experienced can do this with any accuracy.

We are working towards creating an application that will tell the employee what was sold with the requested shoe, focusing on other shoes but also including accessories.   
One of the difficulties we anticipate is understanding the balance between historical sales and the seasonality of our product. For example, in March, we probably don’t want to recommend snow boots with the Vans that the customer recommended, even if it was highly correlated for that past couple of months.

Another difficulty is understanding at what level of our store hierarchy we have enough data to get a decent correlation (with other shoes) for 90-95% of the shoes sold. Our hierarchy is (from highest to lowest):
  
* Division
* Regions
* Districts
* Stores

A district typically has 10-15 stores, a region has 6-10 districts, and XXXXXX has 11 regions.

We feel that it would be best if the correlation happens at the store level. If there isn’t enough data at the store level, the data at the district level should then be considered. Then the region and then at the company level. We’d like to insert a “new” level of the hierarchy between districts and regions which is the State of the store (Arizona, New Jersey, etc.). The hierarchy order now becomes Store, District, State, Region, Company.

### DATA PROVIDED  
The Date Range of the data is 11/1/22 to 1/31/23.  
* products.csv – This is the product dimension. Join on DIV and STOCKNO to get the DEPARTMENT.
* store.csv – This is the store dimension. Join on DIV and STORE to get the District, Region and State.
* Departments.txt – A list of shoe/accessory departments
* Store Sales.csv – A list of all products sold by the stores during the date range. This will be the denominator of the 90-95% calculation.
* Nov Sold With.csv, Dec Sold With.csv, Jan Sold With.csv. These are the files that include the Primary Stockno and what Secondary Stocknos were sold with them at the store level. There is not a key on the table.

**Important columns:**
* Div
* Store – join with Div to store.csv to get region, district, state 
* Primary Stockno – Should be joined with the Div to the product dimension to get the department.
* Secondary Stockno - Should be joined with the Div to the product dimension to get the department.

### PROJECT GOAL 
We’d like the class to verify at what level(s) can we reach the 90-95% of all shoes sold in a store have 3-4 correlating shoe purchases and 2-3 correlating accessory suggestions, all based on the departments. For this exercise, a CORRELATION MEANS AT LEAST 3 PURCHASES. You have the freedom to choose a different correlation level based on what you find in the data. Please separate Shoe Suggestions from the Accessory Suggestions.  