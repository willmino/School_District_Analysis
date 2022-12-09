
# School-District-Analysis

##Overview


##Purpose
- The purpose of this analysis was to help Maria, a chief Data scientist, with analyzing student standardized test data and presenting the findings and key insights to the county district. The takeaways from the analysis will help key make key decisions for each underlying school and the overall district.

- To help Maria, I read the standardized test data from csv format into jupyter notbook in a pandas dataframe format. We cleaned the data by looking for both missing values and duplicated information and then eliminated them. We analyzed the data by summarizing high level data statistics (such as min, max, mean, and sums of particular datasets) and drilled down into the data to identify subsets of interest. Finally, we made comparisons between subsets of interest to uncover some key insights pertaining to standardized testing.

## Analysis

- Before beginning the analysis, we loaded the csv file into the pandas dataframe in Jupyter Notebook. This was accomplished by:
`full_student_data = os.path.join('../Resources/new_full_student_data.csv')`
`student_df = pd.read_csv(full_student_data)`
`student_df.head()`
- The list line of code listed above allowed us to check if the data was successfully imported into a dataframe.
-We cleaned the data by looking for the total number of rows per column that had missing data: `student_df.isna().sum()`. This output showed that there was missing data for rows in the columns `student_df["reading_score"] and student_df["math_score"]`. 
So, we used the function `student_df = student_df.dropna()` to eliminate this missing data. The same process was repeated for finding duplicated data. To do this, we used `.duplicated.sum()` and `.drop_duplicates()` instead. Running the`.sum()` function was performed after eliminating the data and we verified that there was a zero value for missing data and dulicates.
 
-After cleaning the data, we were able to begin our analysis. We started by viewing a high level statistical summary of all data in the dataframe using the code: `student_df.describe()`. We could use the mean values in the columns for "reading_Score", "math_score", and "school_budget" to begin formulating what parts of the data we should drill down into. 




- One additional step of the analysis I wanted to perform was to group the student_df dataframe by "school_name" and "school_type". Then, I took the mean of these values and sorted them in descending order. The resulting dataframe was displayed as below.

![student_df.groupby](https://github.com/willmino/School_District_Analysis/blob/main/student_df.groupby.png)

- I liked this dataframe output because I could observe all of the schools and all of the corresponding, school types, reading scores, math scores, and school budgets. It appeared that the values listed in the "reading_score" column were pretty similar between Charter schools and Public schools. When you compare this table with the dataframe output below, we can observe the mean value for reading scores is marginally different comparing 72.45 at Charter Schools to 72.28 at Public Schools. Since the reading scores were so similar, it was not too interesting of a dataset to drill down into. However, there was a difference in the math scores at Charter schools compared to Public schools and I wanted to confirm why that might be. The average math score at Charter schools was 66.76 and the average at Public schools was 62.95. Charter schools most likely had a higher average math score because these schools receive funding that is distinct from the public state school system. Charter schools are exempt from the rules of the public school system and thus there success is more dependent upon student performance. We can see here that the Charter schools have a higher average math score and that this could  be the output that is required for these schools to receive the level of funding they need. Public schools do receive more funding but they most likely need to receive additional funds for extracurricular programs which charter schools might not deem as necessary to execute their primary function.

![schooltype_gb_mean](https://github.com/willmino/School_District_Analysis/blob/main/schooltype_gb_mean_.png)

- Drilling down even further into the math score data subset, we can see in the dataframe output below that the student math score by grade does not really have an influence on the total average math score. Even though grade 12 math scores at Charter schools are the lowest, Charter schools still have a higher math score for every other grade in addition to the Charter school overall higher math score.

![schooltype_grade_mathscore](https://github.com/willmino/School_District_Analysis/blob/main/schooltype_grade_mathscore.png)
When you compare this table with the dataframe output from Deliverable 5 question #3, as shown below, 


