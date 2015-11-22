######This README file explains how the script works and details how the data was transformed to produce the final data set.
run_analysis <- function () {

The goal of this PA is to create a tidy dataset that contains the mean of various variables of various subjects and activities. This code was written in a manner that I thought would be most efficient, meaning that I
(1) first labeled the measurement data sets (X_train & X_test) with descriptive variable names
(2) secondly renamed the activities in the "Y_train" & "Y_test" data sets
(3) thirdly extracted the measurements on the mean and std for each variable
(4) merged the training and test sets to create one data set
(5) lastly, created an independent tidy data set containing the average of each variable for each activity and each subject
 
First, the project data was downloaded and unzipped. Link: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

Note to my peers: if you are planning to run this code, first download and unzip the data before saving thisscript to your working directory. Then source the R file and run the function "run_analysis". The remaining comments and code below serves as a guide to how the code was written.

Load the library packages "dplyr" and "tidyr". That allows us to use functions such as "summarize_each".
			library (dplyr)
			library (tidyr)

Now, let's read the following files (these files have already been downloaded and unzipped in my personal folder): 
(1) activity_labels.txt
(2) features.txt
(3) train\subject_train.txt
(4) train\X_train.txt"
(5) train\y_train.txt"
(6) test\subject_test.txt
(7) test\X_test.txt
(8) test\y_test.txt

			activity <- read.table ("activity_labels.txt", header = F, stringsAsFactors = F)
			features <- read.table ("features.txt", header = F, stringsAsFactors = F)
			train_subject <- read.table (".\\train\\subject_train.txt", header = F)
			X_train <- read.table (".\\train\\X_train.txt", header = F)
			Y_train <- read.table (".\\train\\y_train.txt", header = F)
			test_subject <- read.table (".\\test\\subject_test.txt", header = F)
			X_test <- read.table (".\\test\\X_test.txt", header = F)
			Y_test <- read.table (".\\test\\y_test.txt", header = F)

Before we can merge the training and test sets, let's rename the variables (column names) of the following 2 files:
(1) X_train (X_train.txt)
(2) X_test (X_test.txt)

Currently, the X_train & X_test contains column names of (V1, V2..., V561) when we read the data via read.table. Let's replace these variable names by matching the numbers with the ID's of the measurements in the "features.txt" file. For example, X_train column 1 will be renamed to "tBodyAcc-mean()-X", which corresponds to ID 1. This fulfills requirement #4 in the assignment, which is to appropriately label the data set with descriptive variable names.

			colnames (X_train) <- c (features$V2)
			colnames (X_test) <- c (features$V2)

Now, let's rename the values of column 1 in the Y_train and Y_test datasets. Match the numbers in the column with the ID of its corresponding activity. For example, # 1 = Walking. This fulfills requirement #3 in the assignment, which is to use descriptive activity names to name the activities in the data set.

For Y_train:

		for (i in 1: nrow (Y_train)) {
			if (Y_train$V1 [i] == 1) {
				Y_train$V1 [i] = "Walking"}
			else if (Y_train$V1 [i] == 2) {
				Y_train$V1 [i] = "Walking Upstairs"}
			else if (Y_train$V1 [i] == 3) {
				Y_train$V1 [i] = "Walking Downstairs"}
			else if (Y_train$V1 [i] == 4) {
				Y_train$V1 [i] = "Sitting"}
			else if (Y_train$V1 [i] == 5) {
				Y_train$V1 [i] = "Standing"}
			else {Y_train$V1 [i] = "Laying"}
		}

Do the same for Y_test.

		for (i in 1: nrow (Y_test)) {
			if (Y_test$V1 [i] == 1) {
				Y_test$V1 [i] = "Walking"}
			else if (Y_test$V1 [i] == 2) {
				Y_test$V1 [i] = "Walking Upstairs"}
			else if (Y_test$V1 [i] == 3) {
				Y_test$V1 [i] = "Walking Downstairs"}
			else if (Y_test$V1 [i] == 4) {
				Y_test$V1 [i] = "Sitting"}
			else if (Y_test$V1 [i] == 5) {
				Y_test$V1 [i] = "Standing"}
			else {Y_test$V1 [i] = "Laying"}
		}

Next, let's extract the mean & sd variables from the X_train and X_test datasets. This fulfills requirement #2 in the assignment, which is to extract only the measurements on the mean and standard deviation. To do this, I included the terms "Mean", "mean", and "std" as part of my argument to "contains". Additionally, we also need to coerce the variable names to syntatically valid names before using the 'select' function.

		valid_variable_names <- make.names (names (X_train), unique = T)
		colnames (X_train) <- valid_variable_names
		X_train <- select (X_train, contains ("mean"), contains ("Mean"), contains ("std"))

		valid_variable_names <- make.names (names (X_test), unique = T)
		colnames (X_test) <- valid_variable_names
		X_test <- select (X_test, contains ("mean"), contains ("Mean"), contains ("std"))

Now that we have all the variable names aligned, we will now combine the following datasets: train_subject, X_train, Y_train. This fulfills requirement #1 of the assignment. I will also create a column called "Trial" to denote whether the subject is doing a train or test run. Additionally, some columns will be renamed to make them more descriptive. 

		Y_train <- rename (Y_train, Activity = V1)
		Merged_table_train <- cbind (train_subject, Y_train, X_train)
		Merged_table_train <- rename (Merged_table_train, Subject = V1)
		Merged_table_train <- mutate (Merged_table_train, Trial = "train")

Repeat the commands above for the 'test' datasets.

		Y_test <- rename (Y_test, Activity = V1)
		Merged_table_test <- cbind (test_subject, Y_test, X_test)
		Merged_table_test <- rename (Merged_table_test, Subject = V1)
		Merged_table_test <- mutate (Merged_table_test, Trial = "test")

Finally, combine Merged_table_train with Merged_table_test. Also arrange the dataset according to Subject ID in increasing order.
			
		Merged_table <- rbind (Merged_table_train, Merged_table_test)
		Merged_table <- arrange (Merged_table, Subject)
		head (Merged_table, 5)

###### Last but not least, step 5 of the PA requires us to create an independent tidy data set containing the average of each
######	  variable for each activity and each subject. There are 180 subject-activity pairs in total.

		Merged_table_avg <- group_by (Merged_table, Activity, Subject)
		Merged_table_avg_final <- summarize_each (Merged_table_avg, funs (mean), - c( Subject, Activity, Trial))
		write.table (Merged_table_avg_final, file = "Cleaning & Gathering Data PA", row.names = F)
		
To best view the data, load the "data.table" package into R before reading the text file: library (data.table) -> fread ("Cleaning & Gathering Data PA.txt")

The resulting, final dataset fulfills the core tidy data rules.
(1) Each variable forms a column.
(2) Each observation forms a row.
(3) Each type of observational unit forms a table.

	}

























