## Project Overview

This project was a freelance paid job the objective was to process survey data from the Survey Monkey website, perform data cleaning and merging operations, and export the final results into a CSV file. delivering a clean and usable dataset for the client. The output is optimized for analysis or visualization using tools like Tableau or Power BI, as was the client's needs

### Key Components:
1. **Excel Preprocessing** (Manual):
    - The raw data initially had two separate header rows. To improve usability and ensure compatibility with later stages, the two header rows were merged into a **Question - Subquestion** format for each column.
    - Two columns that had merged content were handled by associating them properly: One column represented a question, and the other column was used for specific answers. For instance, an "Other Specify" answer in one column was matched with the specific response in another column, allowing for cleaner data analysis.

### Notebook Workflow:

1. **Data Loading**:
   - The survey data was loaded into the notebook environment using **Pandas** for data analysis. The worksheet was imported after the manual Excel adjustments.

2. **Data Cleaning**:
   - Initial cleaning operations were performed to remove missing or inconsistent data, such as empty responses or erroneous entries.

3. **Merging Data**:
   - A key step in the notebook was the merging of two datasets:
     - The cleaned data (`data_cleaned`) was merged with another dataframe (`same_answer`) that contained response details, using the shared keys `Question - Subquestion` and `Answer`.
   - This process ensured that each survey response was aligned with its corresponding metadata and grouped under the appropriate questions and subquestions.

4. **Additional Columns**:
   - Two additional columns were created to further analyze the data:
     - **Total Respondents**: This column tracks the total number of employees who responded to a specific question.
     - **Same Answers**: This column counts how many people gave the same answer to a certain question. 
     - These columns are used to provide deeper insights into response patterns and answer distributions for specific questions.

5. **Final Dataframe**:
   - After the merge, the final dataset (`data_final`) was structured to include the columns: `Question - Subquestion`, `Answer`, `Respondent ID`, `Division`, `Total Respondents`, `Same Answers`, and others.

6. **Export to CSV**:
   - The processed data was exported to a CSV file (`Data_Survey_Monkey_Final.csv`), which can be used for further analysis or reporting.

### Benefits:
- The final dataset is now clear, easy to use, and ready for further analysis or visualization in tools such as **Tableau** or **Power BI**.
  
---

## Code Snippets and Commands:

1. **Merging Dataset**:
    ```python
    data_final = pd.merge(left=data_cleaned, right=same_answer, how='right', on=['Question - Subquestion', 'Answer'])
    ```

2. **Exporting Data**:
    ```python
    data_final.to_csv('Data_Survey_Monkey_Final.csv', header=True, index=False)
    ```

---

## License

This project is licensed under the **MIT License**. This means you are free to use, modify, distribute, and incorporate this project into your own work, provided that the original source is acknowledged. Full details of the license can be found in the `LICENSE` file.

---

