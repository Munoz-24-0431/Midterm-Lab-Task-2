# [Midterm Lab Task 2](https://github.com/user-attachments/files/19143859/Midterm.Lab.Task.2.Munoz.xlsx) – Data Cleaning and Transformation
This repository contains my solution for Midterm Lab Task 2 on data cleaning and transformation. The task involves various steps for cleaning and reshaping a raw dataset related to job listings, including salary estimates, job roles, company sizes, and locations. The goal was to improve the data's structure and prepare it for analysis using Power Query in Excel.
## Step 1 - Data Loading and Duplication
**1.1 Load the Dataset:**
- Download the Uncleaned_DS_jobs.csv dataset.
- Open Excel and go to the Data tab.
- Choose New Query → Open File → Text/CSV.
- Select the file and load it into Power Query Editor.
  
**1.2 Duplicate the Raw Data:**
- Right-click on the raw data query in the Queries pane.
- Select Duplicate to create a copy of the original data for further processing.

## Step 2 - Data Cleaning Tasks
**a. Cleaning the Salary Estimate Column:**

**2.1 Remove Characters After Parentheses:**
- In the Transform menu, select Extract → Text Before Delimiter.
- Type ( as the delimiter and click OK to remove any characters after the parentheses in the Salary Estimate column.
  
**2.2 Create Min and Max Salary Columns:**
- Select the Salary Estimate column.
- Go to the Add Column tab → Column from Examples → From Selection.
- Type the first value (e.g., "101") for Min Sal in the first row and press Enter to fill the column.
- Rename the new column as Min Sal.
- Repeat the process for Max Sal (e.g., "500" for Max Salary) and rename it as Max Sal.
  
**b. Role Type Creation:**
**2.3 Group Job Titles into Categories:**

- Go to Add Column → Custom Column.
- In the dialog box, enter the following formula to categorize the job titles:

Copy:

if Text.Contains([Job Title], "Data Scientist") then "Data Scientist"

else if Text.Contains([Job Title], "Data Analyst") then "Data Analyst"

else if Text.Contains([Job Title], "Data Engineer") then "Data Engineer"

else if Text.Contains([Job Title], "Machine Learning") then "Machine Learning Engineer"
else "other"

- Rename the new column as Role Type and change its data type to Text.
  
**2.3 Fix Location Column:**

**c. Split Location by Delimiter:**

- If the Location column contains inconsistent delimiters (e.g., commas), create a Custom Column with a formula to normalize them:

Copy:

if [Location] = "New Jersey" then ", NJ"

else if [Location] = "Remote" then ", other"

else if [Location] = "United States" then ", other"

else if [Location] = "Texas" then ", TX"

else if [Location] = "California" then ", CA"

else [Location]

**2.4 Split Location into State Abbreviation:**
- Select the Location Correction column and choose Transform → Split Column by Delimiter → Comma.
- This will split the location into two new columns: Location Correction 1 and Location Correction 2.
- Rename Location Correction 2 to State Abbreviations.
  
**2.5 Clean Company Size Column:**

**d. Split Company Size:**

- Follow the same process used for the Salary Estimate column to create MinCompanySize and MaxCompanySize columns.
  
**2.6 Handle Negative Values and Errors:**
  
**e. Handle Negative Values in Competitors Column:**

- Filter out all -1 values in the Competitors column.
  
**f. Filter Zero Values in the Revenues Column:**
  
- Filter out all 0 values in the Revenues column.
  
**g. Handle Negative Values in the Industry Column:**
  
- Filter out all -1 values in the Industry column.
- 
**h. Remove Unnecessary Descriptions and Clean Company Names:**
  
**2.7 Remove Company Name Rates:**
- Clean the company names by removing any "Rates" after the company name in the Company Name column.
- Use Transform → Replace Values to remove any unwanted text.
  
**2.8 Remove Column Descriptions:**
- Delete any columns that are irrelevant to the analysis, such as descriptions or extra metadata.

## Step 3: Data Reshaping and Grouping

**3.1 Duplicate Raw Data for Aggregation:** 
- Right-click on the Unclean DS Jobs query and select Duplicate.
  
**3.2 Grouping by Role Type:**
- Click Choose Columns and select Role Type, Min Sal, and Max Sal columns.
- Change the data type of Min Sal and Max Sal to Currency.
- Multiply both columns by 1000 (go to Transform → Standard → Multiply and type 100).
- Group by Role Type and calculate the Min and Max salary averages.

**3.3 Grouping by Company Size:**
Right-click on the duplicated query and select Reference.
- Choose the Size, Min Sal, and Max Sal columns.
- Change data types and multiply the salary columns by 1000.
- Group by Size and calculate the average Min Sal and Max Sal.

## Step 4: Merging with Other Data Sources

**4.1 Mapping States:**
- Right-click on the Unclean DS Jobs query and select New Query → Open Workbook.
- Select the state mapping file and click OK.
- Merge the State Abbreviations column from both datasets.
- Rename the new column as State Full Name and filter out any null or blank values.

## Step 5: Final Grouping by State

**5.1 Group by State:**
- Create a Reference of the raw data (Right-click → Reference).
- Select State Full Name, Min Sal, and Max Sal columns.
- Change data types and multiply the salary columns by 1000.
- Group by State Full Name and calculate the average Min Sal and Max Sal.

## Step 6: Final Verification

**6.1 View Dependencies:**
- Go to View → Dependencies to verify the relationships between the queries.
- Ensure all queries (e.g., Sal by Role Type, Sal by Size, State, Sal by State) are correctly connected.

## Step 7: Final Queries and Export

**7.1 Ensure Final Queries:**

**Heres the screenshot of my output before I started data cleaning using power query (See Screenshot)**
**- Uncleaned DS Jobs**
![Image](https://github.com/user-attachments/assets/8054f4f6-20b2-4836-91b4-26d078980045)

**Heres the screenshot of my output after I started data cleaning using power query (See Screenshot)**
- **Cleaned DS Jobs**
![Image](https://github.com/user-attachments/assets/de88530f-2ea8-49b0-ad71-1de65967a8e9)

## YOUR FINAL QUERIES SHOULD INCLUDE THE FOLLOWING:

- **Sal by Role Type (dupl)**
![Image](https://github.com/user-attachments/assets/ef8dbfc2-54e6-4f92-9f60-05e2ee31459b)

- **Sal by Size (ref)**
![Image](https://github.com/user-attachments/assets/3bb6ee29-9cd4-4c55-905e-433cfd5b8d2d)

- **State**
![Image](https://github.com/user-attachments/assets/13908e99-6588-483f-8643-1a02af873648)

- **Sal by State (ref)**
![Image](https://github.com/user-attachments/assets/68139da5-18b3-4f90-8b07-da288ea5f51b)

- **Data Query Structure**
![Image](https://github.com/user-attachments/assets/2b7c2a74-7d8d-4dc9-b13f-95e8169ce62a)

- **Here's my Advance Editor**
![Image](https://github.com/user-attachments/assets/221b3b40-54e5-4737-829a-0578e304adfc)
  
