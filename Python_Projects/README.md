# Introduction Summary

This project involved analyzing clinical datasets from an AI-driven med tech company focused on cardiovascular imaging. Their work leverages artificial intelligence to improve diagnostic accuracy and enable early detection of coronary artery disease.

My approach began with transforming the raw data—converting JSON files into Excel format for easier handling and exploration. I then performed a detailed analysis of the inclusion, exclusion, and primary datasets to ensure structural consistency and data integrity.

### Key objectives included:

Demographic breakdowns by race, gender, and stenosis severity

Calcium score risk stratification

Evaluation of imaging machine manufacturers’ influence on results

Standardizing race and ethnicity categories in line with FDA guidelines

Through visualizations, tabular summaries, and structured insights, this analysis aimed to support better clinical decision-making, improve study design, and identify representation gaps in the data.


## 1. Converting jason file into Excel

#### Purpose of the code
The purpose of my code is to convert a JSON file into an Excel file. It reads the data from a JSON file at the specified path, loads it into a pandas DataFrame for easy tabular manipulation, and exports the data to an Excel file at the defined output location. This process transforms the JSON data into a more accessible and user-friendly format, making it suitable for analysis or sharing while preserving the integrity of the original dataset

<br> **Code**

import pandas as pd

##### Define the input JSON file path and output Excel file path
json_file_path = r"C:\Users\username\Documents\MedTechProject\data\clinical_dataset.json"  
excel_file_path = r"C:\Users\username\Documents\MedTechProject\outputs\clinical_dataset.xlsx"

##### Load the JSON file into a pandas DataFrame
data = pd.read_json(json_file_path)

##### Convert the DataFrame to an Excel file
data.to_excel(excel_file_path, index=False)

print(f"JSON file has been successfully converted to Excel and saved at: {excel_file_path}")

#### Output
C:\Users\username\Documents\MedTechProject\outputs\clinical_dataset.xlsx

<br>

## 2. Exploring the dataset using all three excel spreadsheets to provide a glimpse of its structure (e.g., are number of rows, columns, variable names, data types) and convreting and saving in to one excel spreadsheet as Combined dataset summary

#### Purpose of the code
I wrote this code to load three Excel datasets—primary, inclusion, and exclusion—and analyze their structure by examining key attributes such as the number of rows, columns, column names, data types, and missing values. After performing this analysis, I combined these datasets into a single Excel file, saving each dataset as a separate sheet. The final file is saved to a specified output path for further analysis or documentation.

 <br> **Code**
 
###### 2. Exploring the dataset using all three excel spreadsheets to provide a glimpse of its structure.

import pandas as pd

##### Define file paths
primary_excel_file_path = r"C:\Users\username\Documents\MedTechProject\data\clinical_primary_dataset.xlsx"  
inclusion_excel_file_path = r"C:\Users\username\Documents\MedTechProject\data\inclusions.xlsx"  
exclusion_excel_file_path = r"C:\Users\username\Documents\MedTechProject\data\exclusions.xlsx"  
output_excel_file_path = r"C:\Users\username\Documents\MedTechProject\outputs\combined_dataset_summary.xlsx"  

##### Load the Excel files
primary_data = pd.read_excel(primary_excel_file_path)  
inclusion_data = pd.read_excel(inclusion_excel_file_path)   
exclusion_data = pd.read_excel(exclusion_excel_file_path)  

##### Exploring the structure of each dataset
def explore_structure(data, name):  
    print(f"Dataset: {name}")  
    print(f"Number of rows: {data.shape[0]}")  
    print(f"Number of columns: {data.shape[1]}")  
    print(f"Columns: {list(data.columns)}")  
    print("\nData types:")  
    print(data.dtypes)  
    print("\nMissing values:")  
    print(data.isnull().sum())  
    print("\n")  

##### Explore each dataset
explore_structure(primary_data, "Primary Dataset")  
explore_structure(inclusion_data, "Inclusion Dataset")  
explore_structure(exclusion_data, "Exclusion Dataset")  

##### Combine the datasets into one Excel file with multiple sheets
with pd.ExcelWriter(output_excel_file_path) as writer:  
    primary_data.to_excel(writer, sheet_name="Primary Dataset", index=False)  
    inclusion_data.to_excel(writer, sheet_name="Inclusion Dataset", index=False)  
    exclusion_data.to_excel(writer, sheet_name="Exclusion Dataset", index=False)  

print(f"Combined dataset summary has been saved to: {output_excel_file_path}")

##### Output
![Python_Step2](/assets/img/Python_Step2.jpg)
![Python_Step2](assets/img/Python_Step2.jpg)
<br>
