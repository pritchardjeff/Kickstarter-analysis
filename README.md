# Kickstarting with Excel

## Overview of Project

A close friend recently launched a failed fundraising campaign on kickstarter and asked for assitance to better understand how similar campaigns fared in relation to their launch dates and funding goals. The analysis leverages Microsoft Excel and uses historical fundraising campaigns to uncover trends and insights related to both launch date and funding goals. Based on accessible data, it seems like the best time of the year to lauch campaigns in the Theater Category is May or June and the most successful plays tend to have a fund raising goal of less than $5,000.

The analysis is the file below:
[Kickstarter_Challenge.zip] (https://github.com/pritchardjeff/Kickstarter-analysis/blob/master/Kickstarter_Challenge.zip)

### Purpose

To determine the impact of the launch month and goal/funding amount on the outcome of Kickstarter campaigns related to theater and plays.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
 
## Purpose

To visualize trending outcomes for the Theater category by month

## Steps
- Added a column for Year using the Year() to the original data set
- Create a pivot table
- Add a filter for Year and Parent Category
- Set Parent Category to theater
- Populate the rows with the Date Created Conversion
- Remove quarters and years from the pivot table so only the months are showing
- Add outcomes to the column field of the pivot table
- Sort in Descending order to Successful is the first column of the pivot table
- Add Count of Outcomes to the Value field of the pivot table
- Add a Pivot Chart
- Add a title to the pivot chart

## Result

Following these steps will result in the following graph: 
![Theater_Outcomes_vs_Launch.png] (https://github.com/pritchardjeff/Kickstarter-analysis/blob/master/Theater_Outcomes_vs_Launch.png)


### Analysis of Outcomes Based on Goals

## Purpose

To visualize the outcome based on the goal amount.

## Steps
- Add a new sheet and rename it outcomes based on goals
- Add the following columns: Goal, Number Successful, Number Failed, Number Canceled, Total Projects, Percentage Successful, Percentage Failed, Percentage Canceled
- Add the following rows: Less Than 1000, 1000 to 4999, 5000 to 9999, 10000 to 14999, 15000 to 19999, 20000 to 24999, 25000 to 29999, 30000 to 34999, 35000 to 39999, 40000 to 44999, 45000 to 49999, Greater Than 50000
- Categorize the underlying data based on the rows referenced in Step 3. See Challenges and Difficulties for more detail.
- Populate countif statement as follows: =COUNTIFS(Goal Category Column, Goal Category, Subcategory Column, Plays, Outcome Column, Outcome)
- Populate the Total Projects column with a sum function referencing the cells in the Number Successful, Number Failed, and Number Canceled columns
- Populate the three remaining columns starting with the following formula =iferror(B2/$E2,0) and copy it into the remaining cells. Don't forget to do an absolute column reference on cell E2.
- Add a visualization by selecting the data in the table for Goal, Percentage Successful, Percentage Failed, and Percentage Canceled.

## Result

Following these steps will result in the following graph: 
![Outcomes_vs_Goals.png] (https://github.com/pritchardjeff/Kickstarter-analysis/blob/master/Outcomes_vs_Goals.png)

### Challenges and Difficulties Encountered

While performing the Analysis of Outcomes Based on Goals, one may encounter some difficulty on categorizing goals based on category. Doing so manually may result in errors.

In order to overcome this challenge dynamically, I recommend adding a Reference sheet with a look up table that can be used to categorize goal amounts based on dollar amount.
Example. Goal lookup - 0, Goal Category - Less Than 1000; Goal lookup - 1000, Goal Category - Less Than 1000 to 4999; ... ; Goal lookup - 50,000, Goal Category - Greater Than 50000.
After the table is set up, add an additional column with a vlookup. 

The fields should be populated as followed:
Lookup_value = Goal Amount
Table Array = Reference table added above
Col_Index = 2
Range Lookup = 1

Note - Range lookup with 1 sets the formula up to use an approximate match instead of an exact match, which returns a value that is less than the value you are interested in.

Once the Goal Category column is added, it can be used for your countifs and you can change the reference table if you would like to adjust your goal ranges dynamically.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- In the theatre category from 2009 to 2017, December seems to be the worst month to launch a campaign.
- In the Theatre category From 2009 to 2017, May and June tend to have the most successful campaigns.

- What can you conclude about the Outcomes based on Goals?

- In the Plays subcategory, campaigns with goals of less than $5,000 had the highest Success rate.

- What are some limitations of this dataset?

Does not provide a full picture about the backers of the campaigns. It would be interesting to receive another data set that includes a unique identifier for each backer, the campaigns they've funded, amounts funded, the date the campaigns were funded, location, etc..
With that data, we could gain more insight into who the backers are and into the specific geographic region (City/State) we are trying to launch a play for. 

- What are some other possible tables and/or graphs that we could create?
-We could add a column to the original data set that takes the difference between Date Created and Date Ended and determine if there is a relationship between the success of a campaign and its duration.

