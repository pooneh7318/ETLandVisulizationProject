# ETLandVisulizationProject

What is the raw data?
The Transportation Security Administration (TSA) is an agency of the United States Department of Homeland Security that has authority over the security of the traveling public. A claim is filed if you are injured or your property is lost or damaged during the screening process at an airport. 
Our raw data consists of TSA Airport Claims and Enplanement data from 2013 through 2017.
The data is available as multiple SAS tables in the “Structured Query Language (SQL) using SAS” Course in Coursera as the final project of the course.

Transformations: 
Any entirely duplicate row should be removed from the data
Incident Date should always occur before Date Received, Therefore replacing the year 2017 with 2018 in the Date Received column where it is before Incident Date
All string missing values should be considered unknown
If the Claim Type is separated into two types by a slash, Claim Type is the first type. For example: Personal Property Loss/Injury is considered Personal Property Loss.
Claim Type, Claim Site, and Disposition have a list of possible values
State Name, City, and County should be in proper case
State should be in all upper case
A view named Total Enplanements by concatenating the Enplanement2017 and Boarding2013_2016 tables
Incorporate Total Enplanement into the Fact Table to conform to the star schema and keep all the key measures in a single fact table
To avoid redundancy, only one row per Airport Code and Incident Year holds the Total Enplanement value; all other rows for that same combo are set to 0.
In this case, we should be aware that if we attempt to delete a row holding the only value for Total Enplanement, the value should be passed to another row with the same Airport Code and Incident Year. If there is no other row left, a new row will be created with Claim Number set to “TEMP_AC_YR” to hold the Total Enplanement value
Make Claim Number the primary key by maintaining only the rows with the last status of claims (latest Date Received Date) inside Fact Table

Export:
Export Fact and Dimension tables into CSV files since SAS OnDemand for Academics doesn’t support database connections
CSV files can be directly imported to Tableau for visualization since again Tableau Public doesn’t support database servers 


