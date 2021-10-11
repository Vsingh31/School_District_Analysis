# School_District_Analysis

##**Overview of the school district analysis**
The Purpose of this analysis is to help the school board and verify that is there any academic dishonesty happened or not?They have a doubt that file  students_complete.csv has been altered.So specifically,I will check reading and math grades for Thomas High School ninth graders data to verify that students_complete.csv file have been altered or not.And if it is altered then what impact we can see because of this change.So i can explain the school board to the full extent of the academic dishonesty.for this,I am going to replace the math and reading scores for Thomas High School with NaNs while keeping the rest of the data intact. Once I will replace the math and reading scores, then i will repeat the school district analysis that i did in this module and provide a report that describe how these changes affected the overall analysis.  


###**Results**

* In the District Summary,I recalculated the total student count by subtracting the number of ninth-grade students in Thomas High School from the total student count,then I recalculated the passing math and passing reading percentages, and the overall passing percentage with the recalculated total student count. By altering the total student count,I saw passing math and passing reading percentages increased by some tenths percentage and the overall passing percentage increased by almost 1 percentage.

![image](https://user-images.githubusercontent.com/90277142/136711953-5d9efc62-c474-4438-a8cf-79b300b08e7c.png)



* In the school summary,when i executed the code from this module,in my  school summary dataframe Thomas High School metrics look like this:

 ![image](https://user-images.githubusercontent.com/90277142/136710874-51947211-d58b-4f5e-a7be-371301f58407.png)
 
After that i updated the school summary using the 10th-12th graders from Thomas High School as follows:
First, I calculated the number of 10th-12th graders in Thomas High School withis code :
THS_10_12grade_count = student_data_df.loc[ (student_data_df["grade"] != "9th")  & (student_data_df["school_name"] == "Thomas High School")]["student_name"].count()
THS_10_12grade_count

Then I Created three new DataFrames for the 10th-12th graders from Thomas High School: students who passed math, students who passed reading, and students who passed both math and reading.Using these DataFrames, I recalculated the percentage of students who passed math, passed reading, and passed both math and reading for Thomas High School only.In my code I used three conditional statement with logical operator to get only 10th-12th grade students passing math,passing reading and passing both math and reading for Thomas High School. I used "!=" operator with 9th grade,so i want student who is not in 9th grade means i got 10-12th grade passing student of Thomas high school.Then i calculated percentage of  students who passed math, passed reading, and passed both math and reading for Thomas High School. My code for this is:

**Calculate the percentage of 10th-12th grade students passing math from Thomas High School.** 
THS_10_12grade_passing_math = student_data_df.loc[ (student_data_df["grade"] != "9th")  & (student_data_df["school_name"] == "Thomas High School") & (student_data_df["math_score"] >= 70 )]["student_name"].count()
THS_10_12grade_passing_math_percentage =  THS_10_12grade_passing_math / THS_10_12grade_count * 100
THS_10_12grade_passing_math_percentage

**Calculate the percentage of 10th-12th grade students passing reading from Thomas High School.**
THS_10_12grade_passing_reading = student_data_df.loc[ (student_data_df["grade"] != "9th")  & (student_data_df["school_name"] == "Thomas High School") & (student_data_df["reading_score"] >= 70 )]["student_name"].count()
THS_10_12grade_passing_reading_percentage =  THS_10_12grade_passing_reading / THS_10_12grade_count * 100
THS_10_12grade_passing_reading_percentage

**Calculate the overall passing percentage of 10th-12th grade from Thomas High School.** 
THS_10_12grade_passing_reading_math = student_data_df.loc[ (student_data_df["grade"] != "9th")  & (student_data_df["school_name"] == "Thomas High School") & (student_data_df["reading_score"] >= 70 )  & (student_data_df["math_score"] >= 70 )]["student_name"].count()
THS_10_12grade_passing_overall_percentage =  THS_10_12grade_passing_reading_math / THS_10_12grade_count * 100
THS_10_12grade_passing_overall_percentage

Last,I replaced the % Passing Math, % Passing Reading, and % Overall Passing scores in the current School Summary DataFrame with the new passing percentages for Thomas High School.And I got this result.

![image](https://user-images.githubusercontent.com/90277142/136711964-9b3c62d9-3a9e-4927-b55d-b798fed59659.png)

* The School summary affected,You can see changes when you will compare previous school summary dataframe metric with later school summary dataframe metric. after excuding 9th grade student for thomas high school and only calculating 10-12 grade students passing math,passing reading and passing both math and reading for Thomas high school.Then I calculated  % Passing Math, % Passing Reading, and % Overall Passing scores For only Thomas high school 10-12 grade passing student and i saw that % Passing Math, % Passing Reading, and % Overall Passing scores increased.  

* Replacing the ninth graders math and reading scores affect Thomas High School’s performance relative to the other schools because when i replaced Thomas high school 9th grade with Nans the number has move towards accuracy and percentage of passing math and % of passing reading and both % of math and reading increased because NANs are not being considered while calculating. 

![TSH_9th_NaN](https://user-images.githubusercontent.com/90277142/136714209-e5e73e77-46ea-4694-8db5-359fc62a8782.png)

* Yes,Replacing the ninth-grade scores affect the following:
**Math and reading scores by grade** when i calculated Math and reading scores by grade,every grade got results but after Replacing the ninth-grades with NaN, i got (Math and reading scores) for 9th grade is NaN but all other grade have same result.**Scores by school spending:** By replacing the ninth-grade scores does not affect the scores by school spending.**Scores by school size**we divided school in three bin according to sizes,small,Medium and Large.because of change in 9th grade thomas high school scores with nan Medium school size school overall percentage of scores decreased.small and large size school scores are same.**Scores by school type** Replacing the ninth-grade scores affect the scores by school type also,I replaced THomas high school 9th grades scores and thomas high school is charter Type school so,In charter type school type overall Percentage has been decreased.but District type school type dhes not have any affect.
  
   
   
####**Summary:**

Changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.
* Number of passing Math Students for Thomas High School has been changed beacause i replaced 9th grade student of Thomas high school math scores with Nan.
* When Number of passing Math Students for Thomas High School has been changed because of that my % passing math also has been changed.
* Similarly i also put NaN for passing reading scores of 9th grade students of Thomas high school so Number of passing reading Students for Thomas High School has been changed
  because of that %passing reading also has been changed.
* And When we calculate % passing both math and reading that also affected by changing 9th grader students scores of Thomas high school with NaN.
* when I calculated Math and reading scores by grade. Every grade got results but after Replacing the ninth-grades with NaN for Thomas high school, i got (Math and reading        scores) for 9th grade is NaN but all other grade have same result like my module testing
