# Pewlett-Hackard-Analysis
## Overview

In this analysis, we are working with a large corporation called Pewlett-Hackard. As a large corporation, Pewlett-Hackard has many thousands of employees. With many people from the "baby boomer" generation approaching retirement age, the company is concerned with being well-prepared to fill the vacancies in their workforce that they expect to arise in the near future.

In order to prepare for this, they would like to identify employees who are most likely to retire soon based on age. They can then use a two-pronged approach: offer some employees retirement packages when they are prepared to hire someone to replace them, or ask some senior employees to transition to a part-time mentoring role to help employees who will be promoted to their former positions.

In order to identify these populations of interest within their workforce, we can query the various databases that the company has with relevant information about each employee. These queries will help to narrow down the large sets of data to target the employees who meet the desired criteria for their retirement package and mentorship plans.

### Resources

    - Data: departments.csv, dept_emp.csv, dept_manager.csv, employees.csv, salaries.csv, titles.csv
    - Software: pgAdmin4 v6.12, PostgreSQL v11.17, quickdatabasediagrams.com

## Results

Throughout the course of this module, we constructed an entity relationship diagram (ERD) of the raw employee data from Pewlett-Hackard using the tools from quickdatabasediagrams.com, constructed a database in pgAdmin4 from the raw employee data, and from there were able to query the databsae to derive the data of interest for this project. Through this process, we derived four tables of information that Pewlett-Hackard needs to establish the retirement packages and mentorship programs they have planned.

![retirement_titles](https://github.com/tfish110/Pewlett-Hackard-Analysis/blob/main/resources/retirement_titles_head.png)

- This image contains the first several rows of the first table we derived. It contained all employees in the database who were born between 1952-1955, listed the titles the held, and the dates they held those titles. This table was not sufficient for two main reasons. First, it contained employees born in those years who were no longer working at Pewlett-Hackard. Second, many employees had multiple entries in this table, as they have held multiple titles during their time with the company and each of them was listed in its own row.

![unique_titles](https://github.com/tfish110/Pewlett-Hackard-Analysis/blob/main/resources/unique_titles_head.png)

- This is an image of the first several rows of the table we derived from narrowing the scope of the table above. In it, we eliminated all employees no longer with the company. We also eliminated duplicate entries for current employees leaving only their current title.

![retiring_titles](https://github.com/tfish110/Pewlett-Hackard-Analysis/blob/main/resources/retiring_titles.png)

- While the second table did narrow down the data to only what we needed to know about current employees approaching retirement, it still contained several thousand rows of data since it is such a large company. So, we were able to use a "count" function to determine how many employees per title fall into the retirement age bracket that Pewlett-Hackard is interested in.

![mentorship_eligibility](https://github.com/tfish110/Pewlett-Hackard-Analysis/blob/main/resources/mentorship_eligibility_head.png)

- The final table went back to deriving a table from the raw dataset. This time, we built a table containing only current employees born in 1965 and their current titles. As they are about 10-13 years younger than the set of employees being targeted for retirement age, they would be a good place to start looking for the mentees for the mentorship program to step up and fill the leadership positions of those getting ready to retire.

## Summary

From the specialized tables that we derived from the raw data, we can see that the "silver tsunami" of upcoming retirees that Pewlett-Hackard expects will include up to 72,458 employees. This number is dervied from the sum of the counts for each title that current employees born between 1952-1955 hold.

Based on our target birth year of 1965 to identify employees eligible for mentorship by those nearing retirement, it seems Pewlett-Hackard has a a good start to finding pool of employees to select quality mentees. The table we created for employees born in just 1965 contains 1,549 employees.

It seems clear that Pewlett-Hackard will likely need to expand their search for employees eligible for mentoring beyond those born only in 1965. If they would like to fill leadership positions for those born in a four year range, they should be looking for at least a four year range for the birth years of those to replace them, not just a single year. It would seem prudent to set 1965 as the earliest year for mentees, as they want their new leaders to spend a significant amount of time in their positions before reaching retirement age themselves. So, to find employees at least a decade younger than those expected to retire, creating a table for those born between 1965-1968 might be a better place to start.

Another major consideration might be to factor in what we know about generational demographics as a whole. The very idea of a "silver tsunami" is based on the idea that the early-to-mid 1950s was the height of the baby boom, when there was a sizeable spike in the birthrate. So, we should expect that there are simply more people born in those four years that were selected from 1952-1955 than any other four year stretch among their current employees. We could create a another table with a "count" function to simply find out how many of their current employees were born in each year, and chart out when there are spikes in the birthrate among their own employees as a sample of the population at large. This would also help to future-proof against further spikes in retirements be finding out now how demographic shifts between generations might cause a similar problem decades down the line.
