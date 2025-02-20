# Nurse_Staffing_Payroll_Analytics
Analyzing Payroll Based Journal (PBJ) Daily Nurse Staffing data to assess staffing trends across nursing homes in the U.S. Identifying high-demand regions for contractor staffing by calculating contractor-to-employee ratios and correlating staffing levels with quality ratings.
## processing stages:
1.Upload the data and explore it
After downloading the data set, I started to work with it in python.

First, I load the csv dataset and turned it into a Pandas data frame.
Then I ran some code on the data frame to get more familiar with the data set.
The dataset has 1330966 rows, and 33 columns.

After that, I calculated statistical facts(count, mean, std, min, max,…) for every numerical column.(more detailed information is included with the code.)

and then I Calculated all providers names and counts.

2.Preprocess the data 
The purpose of preprocessing the data is to clean the data in a way that we can work better with it and gain more accurate results. I started by cleaning the data. First delete unnecessary columns for the processing. The CY_Qtr column was deleted because all data from this dataset belonged to the last quarter.
Now the data has 32 columns. There are 2 types of data, categorical data and numerical data.

Then, I added 3 new columns:
Hrs_total which represent the total hours of work of all kinds of staff.
Which is the sum of these columns:
['Hrs_RNDON', 'Hrs_RNadmin', 'Hrs_RN', 'Hrs_LPNadmin', 'Hrs_LPN', 'Hrs_CNA', 'Hrs_NAtrn', 'Hrs_MedAide']

Hrs_total_emp which represent the total hours of work of all employees of any kind.
Which is the sum of these columns:
['Hrs_RNDON_emp', 'Hrs_RNadmin_emp', 'Hrs_RN_emp', 'Hrs_LPNadmin_emp', 'Hrs_LPN_emp', 'Hrs_CNA_emp', 'Hrs_NAtrn_emp', 'Hrs_MedAide_emp']

And Hrs_total_ctr which represent the total hours of work of all contractors of any kind.
Which is sum of these columns:
 ['Hrs_RNDON_ctr', 'Hrs_RNadmin_ctr', 'Hrs_RN_ctr', 'Hrs_LPNadmin_ctr',  'Hrs_LPN_ctr', 'Hrs_CNA_ctr', 'Hrs_NAtrn_ctr', 'Hrs_MedAide_ctr']

Now the data set has 35 columns.

The next step in cleaning the data is to deal with non-values. For the purpose of this task the none-values has replaced with 0s.
There is a column in the data set that represents the date: WorkDate. This column is saved as a string value. So, it had to change to a date time data type so that it can be used in the tables and graphs.



3. visualization
Using tables and charts to visualize the data

4. recommendations
4.1. I wanted to find out top providers in every state to become aware of our most powerful competitors in each state and also how many hours of work they provide. 
To answer this question, I group the information first by state and then by provider.  then I calculate the sum of these 3 columns ('Hrs_total', 'Hrs_total_emp', 'Hrs_total_ctr’) for each state, provider. After that, I sort the information based on the state and total hours. Now we have a dataframe of 5 columns which show us the top providers in each state and how many hours of work they reported in 3 categories of employees, contracts, and total.
This is a schema of the dataframe. The whole dataframe has been saved as a csv file and is attached to the report.
 
 
As we can see in this schema, in Wyoming the top 3 providers are: THE LEGACY LIVING AND REHABILITATION CENTER with total working hours of 47905.93, total employee working hours of 38128.84 and total contract working hours of 9777.09, SHEPHERD OF THE VALLEY REHABILITATION with total working hours of 45460.50, total employee working hours of 45460.50 and total contract working hours of 0, and LIFE CARE CENTER OF CHEYENNE with total working hours of 35551.05, total employee working hours of 35551.05 and total contract working hours of 0.
This information can be found about any provider in each state that can help us with organizing our staff accordingly in each state. It can also help us recognized our most powerful competitors and how well they have performed during the last quarter.
The number of working hours every provider reported in each state can lead us to manage our staff better for the future according to the needs of each state.

4.2. Since our focus in the clipboard company is more on the contracts, I created another table that includes the maximum total hours of contract work for each state. This table can show us which state is in more need for contract staff and how we can focus on them by providing more staff in those state or concentrating on advertisement in those states.
To calculate the maximum contract hours in each state, first I grouped the data by state. And then calculate the maximum of total contract hours for each state. Lastly, I sorted the information based on total contract hours decreasing.
This table is also saved and attached to the report.
Here is a chart that represent the maximum total contract hours in each state in the last quarter:
 
As we can see in the chart Pennsylvania and New York are the two state that needed the most contract staff by far during the last quarter. After these two, Michigan, Florida and New Hampshire are the most profitable states for the contract work. On the other hand, Puerto Rico is the least profitable state, which means that we should invest less on this state for the future.

4.3. For this recommendation I wanted to work with the specific data from clipboard, but there was no provider under this name in the dataset.
So, I just choose a random provider to work with its data and visualize them. The provider I chose is PARKVIEW CARE CENTER.
First all the rows containing information about this provider has selected. Then the information has grouped by the state. After that, the sum of total hours, total employee hours and total contract hours has calculated over each state. Then the information has sorted based on total working hours.
This table shows total working hours of the staff of PARKVIEW CARE CENTER for each state in 3 categories of total, employee and contract.
 
This table shows that PARKVIEW CARE CENTER has been active in only 5 states during the last quarter. It has the most working hours in Indiana with 24724.13 hours, which belong to employee works only since the contract work in this state is 0 for this provider. 
The first 3 states that has the most working hours for this provider are Indiana, Colorado and Iowa. Their total working hours are solely based on the employee works.
On the other hand, this provider hasdone more contract in Minnesota and Ohio. The number are total working hours in these states are 9809.50 and 8520.75 respectively. And these two states have the most contact working hours of 1657 and 2191.
This information can lead us to how we would want to organize our budget for these states either based on how we operate during the last quarter or the potential each state has and how we can profit from it.
Here is a chart that shows total working hours of PARKVIEW CARE CENTER staff in each state.
 

And since here in clipboard our focus is on the contract work, here is another chart that shows total contract working hours of PARKVIEW CARE CENTER staff in each state.
 
4.4. this recommendation focusses more on the type of nurses. To show what types of nurses have been more in demand. So that we can focus and invest on those types of nurses more than other. Either in employments or advertisements.
To visualize the needed information, I calculated the sum of each group of nurses. Here is the table of results:
 
This table show us that CNA has been in the most demand in the United States during the last quarter. And after that CAN as employees, LPN, LPN as employees, RN and RN as employees, are respectively the most wanted types of staff.
It also reveals that least wanted staff are contact nurse aide in training, contract LPN with admin duties and contract RN director of nursing.
This information can guide us for future references when we want to interview and employ new staff. And also, can be helpful how we can manage our staff based on needs and in which category we might need more staff.
This is the bar chart of total working hours of each type of nurses during the last quarter:

 
This chart also illustrates the need for each kind of staff in the United States During the last quarter. As it can be seen there is a huge difference between the need for each kind of staff that can be very helpful in managing the staff and be aware of market needs for future organizing purposes.
Again, since our focus is on the contract work, I made a table of the total contract working hours of each kind of nurses as well.
This table shows the types of nurses that has the most contract working hours during the last quarter in the United States.
 
As we can see in this table the most needed kind of contract workers are CAN, LPN and RN. And the least needed ones are nurse aide in training, LPN with admin duties and RN director of nursing
Here is the bar chart that illustrate this information:
 
This chart also shows how the need for CAN, LPN and RN contract staff is much more prominent than any other types of contract workers. Which is a very helpful guide for us to make our decisions based on for the future references.

