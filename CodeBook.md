### Coursera course: Getting and Cleaning data (Data Science Specialization)
### Veronika Gajdosova
### October 2016

*********************************************************************************************************************
##														CODEBOOK
*********************************************************************************************************************

This Codebook contains additional information about the project itself, the information about the data set, variables and the process applied to prepare a tidy data set as per the project instructions.

*********************************************************************************************************************
##												INSTRUCTIONS FOR THE PROJECT
*********************************************************************************************************************


The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. The goal is to prepare tidy data that can be used for later analysis. You will be graded by your peers on a series of yes/no questions related to the project. You will be required to submit: 1) a tidy data set as described below, 2) a link to a Github repository with your script for performing the analysis, and 3) a code book that describes the variables, the data, and any transformations or work that you performed to clean up the data called CodeBook.md. You should also include a README.md in the repo with your scripts. This repo explains how all of the scripts work and how they are connected.

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

Here are the data for the project:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

You should create one R script called run_analysis.R that does the following.

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement.
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive variable names.
5 .From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

*********************************************************************************************************************
##												    PROJECT INFORMATION
*********************************************************************************************************************

* DATA FOR THE PROJECT:
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.


Attribute Information:

For each record in the dataset it is provided: 
* Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration. 
* Triaxial Angular velocity from the gyroscope. 
* A 561-feature vector with time and frequency domain variables. 
* Its activity label. 
* An identifier of the subject who carried out the experiment.

A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones


*********************************************************************************************************************
##										ADDITIONAL INFORMATION & VARIABLE DESCRIPTION
*********************************************************************************************************************

For the purposes of this project, the files in the Inertial Signals folders are not used. The files that will be used to load data are listed as follows:

##Files used for analysis

* test/subject_test.txt
* test/X_test.txt
* test/y_test.txt
* train/subject_train.txt
* train/X_train.txt
* train/y_train.txt

##Explanation of the connection between the data files and the variables

A. Values of Variable Activity consist of: 
	1. data from “Y_train.txt” 
	2. data from “Y_test.txt”

B. Values of Variable Subject consist of: 
	1. data from “subject_train.txt” 
	2. and subject_test.txt"

C. Values of Variable Features consist of:
    1. data from “X_train.txt” 
    2. data from “X_test.txt”


D. Particular levels of Variable Activity come from “activity_labels.txt”

E. Names of Variable Features come from “features.txt”

In order to have descriptive variables, "Activity" "Subject" and "Features" will be used in the variable names. To distinguish between the test and train data, _testdata or _traindata, will be used as suffixes to variable names.


### VARIABLE DESCRIPTION FOR THE VARIABLES USED IN THE CODE LEADING TO A CLEAN DATA SET (steps for the tidy data process are described below)

> str(Activity_Traindata)
'data.frame':	7352 obs. of  1 variable:
 $ V1: int  5 5 5 5 5 5 5 5 5 5 ...

 > str(Activity_Testdata)
'data.frame':	2947 obs. of  1 variable:
 $ V1: int  5 5 5 5 5 5 5 5 5 5 ...

 > str(Subject_Traindata)
'data.frame':	7352 obs. of  1 variable:
 $ V1: int  1 1 1 1 1 1 1 1 1 1 ...

> str(Subject_Testdata)
'data.frame':	2947 obs. of  1 variable:
 $ V1: int  2 2 2 2 2 2 2 2 2 2 ...

> str(Features_Traindata)
'data.frame':	7352 obs. of  561 variables:
 $ V1  : num  0.289 0.278 0.28 0.279 0.277 ...
 $ V2  : num  -0.0203 -0.0164 -0.0195 -0.0262 -0.0166 ...
 $ V3  : num  -0.133 -0.124 -0.113 -0.123 -0.115 ...
 $ V4  : num  -0.995 -0.998 -0.995 -0.996 -0.998 ...
 $ V5  : num  -0.983 -0.975 -0.967 -0.983 -0.981 ...
 ## list output truncated

 > str(Features_Testdata)
'data.frame':	2947 obs. of  561 variables:
 $ V1  : num  0.257 0.286 0.275 0.27 0.275 ...
 $ V2  : num  -0.0233 -0.0132 -0.0261 -0.0326 -0.0278 ...
 $ V3  : num  -0.0147 -0.1191 -0.1182 -0.1175 -0.1295 ...
 $ V4  : num  -0.938 -0.975 -0.994 -0.995 -0.994 ...
 $ V5  : num  -0.92 -0.967 -0.97 -0.973 -0.967 ...
## list output truncated

## AFTER MERGING TEST DATA AND TRAINING DATA TO HAVE ONE DATA SET FOR SUBJECT/ACTIVITY/FEATURES(RBINDING)

> str(Subject_data)
'data.frame':	10299 obs. of  1 variable:
 $ V1: int  2 2 2 2 2 2 2 2 2 2 ...

> str(Features_data)
'data.frame':	10299 obs. of  561 variables:
 $ V1  : num  0.257 0.286 0.275 0.27 0.275 ...
 $ V2  : num  -0.0233 -0.0132 -0.0261 -0.0326 -0.0278 ...
 $ V3  : num  -0.0147 -0.1191 -0.1182 -0.1175 -0.1295 ...
 $ V4  : num  -0.938 -0.975 -0.994 -0.995 -0.994 ...
 $ V5  : num  -0.92 -0.967 -0.97 -0.973 -0.967 ...
## list output truncated

> str(Activity_data)
'data.frame':	10299 obs. of  1 variable:
 $ V1: int  5 5 5 5 5 5 5 5 5 5 ...


## All data data frame after all data sets are merged together:

 > str(Data_All)
'data.frame':	10299 obs. of  563 variables:
 $ ACTIVITY                            : int  5 5 5 5 5 5 5 5 5 5 ...
 $ SUBJECT                             : int  2 2 2 2 2 2 2 2 2 2 ...
 $ tBodyAcc-mean()-X                   : num  0.257 0.286 0.275 0.27 0.275 ...
 $ tBodyAcc-mean()-Y                   : num  -0.0233 -0.0132 -0.0261 -0.0326 -0.0278 ...
 $ tBodyAcc-mean()-Z                   : num  -0.0147 -0.1191 -0.1182 -0.1175 -0.1295 ...
 $ tBodyAcc-std()-X                    : num  -0.938 -0.975 -0.994 -0.995 -0.994 ...
 $ tBodyAcc-std()-Y                    : num  -0.92 -0.967 -0.97 -0.973 -0.967 ...



## EXTRACTING THE MEASUREMENTS ON THE MEAN AND STD FOR EACH MEASUREMENT 
## Data set with with measurements on the mean and standard deviation only

> str(Names_selection)
 chr [1:81] "tBodyAcc-mean()-X" "tBodyAcc-mean()-Y" "tBodyAcc-mean()-Z" ...

 > str(Data_All_StD_Mean)
'data.frame':	10299 obs. of  68 variables:
 $ tBodyAcc-mean()-X          : num  0.257 0.286 0.275 0.27 0.275 ...
 $ tBodyAcc-mean()-Y          : num  -0.0233 -0.0132 -0.0261 -0.0326 -0.0278 ...
 $ tBodyAcc-mean()-Z          : num  -0.0147 -0.1191 -0.1182 -0.1175 -0.1295 ...
 $ tBodyAcc-std()-X           : num  -0.938 -0.975 -0.994 -0.995 -0.994 ...
 $ tBodyAcc-std()-Y           : num  -0.92 -0.967 -0.97 -0.973 -0.967 ...
 $ tBodyAcc-std()-Z           : num  -0.668 -0.945 -0.963 -0.967 -0.978 ...
 $ tGravityAcc-mean()-X       : num  0.936 0.927 0.93 0.929 0.927 ...
 $ tGravityAcc-mean()-Y       : num  -0.283 -0.289 -0.288 -0.293 -0.303 ...
 $ tGravityAcc-mean()-Z       : num  0.115 0.153 0.146 0.143 0.138 ...
 $ tGravityAcc-std()-X        : num  -0.925 -0.989 -0.996 -0.993 -0.996 ...
 $ tGravityAcc-std()-Y        : num  -0.937 -0.984 -0.988 -0.97 -0.971 ...
 $ tGravityAcc-std()-Z        : num  -0.564 -0.965 -0.982 -0.992 -0.968 ...
 $ tBodyAccJerk-mean()-X      : num  0.072 0.0702 0.0694 0.0749 0.0784 ...
 $ tBodyAccJerk-mean()-Y      : num  0.04575 -0.01788 -0.00491 0.03227 0.02228 ...
 $ tBodyAccJerk-mean()-Z      : num  -0.10604 -0.00172 -0.01367 0.01214 0.00275 ...
 $ tBodyAccJerk-std()-X       : num  -0.907 -0.949 -0.991 -0.991 -0.992 ...
 $ tBodyAccJerk-std()-Y       : num  -0.938 -0.973 -0.971 -0.973 -0.979 ...
 $ tBodyAccJerk-std()-Z       : num  -0.936 -0.978 -0.973 -0.976 -0.987 ...
 $ tBodyGyro-mean()-X         : num  0.11998 -0.00155 -0.04821 -0.05664 -0.05999 ...
 $ tBodyGyro-mean()-Y         : num  -0.0918 -0.1873 -0.1663 -0.126 -0.0847 ...
 $ tBodyGyro-mean()-Z         : num  0.1896 0.1807 0.1542 0.1183 0.0787 ...
 $ tBodyGyro-std()-X          : num  -0.883 -0.926 -0.973 -0.968 -0.975 ...
 $ tBodyGyro-std()-Y          : num  -0.816 -0.93 -0.979 -0.975 -0.978 ...
 $ tBodyGyro-std()-Z          : num  -0.941 -0.968 -0.976 -0.963 -0.968 ...
 $ tBodyGyroJerk-mean()-X     : num  -0.2049 -0.1387 -0.0978 -0.1022 -0.0918 ...
 $ tBodyGyroJerk-mean()-Y     : num  -0.1745 -0.0258 -0.0342 -0.0447 -0.029 ...
 $ tBodyGyroJerk-mean()-Z     : num  -0.0934 -0.0714 -0.06 -0.0534 -0.0612 ...
 $ tBodyGyroJerk-std()-X      : num  -0.901 -0.962 -0.984 -0.984 -0.988 ...
 $ tBodyGyroJerk-std()-Y      : num  -0.911 -0.956 -0.988 -0.99 -0.992 ...
 $ tBodyGyroJerk-std()-Z      : num  -0.939 -0.981 -0.976 -0.981 -0.982 ...
 $ tBodyAccMag-mean()         : num  -0.867 -0.969 -0.976 -0.974 -0.976 ...
 $ tBodyAccMag-std()          : num  -0.705 -0.954 -0.979 -0.977 -0.977 ...
 $ tGravityAccMag-mean()      : num  -0.867 -0.969 -0.976 -0.974 -0.976 ...
 $ tGravityAccMag-std()       : num  -0.705 -0.954 -0.979 -0.977 -0.977 ...
 $ tBodyAccJerkMag-mean()     : num  -0.93 -0.974 -0.982 -0.983 -0.987 ...
 $ tBodyAccJerkMag-std()      : num  -0.896 -0.941 -0.971 -0.975 -0.989 ...
 $ tBodyGyroMag-mean()        : num  -0.796 -0.898 -0.939 -0.947 -0.957 ...
 $ tBodyGyroMag-std()         : num  -0.762 -0.911 -0.972 -0.97 -0.969 ...
 $ tBodyGyroJerkMag-mean()    : num  -0.925 -0.973 -0.987 -0.989 -0.99 ...
 $ tBodyGyroJerkMag-std()     : num  -0.894 -0.944 -0.984 -0.986 -0.99 ...
 $ fBodyAcc-mean()-X          : num  -0.919 -0.961 -0.992 -0.993 -0.992 ...
 $ fBodyAcc-mean()-Y          : num  -0.918 -0.964 -0.965 -0.968 -0.969 ...
 $ fBodyAcc-mean()-Z          : num  -0.789 -0.957 -0.967 -0.967 -0.98 ...
 $ fBodyAcc-std()-X           : num  -0.948 -0.984 -0.995 -0.996 -0.995 ...
 $ fBodyAcc-std()-Y           : num  -0.925 -0.97 -0.974 -0.977 -0.967 ...
 $ fBodyAcc-std()-Z           : num  -0.636 -0.942 -0.962 -0.969 -0.978 ...
 $ fBodyAccJerk-mean()-X      : num  -0.9 -0.944 -0.991 -0.991 -0.991 ...
 $ fBodyAccJerk-mean()-Y      : num  -0.937 -0.969 -0.973 -0.972 -0.98 ...
 $ fBodyAccJerk-mean()-Z      : num  -0.924 -0.973 -0.972 -0.97 -0.983 ...
 $ fBodyAccJerk-std()-X       : num  -0.924 -0.962 -0.992 -0.992 -0.994 ...
 $ fBodyAccJerk-std()-Y       : num  -0.943 -0.98 -0.971 -0.975 -0.979 ...
 $ fBodyAccJerk-std()-Z       : num  -0.948 -0.981 -0.972 -0.981 -0.989 ...
 $ fBodyGyro-mean()-X         : num  -0.824 -0.923 -0.973 -0.972 -0.976 ...
 $ fBodyGyro-mean()-Y         : num  -0.808 -0.926 -0.981 -0.981 -0.98 ...
 $ fBodyGyro-mean()-Z         : num  -0.918 -0.968 -0.972 -0.967 -0.969 ...
 $ fBodyGyro-std()-X          : num  -0.903 -0.927 -0.973 -0.967 -0.974 ...
 $ fBodyGyro-std()-Y          : num  -0.823 -0.932 -0.977 -0.972 -0.977 ...
 $ fBodyGyro-std()-Z          : num  -0.956 -0.97 -0.979 -0.965 -0.97 ...
 $ fBodyAccMag-mean()         : num  -0.791 -0.954 -0.976 -0.973 -0.978 ...
 $ fBodyAccMag-std()          : num  -0.711 -0.96 -0.984 -0.982 -0.979 ...
 $ fBodyBodyAccJerkMag-mean() : num  -0.895 -0.945 -0.971 -0.972 -0.987 ...
 $ fBodyBodyAccJerkMag-std()  : num  -0.896 -0.934 -0.97 -0.978 -0.99 ...
 $ fBodyBodyGyroMag-mean()    : num  -0.771 -0.924 -0.975 -0.976 -0.977 ...
 $ fBodyBodyGyroMag-std()     : num  -0.797 -0.917 -0.974 -0.971 -0.97 ...
 $ fBodyBodyGyroJerkMag-mean(): num  -0.89 -0.952 -0.986 -0.986 -0.99 ...
 $ fBodyBodyGyroJerkMag-std() : num  -0.907 -0.938 -0.983 -0.986 -0.991 ...
 $ SUBJECT                    : int  2 2 2 2 2 2 2 2 2 2 ...
 $ ACTIVITY                   : int  5 5 5 5 5 5 5 5 5 5 ...



## Appropriately labels the data set with descriptive variable names (changes shortenings/prefixes for full descriptive name. The following substitutions were applied: 

Gyro -> Gyroskope
Mag -> Magnitude
Prefix "t" -> Time
Acc -> Accelerometer
BodyBody -> Body
Prefix "f" -> Frequency


> names(Data_All_StD_Mean)
 [1] "TimeBodyAccelerometer-mean()-X"                
 [2] "TimeBodyAccelerometer-mean()-Y"                
 [3] "TimeBodyAccelerometer-mean()-Z"                
 [4] "TimeBodyAccelerometer-std()-X"                 
 [5] "TimeBodyAccelerometer-std()-Y"                 
 [6] "TimeBodyAccelerometer-std()-Z"                 
 [7] "TimeGravityAccelerometer-mean()-X"             
 [8] "TimeGravityAccelerometer-mean()-Y"             
 [9] "TimeGravityAccelerometer-mean()-Z"             
[10] "TimeGravityAccelerometer-std()-X"              
[11] "TimeGravityAccelerometer-std()-Y"              
[12] "TimeGravityAccelerometer-std()-Z"              
[13] "TimeBodyAccelerometerJerk-mean()-X"            
[14] "TimeBodyAccelerometerJerk-mean()-Y"            
[15] "TimeBodyAccelerometerJerk-mean()-Z"            
[16] "TimeBodyAccelerometerJerk-std()-X"             
[17] "TimeBodyAccelerometerJerk-std()-Y"             
[18] "TimeBodyAccelerometerJerk-std()-Z"             
[19] "TimeBodyGyroskope-mean()-X"                    
[20] "TimeBodyGyroskope-mean()-Y"                    
[21] "TimeBodyGyroskope-mean()-Z"                    
[22] "TimeBodyGyroskope-std()-X"                     
[23] "TimeBodyGyroskope-std()-Y"                     
[24] "TimeBodyGyroskope-std()-Z"                     
[25] "TimeBodyGyroskopeJerk-mean()-X"                
[26] "TimeBodyGyroskopeJerk-mean()-Y"                
[27] "TimeBodyGyroskopeJerk-mean()-Z"                
[28] "TimeBodyGyroskopeJerk-std()-X"                 
[29] "TimeBodyGyroskopeJerk-std()-Y"                 
[30] "TimeBodyGyroskopeJerk-std()-Z"                 
[31] "TimeBodyAccelerometerMagnitude-mean()"         
[32] "TimeBodyAccelerometerMagnitude-std()"          
[33] "TimeGravityAccelerometerMagnitude-mean()"      
[34] "TimeGravityAccelerometerMagnitude-std()"       
[35] "TimeBodyAccelerometerJerkMagnitude-mean()"     
[36] "TimeBodyAccelerometerJerkMagnitude-std()"      
[37] "TimeBodyGyroskopeMagnitude-mean()"             
[38] "TimeBodyGyroskopeMagnitude-std()"              
[39] "TimeBodyGyroskopeJerkMagnitude-mean()"         
[40] "TimeBodyGyroskopeJerkMagnitude-std()"          
[41] "FrequencyBodyAccelerometer-mean()-X"           
[42] "FrequencyBodyAccelerometer-mean()-Y"           
[43] "FrequencyBodyAccelerometer-mean()-Z"           
[44] "FrequencyBodyAccelerometer-std()-X"            
[45] "FrequencyBodyAccelerometer-std()-Y"            
[46] "FrequencyBodyAccelerometer-std()-Z"            
[47] "FrequencyBodyAccelerometerJerk-mean()-X"       
[48] "FrequencyBodyAccelerometerJerk-mean()-Y"       
[49] "FrequencyBodyAccelerometerJerk-mean()-Z"       
[50] "FrequencyBodyAccelerometerJerk-std()-X"        
[51] "FrequencyBodyAccelerometerJerk-std()-Y"        
[52] "FrequencyBodyAccelerometerJerk-std()-Z"        
[53] "FrequencyBodyGyroskope-mean()-X"               
[54] "FrequencyBodyGyroskope-mean()-Y"               
[55] "FrequencyBodyGyroskope-mean()-Z"               
[56] "FrequencyBodyGyroskope-std()-X"                
[57] "FrequencyBodyGyroskope-std()-Y"                
[58] "FrequencyBodyGyroskope-std()-Z"                
[59] "FrequencyBodyAccelerometerMagnitude-mean()"    
[60] "FrequencyBodyAccelerometerMagnitude-std()"     
[61] "FrequencyBodyAccelerometerJerkMagnitude-mean()"
[62] "FrequencyBodyAccelerometerJerkMagnitude-std()" 
[63] "FrequencyBodyGyroskopeMagnitude-mean()"        
[64] "FrequencyBodyGyroskopeMagnitude-std()"         
[65] "FrequencyBodyGyroskopeJerkMagnitude-mean()"    
[66] "FrequencyBodyGyroskopeJerkMagnitude-std()"     
[67] "SUBJECT"                                       
[68] "ACTIVITY"



The TIDY.TXT file contains the fields that will be described below:

## IDENTIFIERS:

* `SUBJECT` - Corresponds to the test subject ID
* `ACTIVITY` - Corresponds to the type of activity performed during the measurements


## Activity Labels

* 1. WALKING: subject was walking during the test
* 2. WALKING_UPSTAIRS: subject was walking up a staircase during the test
* 3. WALKING_DOWNSTAIRS: subject was walking down a staircase during the test
* 4. SITTING: subject was sitting during the test
* 5. STANDING: subject was standing during the test
* 6. LAYING: subject was laying down during the test


*********************************************************************************************************************
												    CREATING THE CLEAN DATAFILE
*********************************************************************************************************************
1. GETTING THE DATA - downloading of data from the source and unzipping it in the project folder (./project). Unzipping of the data into the project subfolder UCI HAR Dataset

2. READING OF DATA FROM THE PARTICULAR FILES

* Reading of data from the files into the variables

2.1 Read the Activity files
2.2 Read the Subject files
2.3 Read Features files 

##As mentioned above - Explanation of the connection between the data files and the variables

A. Values of Variable Activity consist of: 
	1. data from “Y_train.txt” 
	2. data from “Y_test.txt”

B. Values of Variable Subject consist of: 
	1. data from “subject_train.txt” 
	2. and subject_test.txt"

C. Values of Variable Features consist of:
    1. data from “X_train.txt” 
    2. data from “X_test.txt”


D. Particular levels of Variable Activity come from “activity_labels.txt”

E. Names of Variable Features come from “features.txt”


3. CREATING ONE DATA SET BY MERGING THE TRAINING AND THE TEST SETS 
* merging the data tables by rows
* naming the variables with Subject and Activity names
* creating one data set for all data (merging by columns)


4. EXTRACTING THE MEASUREMENTS ON THE MEAN AND STANDARD DEVIATION FOR PARTICULAR MEASUREMENTS
* Subsetting the Name of Features by measurements on the mean and standard deviation and using these selected feature names to subset the data frame.

5. USING DESCRIPTIVE ACTIVITY NAMES TO NAME THE ACTIVITIES IN THE DATA SET 
* Descriptive activity names are read from “activity_labels.txt”
* Variable Activity is factorized in the data frame using descriptive activity names

6. APPROPRIATELY LABELS THE DATA SET WITH DESCRIPTIVE VARIABLE NAMES 

The following substitutions were applied: 

Gyro -> Gyroskope
Mag -> Magnitude
Prefix "t" -> Time
Acc -> Accelerometer
BodyBody -> Body
Prefix "f" -> Frequency

7. CREATING A SECOND, INDEPENDENT TIDY DATA SET AND OUTPUTING IT INTO TIDYDATA.TXT 

Tidy data set is created with the average of each variable for each activity and each subject based on the data set in the previous step. It is saved in the project folder.






















