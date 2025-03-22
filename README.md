# ETLandVisulizationProject

# What is the Raw Data?

The Transportation Security Administration (TSA) is an agency of the United States Department of Homeland Security responsible for the security of the traveling public. A claim is filed if you are injured or your property is lost or damaged during the airport screening process.

Our raw data consists of TSA Airport Claims and Enplanement data from 2013 through 2017. The data is provided as multiple SAS tables, which were used in the "Structured Query Language (SQL) using SAS" course on Coursera as the final project.

# Transformations

- **Remove Duplicates:**  
  Eliminate any entirely duplicate rows.

- **Incident Date vs. Date Received:**  
  Ensure the Incident Date always precedes the Date Received. Replace the year 2017 with 2018 in the Date Received column if it occurs before the Incident Date.

- **Missing Values:**  
  Treat all missing string values as "unknown."

- **Claim Type Normalization:**  
  If the Claim Type is separated by a slash (e.g. "Personal Property Loss/Injury"), consider only the first part (e.g. "Personal Property Loss").

- **Standardize Values:**  
  Ensure that Claim Type, Claim Site, and Disposition contain only a predefined list of possible values.

- **Proper Casing:**  
  Convert State Name, City, and County to proper case.

- **State Formatting:**  
  Format the State field in all uppercase.

- **Total Enplanements View:**  
  Create a view named "Total Enplanements" by concatenating the Enplanement2017 and Boarding2013_2016 tables.

- **Fact Table Integration:**  
  Incorporate Total Enplanement into the Fact Table to conform to the star schema and consolidate all key measures.

- **Avoid Redundancy:**  
  Only one row per Airport Code and Incident Year should contain the Total Enplanement value; all other rows for that combination should be set to 0.  
  - If a row holding the sole Total Enplanement value is deleted, transfer that value to another row with the same Airport Code and Incident Year.  
  - If no other row exists, create a new row with Claim Number set to "TEMP_AC_YR" to hold the Total Enplanement value.

- **Primary Key:**  
  Set Claim Number as the primary key by keeping only the rows with the latest status of claims (i.e., the most recent Date Received) in the Fact Table.

# Export

- **Export Format:**  
  Export the Fact and Dimension tables as CSV files, as SAS OnDemand for Academics does not support database connections.

- **Tableau Import:**  
  These CSV files can be directly imported into Tableau for visualization since Tableau Public does not support database servers.
