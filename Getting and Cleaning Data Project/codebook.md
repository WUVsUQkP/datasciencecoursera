##This document describes the variables, the data, and any transformations or work that I have done to clean the dataset.

##data location:
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones


##data set for this project:
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip


##The run_analysis.R script with the following steps to clean up the data set:
1. Read X_train.txt, y_train.txt and subject_train.txt from the folder and store each of them into trainData, trainLabel and trainSubject.
2. Read X_test.txt, y_test.txt and subject_test.txt from the folder and store each of them into testData, testLabel and testsubject.
3. Concatenate testData to trainData to produce a data frame (10299x561), joinData; concatenate testLabel to trainLabel to produce another data frame(10299x1), joinLabel; concatenate testSubject to trainSubject to produce the third data frame(10299x1), joinSubject.
4. Read the features.txt from the folder and store the data in a variable called features. We only get the measurements on the mean and sd. These results in a 66 indices list. We get a subset of joinData with the 66 corresponding columns.
5. Clean up the column names of the subset. We remove the "()" and "-" symbols in the names. Likewise, we make the first letter of "mean" and "std" a capital letter "M" and "S".
6. Read the activity_labels.txt file from the folder and store them into a variable called "activity".
7. Clean up the activity names in the second column of activity. At first, we change all names to lower cases. If the name has an underscore between letters, we remove them and capitalize them.
8. Transform the values of joinLabel according to the activity data frame.
9. Combine the joinSubject, joinLabel and joinData by column to get a new cleaned a data frame(10299x68 ), cleanedData. And then name the first two columns, "subject" and "activity". The "subject" column contains integers that range from 1 to 30 inclusive; the "activity" column contains six kinds of activity names; the final 66 columns contain measurements that range from -1 to 1 exclusive.
10. Write the cleanedData out to "mergeddata.txt" file in current working directory.
11. At last, produce a second independent tidy data set with the average of each measurement for each activity and each subject. We have 30 unique subjects and 6 unique activities, which result in a 180 combinations of the two. Then, for each combination, we calculate the mean of each measurement with the corresponding combination. So, after initializing these data frame and performing the two for-loops, we get a new data frame(180x68).
12. Write the result to a file ( "data_with_means.txt") in current working directory.
