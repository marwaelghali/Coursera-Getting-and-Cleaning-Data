This file describes the variables, the data, and any transformations or work done to clean up the retrieved data.

- The main data source:
  http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

- The original data set:
  https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
  
- The data set contains the records obtained from experiments carried out with a group of 30 subjects, each performing six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING).

- The data features provided in the original data set, for each record are listed below ('-XYZ' denotes the 3-axial  signals in the X, Y and Z directions):
	tBodyAcc-XYZ
	tGravityAcc-XYZ
	tBodyAccJerk-XYZ
	tBodyGyro-XYZ
	tBodyGyroJerk-XYZ
	tBodyAccMag
	tGravityAccMag
	tBodyAccJerkMag
	tBodyGyroMag
	tBodyGyroJerkMag
	fBodyAcc-XYZ
	fBodyAccJerk-XYZ
	fBodyGyro-XYZ
	fBodyAccMag
	fBodyAccJerkMag
	fBodyGyroMag
	fBodyGyroJerkMag

- For each of the above features, the following measurements are produced in the final data set, computed as an average per test subject and activity: 
	Mean: Mean value
	Std: Standard deviation

- The analysis script applies the following steps to clean and reformat the original data set:
	1. Reads the file "activity_labels.txt" to obtain the labels of the activities, and stores them into a corresponding variable.
	2. Reads the file "features.txt" to obtain the labels of the features, and stores them into a corresponding variable.
	3. Reads the files "X_train.txt", "y_train.txt" and "subject_train.txt" from the "train" folder into data frames, assigns the 'feature' column labels accordingly, and stores them into corresponding variables.
	4. Concatenates the "train" feature measurements, activities, and subject data frames into a single data frame [7352 x 563].
	5. Reads the files "X_test.txt", "y_test.txt" and "subject_test.txt" from the "test" folder into data frames, assigns the 'feature' column labels accordingly, and stores them into corresponding variables.
	6. Concatenates the "test" feature measurements, activities, and subject data frames into a single data frame [2947 x 563].
	5. Appends the "train" and "test" data frames into a single data frame [10299 x 563].
	6. Determines the columns of the data frame containing the required 'Mean' and 'Standard Deviation' feature measurements, based on the 'feature' labels.
	7. Extracts only those columns from the combined data frame, along with the activity and subject columns. This produces a data frame of [10299 x 68] dimensions.
	8. Merges the resulting data frame with the 'activities' labels, to assign the corresponding activity name to each record, and removes the column containing the activity ids.
	9. Cleans up the feature measurements column labels, by removing the "()" and "-" characters, and capitalizing the first letter of "Mean" and "Std".
	10. Writes the merged and cleaned data frame into the text file 'merged_data.txt'.
	11. Groups the data frame by subject and activity.
	12. Summarizes the data frame by applying the 'mean' function on each of the non-grouping columns, computing an average of the "Mean" and "Std" measurements per subject and activity. This produces a data frame of [180 x 68] dimensions.
	13. Writes the resulting data frame into the text file 'tidy_data.txt'.
