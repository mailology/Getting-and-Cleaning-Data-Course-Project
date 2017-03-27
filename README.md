# Getting and Cleaning Data Course Project

The files in this folder provide a solution for the Coursera "Getting And Cleaning Data" course project. The course project works with the "Human Activity Recognition Using Smartphones Dataset" from the UCI Machine Learning Repository. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

Here are the data for the project:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip


# The Transformation Script run_analysis.R

The file run_analysis.R contains an R script for transforming the original dataset into a second dataset according to the following rules:

You should create one R script called run_analysis.R that does the following:

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement.
3. Uses descriptive activity names to name the activities in the data set.
4. Appropriately labels the data set with descriptive variable names.
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.


# Getting the data from the link provided

From the script, we get the data by downloading the file via the link provided. The data is saved in a folder called "data" which is created at the beginning if it does not exist. The file is then unzipped and we get the UCI HAR Dataset.

See the README.txt file for the detailed information on the dataset. For the purposes of this project, the files in the Inertial Signals folders are not used. The files that will be used to load data are listed as follows:

* test/subject_test.txt
* test/X_test.txt
* test/y_test.txt
* train/subject_train.txt
* train/X_train.txt
* train/y_train.txt

We read the activity files, subject files and features files of both testing and training data set into the variables. The next step is to merge the data from these two sets into one data set.

# Merges the training and the test sets to create one data set

We first concantenate the data tables of training and testing sets by row. There are altogether three tables: subject, activity and features. Then we set names for the variables on each table. For features, we read the names of the variables from the feature.txt file.
Lastly, we combine all these three tables into one data set called Data.

# Extracts only the measurements on the mean and standard deviation for each measurement

Only variables with means and standard deviations are needed for the final data. We select only means and standard deviation by using the grep() function on Data. Then we use subset function to get the variables and assign it back to Data.

# Uses descriptive activity names to name the activities in the data set

We read the descriptive activity names from the activity_labels.txt file. The activity names are replaced by the descriptive name by using the factor() function. 

# Appropriately labels the data set with descriptive variable names

In the former part, variables activity and subject and names of the activities have been labelled using descriptive names. In this part, Names of Features will be labelled using descriptive variable names. We 

1. prefix t is replaced by time
2. Acc is replaced by Accelerometer
3. Gyro is replaced by Gyroscope
4. prefix f is replaced by frequency
5. Mag is replaced by Magnitude
6. BodyBody is replaced by Body

# Creates a second, independent tidy data set and ouput it
In this part, a second, independent tidy data set will be created with the average of each variable for each activity and each subject based on the data set in step 4. We use library(plyr) and the aggregate function to compute the mean for each variable for each activity and each subject. The result data is saved as tidyfile.txt.


