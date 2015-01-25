This file describes the analysis done on the "Human Activity Recognition Using Smartphones" dataset.

1. Download the data from "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip" and unzip it into the working directory.
2. Include the run_analysis.R file in the same working directory.
3. The run_analysis.R file contains the script for conducting the analysis. The script consists of a function to create and write the intermediate merged data, as well as the script to utilize that merged data, produce the final tidy data set, and write that into a text file.
4. Two output files are generated in the working directory:
	- merged_data.txt (7.89 Mb): contains the intermediate merged and cleaned data frame [10299 x 68].
    - tidy_data.txt (218 Kb): contains the final data frame [180 x 68], of average mean and standard deviation measurements per subject and activity.
