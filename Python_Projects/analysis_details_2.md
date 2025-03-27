## 6. Create a new column that contains the first five numeric characters from the mod_patient_id field. This is representative of the patient's site of treatment
#### Purpose of the code
The purpose of the code below is to process a dataset by extracting the first five numeric characters from the mod_patient_id column to create a new column called site_of_treatment, which represents the patient’s site of treatment. I first ensured that the mod_patient_id column exists in the dataset. Then, I applied a function to extract the numeric characters and added them as a new column. Finally, I saved the updated dataset to an Excel file and displayed the first few rows of the modified dataset to verify the changes. This approach allows me to identify treatment sites in a structured and easily accessible format.

**Code**  
import pandas as pd

#### Load the dataset
file_path = r"C:\Users\username\Documents\MedTechProject\data\clinical_primary_dataset.xlsx"  
data = pd.read_excel(file_path)  

#### Ensure the 'mod_patient_id' column exists  
if 'mod_patient_id' not in data.columns:  
    raise ValueError("The dataset must contain the 'mod_patient_id' column.")  

#### Create a new column with the first five numeric characters from 'mod_patient_id'  
def extract_site_id(mod_patient_id):  
    # Extract the first five numeric characters  
    numeric_characters = ''.join(filter(str.isdigit, str(mod_patient_id)))  
    return numeric_characters[:5] if len(numeric_characters) >= 5 else None  

data['site_of_treatment'] = data['mod_patient_id'].apply(extract_site_id)  

#### Save the updated dataset  
output_file = r"C:\Users\username\Documents\MedTechProject\outputs\updated_dataset.xlsx"  
data.to_excel(output_file, index=False)  

#### Display the first few rows of the updated dataset  
print(data[['mod_patient_id', 'site_of_treatment']].head())  
print(f"Updated dataset with 'site_of_treatment' column saved to: {output_file}")  

#### Output
![python_step6](assets/img/python_step6.jpg)

## 7.Demographic Analysis and Visualization of Patient Data
The purpose of the code below is to analyze and visualize the demographics of the dataset, focusing on the distribution of age, gender, and race among patients categorized as "Included," "Excluded," or "To Be Determined" (TBD). I ensured that all necessary columns for the analysis were present, and the visualizations generated highlight patterns, trends, or disparities in these demographic groups. Additionally, I saved a summary table with descriptive statistics for age into an Excel file to allow for further analysis or reporting.

I carefully designed the graph selection to provide clear and actionable insights. For gender distribution, I used a bar chart to offer a straightforward comparison of male and female patients across inclusion categories, making it easy to spot potential disparities in representation. Similarly, I used another bar chart to display the racial composition across inclusion categories, highlighting any over- or under-representation of specific racial groups and supporting diversity analysis. For age distribution, I replaced the histogram with a box plot to better summarize the data. The box plot makes it easier to identify the median, interquartile range, and outliers in age for each inclusion category, enabling a more precise comparison between groups.

These visualizations are intuitive and actionable, providing clinicians or study coordinators with valuable insights to refine inclusion criteria, address representation gaps, and ensure a diverse and equitable population in clinical studies.

**Code**

import pandas as pd  
import matplotlib.pyplot as plt  
import seaborn as sns  

#### Load the dataset  
file_path = r"C:\Users\username\Documents\MedTechProject\outputs\primary_data_categorized.xlsx"  
data = pd.read_excel(file_path)  

#### Ensure necessary columns exist  
required_columns = ['age_generated', 'sex', 'race_mapped', 'category']  
missing_columns = [col for col in required_columns if col not in data.columns]  
if missing_columns:
    raise ValueError(f"The following columns are missing: {', '.join(missing_columns)}")  

#### Distribution of Gender using bar graph  
plt.figure(figsize=(8, 5))  
sns.countplot(data=data, x='sex', hue='category', palette='Set2')  
plt.title('Gender Distribution by Study Inclusion/Exclusion', fontsize=14)  
plt.xlabel('Gender', fontsize=12)  
plt.ylabel('Count', fontsize=12)  
plt.legend(title='Category', labels=['Included', 'Excluded', 'TBD'])  
plt.grid(axis='y', linestyle='--', linewidth=0.7)  
plt.show()  

#### Distribution of Race using bar graph  
plt.figure(figsize=(10, 5))  
sns.countplot(data=data, x='race_mapped', hue='category', palette='coolwarm')  
plt.title('Race Distribution by Study Inclusion/Exclusion', fontsize=14)  
plt.xlabel('Race', fontsize=12)  
plt.ylabel('Count', fontsize=12)  
plt.legend(title='Category', labels=['Included', 'Excluded', 'TBD'])  
plt.xticks(rotation=45)  
plt.grid(axis='y', linestyle='--', linewidth=0.7)  
plt.show()  

#### Distribution of Age using Box Plot  
plt.figure(figsize=(10, 6))  
sns.boxplot(data=data, x='category', y='age_generated', palette='muted')  
plt.title('Age Distribution by Study Inclusion/Exclusion', fontsize=14)  
plt.xlabel  

#### Output

![python_step7.1](assets/img/python_step7.1.png)
![python_step7.2](assets/img/python_step7.2.png)
![python_step7.3](assets/img/python_step7.3.png)
