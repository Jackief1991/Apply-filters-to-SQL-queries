# Apply-filters-to-SQL-queries

## **Project description**

Use SQL filters to retrieve records from different datasets including their employees and log_in_attempts and investigate potential security issues.

## **Retrieve after hours failed login attempts**

I noticed a potential security incident that involved multiple failed login attempts after 18:00 which is outside of normal business hours. 

First I need to investigate the log_in_attempts table and view the login_time. I use FROM log_in_attempts WHERE login_time > ’18:00’ AND success = FALSE; as shown in the screenshot:

 ![Commandlinesql](https://i.imgur.com/NDydq6m.png)


I started with the log_in_attempts table to filter for login_time and used the WHERE clause with the AND operator to filter the output results to only show me failed log in attempts that happened after 18:00 . Next I used login_time > ’18:00’ to filter for times that happened after 18:00. Then I used success = Flase condition to filter for failed login attempts.

## **Retrieve login attempts on specific dates**

There was a noticeable suspicious event on 2022-05-09. Any login activity that happened on or before this day should be investigated.

 ![commandlinesql](https://i.imgur.com/Hpit2XF.jpg)


This screenshot shows all login in attempts that occurred on 2022-05-08 or 2022-05-09. First, I started by getting the login_date from the log_in_attempts table. I did this by using the WHERE clause and the OR operator to filter results to output only the login in attempts made on those particular dates, this is shown as follows: WHERE login_date = ‘2022-05-09’ OR login_date = ‘2022-05-08’.

## **Retrieve login attempts outside of Mexico**

Based on the investigation so far, it looks like there might be and issue with the log in attempts that happened outside of Mexico. These attempts should to be investigated. 

 ![commandlinesql](https://i.imgur.com/bQiOkVn.jpg)


This screenshot shows all log in attempts that outside of Mexico. Using the data from the log_in_attempts table, I used a WHERE clause with the NOT operator to filter for countries other than Mexico. Using LIKE with MEX% helps filter for all countries that begin with MEX because the database stores it as both MEX and MEXICO. 

Note* The (%) represents any number of unspecified characters when used with LIKE.

## **Retrieve employees in Marketing**

Next, the team need to update the computers for the marketing department. I have to find which employee machines need to be updated.

 ![commandlinesql](https://i.imgur.com/covstQW.jpg)


I needed to start with all the data being selected from the employees table. Next, I used another WHERE clause with AND operator to filter employees working in the East building in the marketing department. Since the office column represents the east building with different office numbers, I must use LIKE with East% so it shows the match pattern for all East buildings. The condition department= ‘marketing’ show the employees in the Marketing department. The other condition office LIKE ‘East%’ shows the employees that work in the East buildings regardless of what number is on the building.

## **Retrieve employees in Finance or Sales**

Employees that work in the Finance and Sales departments also need to be updated. I need to get information on the employees that work in those to departments. 
 
 ![commandlinesql](https://i.imgur.com/PVcPBei.jpg)


All the data in from the employees table needs to be selected. Next, I use the WHERE clause with OR to filter for the employees in Finance and Sales departments. The OR operator is used instead of AND because I want all employees from either department. The section that shows department = ‘Finance’ filters for employees who work in the finance department. The other condition is department = ‘Sales’ and this filters for the employees working in the Sales department. 

## **Retrieve all employees not in IT**

Now I need to get information on all the employees who don’t work in the IT department so updates can be made. 

 ![commandlinesql](https://i.imgur.com/PIsl7vI.jpg)


I started with the data in the employees table and used the WHERE clause with NOT operator to filter for all the employees who don’t work in this department. 

## **Summary**

I was able to apply SQL filters to look for specific information from the two different tables used: log_in_attempts and employees. Operators used were AND, OR, and NOT with LIKE and (%) to filter for 
patterns.
