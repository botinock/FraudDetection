# FraudDetection
 Test task for Scalarr on Data Analysis and Anomaly Detection.  
 All the tasks have been completed using Python and Pandas.
 

## Data_1

Task 1. Find the difference between two dates of each stroke and plot Probability Density Function of it. 
A column named **'tti'** was created with a date differences in seconds. Then there was plotted *KDE* graph in *log* scale. ![KDE Plot](https://i.ibb.co/ssm2Ft7/graph.png)  
Result was saved as new .xlsx table.

## Data_2

Task 2. Given data with certain activity of users and information which media and campanign and site they are from.
Find all suspicious sources of users that could be rated as a fraud.  
Firstly, need to split and aggregate **event_name** column as number of each event and group it by media/campaign/site columns. 
Further, we able to make some hypotheses what is fraud based on given data.  
1.  Number of reached level5 can't be bigger than number of reached level3. Found 1914
2.  Number of installations can't be 0. Found 2
3.  Too great values can be outliers(NPU, level3, level5). Found 33
4.  All the users of group have not reached level3. Found 3750
5.  Conversion rate in group is <0.1% (or zero). Found 15347
6.  Levels 3 and 5 have reached many times in group (depends on game, not used).
7.  Too similar ID in group. It can mean that all bots installed the game in the same time (not used).  

There have been created 4 coulmns named *"flag"*, *"flag_rare"*, *"flag_zero"*, *"flag_NPU"*. It has a bool value if user was flagged by the above conditions.
These all data is not 100% fraud and should be subject to more detailed analysis.

## Data_3

Task 3. Given data of hardware and software users' phones. Find anomalies.
Found anomalies: 
1.  Location country name == '0'. Found 172
2.  Device OS version == '0'. Found 3603
3.  Network type == '0'. Found 100
4.  Network type == 'Dialup', number of examples = 4.
5.  User agent - Mozilla. Found 24.

Device OS version anomaly can be labeling error because correct OS version information exist in user agent. Different country locations(except Russia) can be just a noise. And i can't tell anything about device models, other OS versions and app versions. It needs to apply different unsupervised machine learning models to get more information. 
