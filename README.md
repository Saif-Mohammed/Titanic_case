### Titanic_case
* Titanic case - Kaggle https://www.kaggle.com/c/titanic
* General overview of the case using python, numpys, pandas and seaborn
* Udacity Data Analyst Nanodegree Student - Intensive course with live classes

### Introduction
The sinking of the RMS Titanic is one of the most infamous shipwrecks in history. On April 15, 1912, during her maiden voyage, the Titanic sank after colliding with an iceberg, killing 1502 out of 2224 passengers and crew. This sensational tragedy shocked the international community and led to better safety regulations for ships.

### Installations
* Python 2.7 and the following Python libraries:
* NumPy
* Pandas
* matplotlib
* Anaconda.

### Code
Code is provided in Titanic_case4.ipynb

### Sample file size
We need to determine the size of file titanic-data.csv provided just in case, so it is not a way too large. If it is large we would probably need to break it or analyse samples. As we can se the file size is only 61Kb, manageable for analysis size.

### Plan of project

* Formulate few questions to be answered and determine what to investigate
* Have a look at the file and see what it consists of and whether the data is consitent and not corrupt
* Investigate the data by grouping and counting it and seeing if there are any conclusions to be made
* Made visualizations of certain information points to illustrate the overall data points and also specific points
* Make conclusions and discuss the deficiences

### Methodology to be used
We will use numpy and pandas to analyze our file. And first we will create a dataframe and see what table consists of: the table size is 891 rows X 12 columbs.

### Approach to problem
We know from the intro that women, chidlren and upper class were the most likely to survive. Also, it was stated the one of the reasons was the lack of lifeboats for some passenges. By looking at the table, we can estimate the additional questions which we are going to be researching. Obviously we need to prove that there is connection between percent of survival and Sex, Age and Passenger classes.

I would also research weather having spouces, children or parents would actually increase survivorship chances. Possibly, it would increase for those who would have low chances otherwise. I am going to try to see what happened with the crew - what was the chance of survivorship for crew members. We can probably identify them by Fare - obviously they haven't paid it or Cabin class. Location of Cabin on the ship would also have an effect of survivorship as there is a chance that certain individuals were not able to emabark on boats as they were the last in the queue, or there was a panic and they could not leave. As such, the question is what are the chances of women, children and upper-class, i.e. those who had highest changes of survival to survive if they were in certain cabins? I am going to take one group - say upper class and see the survival rates based on cabin location. There is a chance that in the panic, whole sections of the ships were cut off from access to the deck where lifeboat embarkment was happening. We should also see if all who embarked survived. There is a chance that some boats capped and were not found by resque mission.

### Questions that will be investigated
1. Number of passengers survived broken down by Sex or Passenger Class or Fare
2.  Number of passengers who were children and survival rates
3.  Number of crew members and survival rates
4.  Survival rates by Sex and Passenger class together

### Statistical description
We will need to see a brief statistical description of our table, where numerical values will be analyzed and basic information like count, mean, standard deviation, quartiles will be provided. For some columns like Agge and Fare this summary gives a useful overview. Mean ages is 29.7 years with std of 14.5 years. Quartile information was not retrieved due to some null values. 'Fare' information provided some meaningful data, however it seems that there is significant difference between ticket price, where the lowest price was 0 and the highest 512. Probably, 0 ticket price was assigned to the crew.
To investigate the above we will need to determine the type of data in the sample and its availability (not Null data)

### Sample description and analysis
It should be noted that 1,502 passengers died (2,224 total passengers) or 67.5%. We should see if our sample's survivorship data is similar to it. Finally, our sample has 891 entries while Titanic ship had 2224, which is a very good sample and can probably be used to estimate the total population. However, we need to be careful and see if the sample is not biased, i.e. that passengers of certain class or age, etc were not selected.
Below we can view the type of information in the dataframe. Majority of it are integers, followed by objects and floats.

### Titanic population data
We can see that 342 or 38.4% survived out of our total passengers in sample data. In total population we had 32% survivorship rate. We can also find out from open sources how many males and females were on the ship, but in our sample females are 35%. As you can see below, there were 434/2226 or 19.5%. Our sample is misrepresented in women, i.e. it is too high for women.
[http://www.icyousee.org/titanic.html]
* Women Total: 434 Died: 110 Survived: 324 Survived: 75%
* Children Total: 112 Died: 56 Survived: 56 Survived: 50%
* Men Total: 1680 Died: 1357 Survived: 323 Survived: 19%
* On Board Total: 2226 Died: 1523 Survived: 703 Survived: 32%

### Null data and data wrangling
There are many null data in Age. 177 our of 891 represents almost 20% of information. Cabin information is only 23% available, with 77% is null. We will replace Null data as it will interfere with our calculations as rows with null data are not taken into account in many plots and caculations used throughout this project. We will fill the null rows in Age with mean data as below and in rows with categorical data they will be replaced by 'Unknown'. Unknown is considered to be as no data and will be still taken into account in calculations and plots. For visualization purposes in column 'Survived' we will replace 1 and 0 with more understanding Yes and No strings.
```
print pd.isnull(df).sum()
df['Age'] = df['Age'].fillna(df['Age'].mean())
df['Cabin'] = df['Cabin'].fillna('Unknown')
df['Embarked'] = df['Embarked'].fillna('Unknown')
df['Survived'] = df['Survived'].replace([0], 'No')
df['Survived'] = df['Survived'].replace([1], 'Yes')


#print df['Cabin'].isnull().sum()
print df['Cabin'].describe()
df['Age'].describe()
print df['Survived'].head(5)
```
| Tables        | Are           |   |
| ------------- |:-------------:| -----:|
|       |  |  |
# Number of passengers by Sex and Survived¶
```
female    314
male      577
Name: Sex, dtype: int64
Yes    342
No     549
Name: Survived, dtype: int64
Yes    109
No     468
Name: Survived, dtype: int64
```
### Visualization of sex and class distribution
Males were predominant in all classes but clearly so in third class.
![GitHub Logo](/iclouddrive/Desktop/img)
Format: ![Alt Text](url)



