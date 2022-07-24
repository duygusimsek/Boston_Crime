# Boston_Crime

## Final Project - Part 1 


## Team Members - Roles

* [Carter Bentinganan](https://github.com/csobent) - Tool Creation (Triangle)
* [Christopher Lue](https://github.com/chrislue01) - Technology Manager (X)
* [Duygu Simsek](https://github.com/duygusimsek) - GitHub Repository Owner (Square)
* [Kimberly Smith](https://github.com/kimcamp33) - Data Framework Creation (Circle)

## Project Overview

Crime is one of the complex social problems that has grown a lot over time with the increase in population and impacts directly on victims and indirectly on the community. It has strong links to health and well-being at a population level. Crimes are divided by law into various categories, depending on the offense’s severity, the offender’s age, the potential punishment that can be imposed, and the court that holds jurisdiction over the case. No society in any part of the world is without crime. 

Boston is the capital and most populous city of the Commonwealth of Massachusetts in the United States and the 24th-most populous city in the country. It has been recorded 4,378 violent crimes in 2020 in Boston, giving it a violent crime rate of 6.48 per 1,000 people. There were 58 murders, 193 rapes, 923 robberies, and 3,204 sex assaults. These are considered high, given the city has a population of about 675,000 as of 2020.

For the University of Central Florida Data Analytics Bootcamp Project, our team has analyzed **Boston Crime Rate**  for last year (2021) to identify major criminal incidents, locations, and times. In this project, we analyzed the prime crime locations, crimes that have been committed, and days and times. With this analysis, we aimed to answer these questions:

* Is it possible to predict where or when a crime will be committed?
* How has crime changed over the year?
* Does the frequency of crimes change over the day? Week? Months?
* What types of crimes are most common?
* In which area most crimes are committed?

## Analysis

The dataset that has been used for the project is provided by [data.boston.gov](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/f4495ee9-c42c-4019-82c1-d067f07e45d2) web site. 

For the first stage of the analysis, to have a clean dataset, [Crime_Data.png](https://github.com/duygusimsek/Boston_Crime/blob/main/Images/Crime_Data.png) some columns were dropped by using SQL, and the pseudocode for the machine learning analysis was created.  To display the findings visually Tableau will be used. 


## Machine Learning 

For this analysis, we will utilize an unsupervised machine learning model -- clustering -- in order to determine Boston’s crime rate and areas on the given day and time. Pulling data from [data.boston.gov](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/f4495ee9-c42c-4019-82c1-d067f07e45d2), we will train and test our model to help predict crimes at a specific location in the city based on previous crime data. The dataset will be divided into two parts training and testing using **clustering** and **K-Means algorithm**. This analysis hopefully will help law enforcement agencies to predict and detect crimes in specific areas. Visualizing the results by graphs and charts will help understand better the dataset, crime hotspot areas, crime types, and crime patterns.

### Breakdown of Machine Learning Model:

In our dataset, there were 17 variables: 
Incident Number, Offense Code, Offense Description, Offense Code Group, District, Reporting Area, Shooting, Occurred on Date, Month, Year, Hour, UCR Part, Street, Latitude, Longitude, and Location. Many of these variables seemed to be duplicates of information we already had. We determined immediately that Offense Code Group and UCR part could be dropped since both columns were completely null. Other data that we dropped included Reporting Area, Year, Street, Latitude and Longitude. We dropped Reporting Area, Latitude, and Longitude because they provided similar area to District and Location, respectively. Year was dropped because all of the data was from the year 2021. After further analysis, it was determined that we could also drop Street and Location in order to create our first K-Means clusters.

The machine learning model chosen for this project was K-Means clustering with PCA (principal component analysis). One of the reasons we chose this model was because we’re not looking for specific outputs, but rather for patterns to determine new patrols and/or stations for specific areas. Some of the limitations include clustering outliers by possibly giving outliers their own cluster, working exclusively only with numeric data, having to know the clusters ahead of time, and being prone to the curse of dimensionality. The benefits of this model include: clustering the data to see patterns, it can scale to large data sets (since ours include 70,000+ data points), and it is relatively easy to use and can manipulate it to suit our goals.

One of the ways we worked around one of the limitations is by using PCA, or Principal Component Analysis; this helps reduce the number of dimensions by grabbing the most important variables and condensing the data into more usable variables. Another way was by using the Elbow curve to help us determine the best number of clusters for our data. As far as figuring out our training and testing data, we used a standard testing size of 0.20 or 20% to test the data, while 0.80 or 80% of the data is used for training. This seems to be the standard for testing/training methods, especially for larger datasets.

## Technolgies 
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




