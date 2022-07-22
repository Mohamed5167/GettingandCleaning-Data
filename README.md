# Code Description
## Mohamed Alameeri

Read the test data using read.table with the default parameters  
and column bind them. This also applies to the train data files.  

```
# Read the three test files and column bind them
subject_test_df <- read.table("UCI HAR Dataset/test/subject_test.txt")
x_test_df <- read.table("UCI HAR Dataset/test/X_test.txt")
y_test_df <- read.table("UCI HAR Dataset/test/y_test.txt")
test_df <- cbind(subject_test_df, y_test_df, x_test_df)
```
```
# Read the three train files and column bind them
subject_train_df <- read.table("UCI HAR Dataset/train/subject_train.txt")
x_train_df <- read.table("UCI HAR Dataset/train/X_train.txt")
y_train_df <- read.table("UCI HAR Dataset/train/y_train.txt")
train_df <- cbind(subject_train_df, y_train_df, x_train_df)
```

Combine the test and train data frames to form a single data frame using row  
bind.  

```
# Merge the train and test data frames using rbind
merged_df <- rbind(test_df, train_df)
```

Change the column names to descriptive ones from the features.txt file.  

```
# Write descriptive column names
new_names <- read.table("UCI HAR Dataset/features.txt")
names(merged_df) <- c("SubjectID", "Activities", new_names[, 2])
```

To get the mean and standard deviation measurements, use the grep function  
to search for "mean" or "std" in the column names of the merged_df while  
ignoring case.  

```
# Get the mean and standard deviation measurements only
mean_std_measure <- grep("mean|std", names(merged_df), ignore.case = TRUE)
mean_std_df <- merged_df[, c(1, 2, mean_std_measure)]
```

Change the labels in the Activities column from the second column of the  
activity_labels.txt file. Use the numbers from the Activities column for indexing.  

```
# Changed the Activities column to descriptive names
activity_label <- read.table("UCI HAR Dataset/activity_labels.txt")[2]
mean_std_df$Activities <- activity_label[mean_std_df$Activities, ]
```

Using piping (%>%), average of every measurement grouped by subject id and the activity performed.  

```
# Mean of all measurements for each subject and activity
group_by(mean_std_df, SubjectID, Activities) %>%
    summarize_all(list(mean = mean))
```