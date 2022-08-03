# Boston_Crime

![boston-city-at-night-michael-claudio](https://user-images.githubusercontent.com/98721891/182532633-cad70681-1fdb-4c12-86ff-5548d802613e.jpeg)

## Final Project - Part 1 
 
* **PowerPoint -** [BOSTON CRIME.pptx](https://github.com/duygusimsek/Boston_Crime/blob/duygu/BOSTON%20CRIME.pptx)

* **Tableau -** [Boston Crime Project](https://public.tableau.com/app/profile/kimberly.smith2198/viz/BostonCrimeProject/CRIMECOUNT)

## Team Members - Roles

* [Carter Bentinganan](https://github.com/csobent) - Tool Creation (Triangle)
* [Christopher Lue](https://github.com/chrislue01) - Technology Manager (X)
* [Duygu Simsek](https://github.com/duygusimsek) - GitHub Repository Owner (Square)
* [Kimberly Smith](https://github.com/kimcamp33) - Data Framework Creation (Circle)

## Project Overview

Crime is one of the complex social problems that has grown exponentially over time with the increase in population and impacts directly on victims and indirectly on the community. It has strong links to health and well-being at a population level. Crimes are divided by law into various categories, depending on the offense’s severity, the offender’s age, the potential punishment that can be imposed, and the court that holds jurisdiction over the case. No society in any part of the world is without crime. 

Boston is the capital and most populous city of the Commonwealth of Massachusetts in the United States and the 24th-most populous city in the country. It has been recorded 4,378 violent crimes in 2020 in Boston, giving it a violent crime rate of 6.48 per 1,000 people. There were 58 murders, 193 rapes, 923 robberies, and 3,204 sex assaults. These are considered high, given the city has a population of about 675,000 as of 2020.

For the University of Central Florida Data Analytics Bootcamp Project, our team has analyzed **Boston Crime Rate**  for last year (2021) to identify major criminal incidents, locations, and times. In this project, we analyzed the prime crime locations, crimes that have been committed, and days and times. With this analysis, we aimed to answer these questions:

* Is it possible to predict where or when a crime will be committed?
* How has crime changed over the year?
* Does the frequency of crimes change over the day? Week? Months?
* What types of crimes are most common?
* In which area most crimes are committed?

## Analysis

The dataset that has been used for the project is provided by [data.boston.gov](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/f4495ee9-c42c-4019-82c1-d067f07e45d2) web site. 

For the first stage of the analysis, to have a clean dataset, [Crime_Data.png](https://github.com/duygusimsek/Boston_Crime/blob/main/Images/Crime_Data.png) some columns were dropped by using SQL, and the pseudocode for the machine learning analysis was created.  To display the findings visually Tableau will be used. 

### Pertinent Information for the Names of Districts and Crime Codes
Name of the Districts:
1. A1 - Boston Downtown
2. A7 - East Boston
3. A15 - Charlestown
4. B2 - Roxbury
5. B3 - Mattapan
6. C6 - South Boston
7. C11 - Dorchester
8. D4 - South End
9. D14 - Brighton
10. E5 - West Roxbury
11. E13 - Jamaica Plain
12. E18 - Hyde Park

Crime Codes
1. Other - conglomerate of crimes
2. 3115 - Investigate person
3. 3005 - Sick Assist       
4. 3831 - M/V - Leaving Scene - Property Damage    
5. 3114 - Investigate properly      
6. 1402 - Vandalism      
7. 3410 - Towed Motor Vehicle      
8. 801 - Assault - Simple        
9. 613 - Larceny Shoplifting       
10. 3802 - M/V Accident - Personal Injury      
11. 614 - Larceny Theft from MV - Non-Accessory       
12. 3006 - Sick/Injured/Medical - Person     
13. 3201 - Property - Lost/Missing      
14. 3301 - Verbal Dispute      
15. 2647 - Threats to do bodily harm      
16. 1810 - Drugs - Possession/Sale/Manufacturing/Use   
17. 617 - Larceny Theft from Building       
18. 423 - Assault - Aggravated       
19. 619 - Larceny All Others       
20. 3801 - M/V Accident - Other      
21. 2670 - Harassment/Criminal Harassment      
22. 2905 - VAL: Violation of Auto Law     
23. 1102 - Fraud - False Pretense/Scheme     
24. 3803 - M/V Accident - Personal Injury       
25. 724 - Auto Theft       
26. 3502 - Missing Person - Located       
27. 3207 - Property Found       
28. 1832 - Sick Assist - Drug Related Illness       
29. 520 - Burglary - Residential       
30. 616 - Larceny Theft of Bicycle        
31. 301 - Robbery      

## Machine Learning 

For this analysis, we will utilize an unsupervised machine learning model -- clustering -- in order to determine Boston’s crime rate and areas on the given day and time. Pulling data from [data.boston.gov](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/f4495ee9-c42c-4019-82c1-d067f07e45d2), we will train and test our model to help predict crimes at a specific location in the city based on previous crime data. The dataset will be divided into two parts training and testing using **clustering** and **K-Means algorithm**. This analysis hopefully will help law enforcement agencies to predict and detect crimes in specific areas. Visualizing the results by graphs and charts will help understand better the dataset, crime hotspot areas, crime types, and crime patterns.

### Breakdown of Machine Learning Model:

In our dataset, there were 17 variables: 
Incident Number, Offense Code, Offense Description, Offense Code Group, District, Reporting Area, Shooting, Occurred on Date, Month, Year, Hour, UCR Part, Street, Latitude, Longitude, and Location. Many of these variables seemed to be duplicates of information we already had. We determined immediately that Offense Code Group and UCR part could be dropped since both columns were completely null. Other data that we dropped included Reporting Area, Year, Street, Latitude and Longitude. We dropped Reporting Area, Latitude, and Longitude because they provided similar area to District and Location. Year was dropped because all of the data was from the year 2021. After further analysis, it was determined that we could also drop Street and Location in order to create our K-Means clusters.

Other preprocessing steps included encoding the days to turn them into numeric data and binning the Offense Description category. (The reason why we need to turn it into numeric data is provided in the next paragraph). I reduced the offense description category because there were 121 crime types and many of those crime types had an instance of 1. Using a density plot, I found where the amount of instances fell off in the curve; I estimated about 1200. Binning cut down the crime types from 121 to only 20 categories. Encoding the days was straightforward using a lambda function.

![EncodeDays](https://user-images.githubusercontent.com/98721891/182527639-d37ee3a3-8b33-4a7b-99e6-487350979d70.png)
![OriginalCrimeAmount](https://user-images.githubusercontent.com/98721891/182527679-15f879cd-ab51-44be-81f5-14cc48184e24.png)
![BinnedCrime](https://user-images.githubusercontent.com/98721891/182527708-c8d0c2e7-ee62-427a-b13b-ccb6a6305dad.png)

The machine learning model chosen for this project was K-Means clustering with PCA (principal component analysis). One of the reasons we chose this model was because we’re not looking for specific outputs, but rather for patterns to determine new patrols and/or stations for specific areas. Some of the limitations include clustering outliers by giving outliers their own cluster, working exclusively only with numeric data, having to know the clusters ahead of time, and being prone to the curse of dimensionality. The benefits of this model include: it clusters the data to see patterns, it can scale to large data sets (since ours include 70,000+ data points), and it is relatively easy to use and can manipulate it to suit our goals.

One of the ways we worked around one of the limitations is by using PCA, or Principal Component Analysis; this helps reduce the number of dimensions by grabbing the most important variables and condensing the data into more usable variables. Another way was by using the Elbow curve to help us determine the best number of clusters for our data. In order to find out how many components I needed, I inputted 0.95 to encapsulate at least 95% of the data while using PCA, which outputted 33 components. Then I used the variance ratio function to show what percentage each component represented of the data. Afterwards, I used the pcs dataframe to help create an elbow curve, which showed an "elbow" at 34. Since this is an unsupervised machine learning model, there is no training/testing/splitting involved, plus K-Means uses the data as a whole.

![Variance_Ratio](https://user-images.githubusercontent.com/98721891/182528428-84bc944b-c373-432d-95f1-16c513a0a35c.png)
![Elbow_Curve](https://user-images.githubusercontent.com/98721891/182527586-7ecd3eba-4b2a-4830-9d4a-47a8bda49fc3.png)

### Suggestions for Machine Learning:
Possible suggestions I can think of include involving a supervised machine learning model after implementing KMeans. By doing some research online, different sources say using a supervised model after an unsupervised model can help classify information more binarily and we can use different algorithms to help us include an accuracy score and confusion matrix. Also, maybe using a supervised model after using KMeans can identify whether a certain crime will happen in a certain district during specific times. Our unsupervised model helped us with identifying patterns within the data, but the possibility of implementing different algorithms or a different model in conjunction with KMeans could narrow down specifics. 

## Conclusion
According to the results of the analysis, when examining the types of crime by month, Investigate Person, Leaving Scene - Property Damage, and Sick Assist are showing consistency by staying at higher rates throughout the year than other crimes. The trend of crime by month suggests that crime happens at lower rates and then gradually increases throughout the year before dipping in November, before the holidays. Fridays during the month of October see the most crime out of the year. Districts B2 and D4, Roxbury and Southend, respectively, see the most crime in their areas.

Considering more crime occurs on Fridays during the year and then mostly in the month of October, it would be in the best interest of the public and law enforcement to increase patroling during that specific day and month. Also, it would be helpful to add more patrols in September, as well. Although the districts have their main stations to report to, we can also suggest that adding more stations within the district may be beneficial. There is also the possibility of adding more patrols in the districts displaying higher crime rates such as districts B2, D4, C11, and A1. We also suggest that law enforcement teams utilize the winter months for training, whether that be in physical fitness, de-escalation techniques, or collaborating with other professionals to learn more about the population they serve and how to best serve and protect them. 

## Suggestions on Improvements for the Project
One of the improvements for this project we could make is finding another dataset to compare our data. We could possibly include data about the suspects in each crime or data from other years to see the trends of different crimes occurring. There is the possibility the districts see increase or decrease of crime in their area due to other factors whether they be environmental, socioeconomic, political, or other life-changing factors. Another improvement could be finding a dataset that had the Offense Groups and UCR Parts included with them. It probably would have made categorization easier for preprocessing and also easier to cluster using UCR Parts. UCR stands for Uniform Crime Reports and it's basically a tool to calculate the severity of a crime and how to categorize it.


## Technology 
* Application/Data
* PG Admin SQL
* Jupyter Notebooks/Pandas
* Excel

### Utilites
* Github
* Tableau

### Business tools
* Slack

### Visulization
* VSCode
* Tableau

## Sources 
* Dataset Source 
* Dataset csv file 
* Wikipedia 
* [Crime Data](https://github.com/duygusimsek/Boston_Crime/blob/main/CRIMEDATA.csv)





