# Project 5 : Measure Up!



## Problem statement
In the PBS KIDS Measure Up! app, children ages 3 to 5 learn early STEM concepts focused on length ,capacity and weight while going on an adventure through different worlds - Treetop City, Magma Peak, and Crystal Caves. Joined by their favourite PBS KIDS characters from Dinosaur Train, Peg + Cat, and Sid the Science Kid, children can also collect rewards and unlock digital toys as they play.This project will predict grades on in-game assessments and create an model that will
lead to better-designed games and improved learning outcomes.



## Executive Summary


### Contents

- [Data Collection and Cleaning](#Data-Collection-&-Cleaning)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Pre Processing](#Pre-Processing)
- [Modeling](#Modelling)
- [Inferential Visualizations](#Inferential-Visualizations)
- [Conclusions and Recommendation](#Conclusions-and-Recommendation)


### Data Collection & Cleaning


Anonymous gameplay data, 
including knowledge of videos watched and games played, 
from the PBS KIDS Measure Up! app, a game-based learning tool 
developed as a part of the CPB-PBS Ready To Learn Initiative with funding from the U.S. Department of Education 
has been provided on kaggle.https://www.kaggle.com/c/data-science-bowl-2019/data

### Exploratory Data Analysis
This step involves the following:

>1. Import and Read data - Reading the csv file <br>
>2. Data Dictionary - is specified below <br>
>3. Data Visualization - Creating histogram and other plots to study the distribution of data<br>


Data Dictionary :

Game Dataframe
|Feature|Type|Description|
|---|---|---|
|event_id|object|Randomly generated unique identifier for the event type|
|game_session|object|Randomly generated unique identifier grouping events within a single game or video play session|
|timestamp|object|Client-generated datetime|
|event_data|object|Semi-structured JSON formatted string containing the event parameters|
|installation_id|object|Randomly generated unique identifier grouping game sessions within a single installed application instance|
|event_count|int64|Incremental counter of events within a game session (offset at 1)|
|event_code|int64| Unique Identifier per game, but duplicated across games|
|game_time|int64|Time in milliseconds since the start of the game session|
|title|object|Title of the section|
|type|object|Media type of the section|
|world|object|Main section of application|

Score Dataframe
|Feature|Type|Description|
|---|---|---|
|game_session|object|Randomly generated unique identifier for the event type|
|installation_id|object|Randomly generated unique identifier grouping game sessions within a single installed application instance|
|title|object|Title of assessment|
|num_correct|int64|Number of attempt made to complete the assessment|
|num_incorrect|int64|Number of incorrect attempt made to complete the assessment|
|accuracy|float64|Calulated based on num_correct and num_incorrect|
|accuracy_group|int64|Outcomes in this competition are grouped into 4 groups|




### Pre Processing
This step involves the splitting the dataframe into three parts based on Worlds in the game :

>1.World 1- Magma Peak<br>
>2.World 2- TreeTop City<br>
>3.World 3- Crystal Caves<br>


### Modeling
This step creates two models and compares them.

>1. SVM(Support Vector Machine) Model<br>
>2. Random Forest Model Model<br>
>3. Comapring Models

World 1

|Model|Score|Kappa Score|
|---|---|---|
|SVM|0.641|0.1007
|Random Forest|0.625|0.2900|

World 2

|Model|Score|Kappa Score|
|---|---|---|
|SVM|0.662|0.6031|
|Random Forest|0.66292|0.5839|

World 3

|Model|Score|Kappa Score|
|---|---|---|
|SVM|0.687|0.6865|
|Random Forest|0.6795|0.6484|


### Inferential Visualizations

>1. Creating a Logistic Regression Model <br> 


## Conclusions and Recommendations

Calculating the coefficients of Logistic Regression and further exploring the lessons with lower coefficients,following conclusion/recommendation is made.<br>

Bug Measurer, Flower waterer, Fireworks, Bottle filler and sandcastle builder are some of the lessons where the percentage of people who have played and won is significantly more than people who haven’t played and won.<br>
These are the lessons which are most poular in this application.It is interesting to note that all these lessons activity based.Activities are mini games which do not have a specific goal but still helps the children to practise the concept in an interesting manner.
As games have specific goals and if a task is not completed correctly, one will not be able to proceed further,hence Children might be attracted towards activity based lessons than games based lessons. <br>

Egg dropper, heavy-heavier-heaviest,leaf leader,pan balance,costume box,rulers,treasure map and slop problem are some of the lessons where the percentage of people who have played and won is significantly less than people who haven’t played and won.<br>
 All these lessons are appear very complicated for the age 3 to 5.If children could not finish a lesson, they will probably be not much interested and will not try that lessons again and hence they are less popular lessons.We can also say that these lessons do not contribute to earn good grades in assessment and hence these lessons can be replaced by simpler activities which will help them to undertand a concept better.<br>
It is also interesting to note that some of the lessons are of type videos,which are 
are conversational, and probably children might be interested into videos which has music like a song or rhyme.<br>
