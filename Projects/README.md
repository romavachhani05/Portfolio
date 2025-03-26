# Introduction Summary

Thank you for the opportunity to work on this assignment. I would like to take you through my step-by-step approach, starting with converting the file into a manageable format, exploring the data in each file, and leveraging creative analysis to extract valuable insights. My focus throughout the process was to ensure that the data representation and analysis provided maximum value to the business.

In this document, I detail my step-by-step analysis of clinical datasets to derive meaningful insights and actionable recommendations. I began by transforming the data, converting JSON files to Excel for better accessibility, and thoroughly exploring the dataset structures to gain a clear understanding of their content. I also ensured alignment and consistency across the inclusion, exclusion, and primary datasets to maintain data integrity and reliability.

The main objectives of my analysis included conducting demographic analysis, creating stratified views of race and gender by stenosis severity, categorizing calcium score risk levels, and assessing the impact of imaging machine manufacturers. I also focused on aligning race and ethnicity categories with FDA clinical trial standards. By using visualizations, tabular summaries, and enhanced data structures, I provided stakeholders with the insights needed to refine study criteria, address representation gaps, and make informed clinical decisions.
1. Converting JSON file into Excel (artrya_coding_interview_primary_dataset.xlsx)
Purpose of the code
The purpose of my code is to convert a JSON file into an Excel file. It reads the data from a JSON file at the specified path, loads it into a pandas DataFrame for easy tabular manipulation, and exports the data to an Excel file at the defined output location. This process transforms the JSON data into a more accessible and user-friendly format, making it suitable for analysis or sharing while preserving the integrity of the original dataset.

<br> **Code**
### 1. Converting jason file into Excel

import pandas as pd

##### Define the input JSON file path and output Excel file path
json_file_path = r"C:\Users\romap\OneDrive\Desktop\Artrya\Artrya CDM Coding Assignment\artrya_coding_interview_primary_dataset.json"
excel_file_path = r"C:\Users\romap\OneDrive\Desktop\Artrya\Artrya CDM Coding Assignment\artrya_coding_interview_primary_dataset.xlsx"

##### Load the JSON file into a pandas DataFrame
data = pd.read_json(json_file_path)

##### Convert the DataFrame to an Excel file
data.to_excel(excel_file_path, index=False)

print(f"JSON file has been successfully converted to Excel and saved at: {excel_file_path}")


<br>
