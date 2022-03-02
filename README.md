# School District Analysis Challenge
## Overview

The local school board has requested some data on the performance of students in the 15 schools in the school district. This data includes information on each student's test scores, as well as school level data regarding budgets, school size, and the type of school. The district is interested in a summary and analysis of this data to help inform decision-making around budgeting, among other things. 

## Results 

After cleaning up some naming errors to make sure the data coincides with student records, we merged the student data and the school data into a large Data Frame in order to work with all the data simultaneously.

```
school_data_complete_df = pd.merge(student_data_df, school_data_df, on=["school_name", "school_name"])
```
A sample of that data is displayed below:
![image 1](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/image%201.jpg?raw=true)

We determined the number of students who passed their math and reading tests. 

```
passing_math_reading = school_data_complete_df[(school_data_complete_df["math_score"] >= 70) & (school_data_complete_df["reading_score"] >= 70)]
```

With that data, we were able to develop a dataframe with information on the total number of students who passed math, reading, and both tests, as well as the average scores across the district. 
![Image 2](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/Image%202.jpg?raw=true)
This information was helpful as a reference point, but ultimately the district was interested in which schools were performing higher or lower within the district. 

By using the `groupby` function, we were able to create a new dataframe that included students' scores aggregated by school, as well as higher-level data about the school, such as budget and type of school. 

Below are the top 5 highest performing schools in the district, based on overall pass-rate:
![image 3](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/image%203.jpg?raw=true)
And here are the lowest performing schools, by the same metric
![image 4](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/image%204.jpg?raw=true)

Interestingly, the success of the school does not appear to be directly correlated to the pass-rate -- if anything, it may be inversely correlated. The highest performing schools have lower budgets than the lowest performing schools - both in terms of total budget and per-student budget. 
The school type, however, may indeed be correlated. All 5 of the top performing schools are charter schools, while all 5 of the bottom performing schools are district schools. In fact, a separate summary of schools by type shows the same results: 
![image 8](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/Screenshot%202022-03-01%20160035.jpg?raw=true)
The charter schools appear to be producing better overall results and that there are also better results per dollar spent in charter schools. 

Of course, a further statistical analysis would need to be conducted to determine whether this correlation is produced as a result of the school type itself, or whether there is simply a correlation between students that choose charter schools and higher test scores. What the school can likely surmise from thie data, however, is that increasing funding does not appear to be a direct path towards increased test scores. In fact, as seen in an additional summary below, the higher the average spending per student, the lower the overall test scores.
![image 5](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/Image%205.jpg?raw=true)

One of the final useful analyses we had the opportunity to conduct was performance based on school size. 
![image 7](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/image%207.jpg?raw=true)
This data shows that the larger schools - those with 2000+ students - are doing worse in all testing metrics.

Unfortunately, some of the data came under suspicion - one of the schools, Thomas High School, was suspected to have tampered with test results from its ninth graders. We re-ran the analysis, eliminating the suspect data, in order to see if this made a difference in the end results.

As seen above, Thomas High School had been in the top five highest performing schools in the district. The new analysis below maintains their place as second in the district, even without the ninth graders' data.
![image 6](https://github.com/sophiehearn/School_District_Analysis_Challenge/blob/main/Images/image%206.jpg?raw=true)

Ulimately, this data summary cannot tell us whether the 9th grade test scores at THS were tampered with, but it does not seem to significantly affect THS' relative standing to other schools in the district. 

With the new data, the average math score went down - 83.35 compared with the previous score of 83.41, but the average reading score actually went up - 83.90 compared with 83.85. The percentage of students who passed both math and reading went down, however. In math, the percentage of students who passed went down from 93.27% to 93.19%. The percentage of students who passed reading went down from 97.31% to 97.02%. The overall pass rate went down from 90.94% to 90.63%. 

The change in data didn't ultimately affect the overall district analysis - such as the average scores based on scool size or spending per student.

## Summary

The data provided should give the school board a better ability to assess the direction they would like their school district to go in. It is somewhat difficult to draw firm conclusions from this data without more information about the school populations, but it seems clear that the schools that need attention are the larger schools and the district schools. The data also seems to point towards the conclusion that increased funding is not improving the performance of these schools. The school district should look carefully at how to improve performance at the larger, district schools, and should look towards the smaller, charter schools to understand pathways to success.