
# School-District-Analysis

##Overview


##Purpose
- The purpose of this analysis was to help Maria, a chief Data scientist, with analyzing student standardized test data and presenting the findings and key insights to the county district. The takeaways from the analysis will help key make key decisions for schools within this district.

- To help Maria, I read the standardized test data from csv format into jupyter notbook in a pandas dataframe format. We cleaned the data by looking for both missing values and duplicated information and then eliminated them. We analyzed the data by summarizing high level data statistics (such as min, max, mean, and sums of particular datasets) and drilled down into the data to identify subsets of interest. Finally, we made comparisons between subsets of interest to uncover some key insights pertaining to standardized testing.

## Analysis

- Before beginning the analysis, we loaded the csv file into the pandas dataframe in Jupyter Notebook. This was accomplished by:

`full_student_data = os.path.join('../Resources/new_full_student_data.csv')`

`student_df = pd.read_csv(full_student_data)`

`student_df.head()`

- The list line of code listed above allowed us to check if the data was successfully imported into a dataframe.
-We cleaned the data by looking for the total number of rows per column that had missing data: `student_df.isna().sum()`. This output showed that there was missing data for rows in the columns `student_df["reading_score"] and student_df["math_score"]`. 
So, we used the function `student_df = student_df.dropna()` to eliminate this missing data. The same process was repeated for finding duplicated data. To do this, we used `.duplicated.sum()` and `.drop_duplicates()` instead. Running the`.sum()` function was performed after eliminating the data and we verified that there was a value of zero for missing data and dulicates in all of the dataframe columns.
 
- After cleaning the data, we were able to begin our analysis. We started by viewing a high level statistical summary of all data in the dataframe using the code: `student_df.describe()`. We could use the mean values in the columns for "reading_Score", "math_score", and "school_budget" to begin formulating what parts of the data we should drill down into. First we found that the average reading score of all 9th graders was 69.2. We found that the lowest reading score out of any student in the district was from 10th grader Matthew Thomas, whose reading score was 10.5. I performed an additional analysis to observe the average reading scores of all 10th graders at Dixon High School. The average reading score of 10th graders at this high school was 67.8 which was considerably lower than the average reading score of all 9th graders. This could imply something about the quality of reading education at Dixon High Scool. Furthermore, after drilling down into the dataframe specifically for the 11th and 12th grade student reading scores, the average reading score for all of these students was higher than any previously observed reading score at 74.9. This value further proves a point that Dixon High School may want to evaluate its reading education platform. This figure for 11th and 12th grade average student reading score was also higher than the average reading score of all 9th graders which had an average reading score value of 69.2. 


## Additional Analysis

- One additional step of the analysis I wanted to perform was to group the student_df dataframe by "school_name" and "school_type". Then, I took the mean of these values and sorted them in descending order. The resulting dataframe was displayed as below.

![student_df.groupby](https://github.com/willmino/School_District_Analysis/blob/main/student_df.groupby.png)

- I liked this dataframe output because I could observe all of the schools and all of the corresponding, school types, reading scores, math scores, and school budgets. It appeared that the values listed in the "reading_score" column were pretty similar between Charter schools and Public schools. When you compare this table with the dataframe output below, we can observe the mean value for reading scores is marginally different comparing 72.45 at Charter Schools to 72.28 at Public Schools. Since the reading scores were so similar, it was not too interesting of a dataset to drill down into. However, there was a difference in the math scores at Charter schools compared to Public schools and I wanted to confirm why that might be. The average math score at Charter schools was 66.76 and the average math score at Public schools was 62.95. Charter schools most likely had a higher average math score because these schools receive funding that is distinct from the public state school system. Charter schools are exempt from the rules of the public school system and thus their success is more dependent upon student performance. We can see here that the Charter schools have a higher average math score and that this could be the output that is required for these schools to receive the level of funding they need. Public schools do receive more funding but they most likely need to receive additional funds for extracurricular programs which charter schools might not deem as necessary to execute their primary function.

![schooltype_gb_mean](https://github.com/willmino/School_District_Analysis/blob/main/schooltype_gb_mean_.png)

- Drilling down even further into the math score data subset, we can see in the dataframe output below that the student math score by grade does not really have an influence on the total average math score. Even though grade 12 math scores at Charter schools are the lowest, Charter schools still have a higher math score for every other grade in addition to the Charter school overall higher math score. This is because Charter Schools had a grade 9 average math score of 70, grade 10 average math score of 66, and grade 11 average math score of 68. This was compared to the Public School grade 9 average math score of 64, grade 10 average math score of 64, and grade 11 average math score of 59. One caveat to this dataset was that the Charter School grade 12 average math score was 60 compared to the Public school grade 12 average math score of 64. Despite this difference in grade 12 student math scores, this did not have a negative impact on the the Charter Schools overall higher average math score.

![schooltype_grade_mathscore](https://github.com/willmino/School_District_Analysis/blob/main/schooltype_grade_mathscore.png)

##Summary

- We found that Dixon high school had one of the lowest 10th grade reading scores in the district. The reading scores for this school's 10th graders was lower than the reading score which was specifically for all 9th graders and also lower than the reading score specifically for all combined 11th and 12th graders. This was also accompanied by the lowest reading score in the entire district coming from a 10th grade student at Dixon High School. We suggested to Maria that Dixon High School should re-evaluate the curriculum for its reading education program.

- Additional analysis showed that Charter schools had overall higher math scores compared to Public Schools. We even drilled down in this data subset to show that Charter school students from grades 9, 10, and 11 each had higher average math scores than Public school students from the same grades. This data suggests that public schools may want to re-allocate their funds to help improving mathematics education in an effort to improve student math scores.
