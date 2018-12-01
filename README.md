getting-and-cleaning-data-peer-assignment

This project is to prepare a tidy data set for later analysis from the experiment data available at https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip. The main procedure is as following:

1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement.
3. Uses descriptive activity names to name the activities in the data set
4. Appropriately labels the data set with descriptive variable names.
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

Here is how my script implements:
1. Download the above data and unzip to working directory.
2.	Load the activity labels in 'activityLabels.txt' and features in 'features.txt' and assign the value to variables 'activityLabels' and 'featureNames'. 
3.	Select only mean and standard deviation in variable 'featureNames' using ‘grep’ function, and assign to variable 'columnsWithMeanSTD'.
4.	Load the data in files ‘X_train.txt’, ‘y_train.txt', ‘X_test.txt', ‘y_test.txt' 'subject_train.txt' and 'subject_test.txt' to variables 'featuresTrain', 'activityTrain', 'featuresTest', 'activityTest', 'subjectTrain' and 'subjectTest'. 
5.	Use function ‘rbind’ to merge “train” and “test” into 'subject', 'activity' and 'features'.
6.	Use function ‘cbind’ to combine 'subject', 'activity' and 'features' to create variable 'extractedData'.
7.	Use function ‘gsub’ to replace ‘-‘ with ‘_’ and remove ‘()’ in column 2 of “columnsWithMeanSTD”. Rename column names in “extractedData” to ‘subject’, ‘activity’ and features in 'columnsWithMeanSTD' column 2. 
8.	Use ‘factor’ function to name the activity column in “extractedData” using the descriptive activity names in 'activityLabels'. 
9.	To take the average of each variable in “extractedData” for each activity and each subject, use ‘aggregate’ function and FUN = mean and get a new tidy data set ‘Tidy’. Rename the first two columns of ‘Tidy’ to ‘subject’ and ‘activity’. Write the output to ‘Tidy.txt’ in working directory. 