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
