#Coursera Assignment
###I have already downloaded and unzipped file
The data is available at:

<https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip>

I set my working directory
```{r}
setwd("C:/Users/zjavzmaa/Documents/R-Coursera/3) Getting and Cleaning Data/Assignment")
```

I used two packages, `dplyr` and `data.table`.
```{r}
library("dplyr", lib.loc="~/R/win-library/3.2")
library("data.table", lib.loc="~/R/win-library/3.2")
```


##Read Tables
Read the meta tables
```{r}
all_features <-read.table("UCI HAR Dataset/features.txt")
activity_labels <- read.table("UCI HAR Dataset/activity_labels.txt", header = FALSE)
```
Read the Train tables
```{r}
subject_train <- read.table("UCI HAR Dataset/train/subject_train.txt", header=FALSE)
activity_train <- read.table("UCI HAR Dataset/train/y_train.txt", header=FALSE)
features_train <- read.table("UCI HAR Dataset/train/X_train.txt", header=FALSE)
```
Read the Test tables
```{r}
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", header=FALSE)
activity_test <- read.table("UCI HAR Dataset/test/y_test.txt", header=FALSE)
features_test <- read.table("UCI HAR Dataset/test/X_test.txt", header=FALSE)
```
Insert headers to tables
```{r}
colnames(features_train) <- t(all_features[2])
colnames(features_test) <- t(all_features[2])
colnames(subject_train) <- "Subject"
colnames(subject_test) <- "Subject"
colnames(activity_train) <- "Activity"
colnames(activity_test)<- "Activity"
```

##1.Merges the training and the test sets to create one data set.

Row bind the data
```
subject <- rbind(subject_train,subject_test)
features <- rbind(features_train,features_test)
activity <- rbind(activity_train,activity_test)
```

Combine all tables
```
All_Tables <- cbind(features,subject,activity)
```

##2.Extracts only the measurements on the mean and standard deviation for each measurement.
Find all the columns with "mean" or "std" in the headers
```
Col_mean_std <- grep(".*Mean.*|.*Std.*",names(All_Tables), ignore.case = TRUE)
```
Add the "subject" and "activity" columns
```
All_required_columns <- c(Col_mean_std,562,563)
```

Extract the data using the column names from previous
```
Extracted_data <- All_Tables[,All_required_columns]
```

#3.Uses descriptive activity names to name the activities in the data set
Change type of Activity column from numeric to character before replacing
```
Extracted_data$Activity <- as.character(Extracted_data$Activity)
```

Now replace 
```
for(i in 1:6){
  Extracted_data$Activity[Extracted_data$Activity == i]<- as.character(activity_labels[i,2])
}
```
Now change the type back to factor
```
Extracted_data$Activity <- as.factor(Extracted_data$Activity)
```
Check the Activity variable
```
str(Extracted_data[,"Activity"])
```

##4.Appropriately labels the data set with descriptive variable names

Use gsub function to fix the column headers to be more descriptive
`"Acc" to Acceleration`
`"Gyro" to Gyroscope`
`"BodyBody" to Body`
`"Mag" to Magnitude`
`"f" to Frequency`
`"t" to Time`

```
names(Extracted_data)<-gsub("Acc", "Acceleration", names(Extracted_data))
names(Extracted_data)<-gsub("Gyro", "Gyroscope", names(Extracted_data))
names(Extracted_data)<-gsub("BodyBody", "Body", names(Extracted_data))
names(Extracted_data)<-gsub("Mag", "Magnitude", names(Extracted_data))
names(Extracted_data)<-gsub("^t", "Time", names(Extracted_data))
names(Extracted_data)<-gsub("^f", "Frequency", names(Extracted_data))
names(Extracted_data)<-gsub("tBody", "TimeBody", names(Extracted_data))
names(Extracted_data)<-gsub("-mean()", "Mean", names(Extracted_data), ignore.case = TRUE)
names(Extracted_data)<-gsub("-std()", "STD", names(Extracted_data), ignore.case = TRUE)
names(Extracted_data)<-gsub("-freq()", "Frequency", names(Extracted_data), ignore.case = TRUE)
names(Extracted_data)<-gsub("angle", "Angle", names(Extracted_data))
names(Extracted_data)<-gsub("gravity", "Gravity", names(Extracted_data))
```
View column headers
```
names(Extracted_data)
```


##5.From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

Change the `subject` column type to a factor and convert whole table using `data.table` package for easy manipulation
```
Extracted_data$Subject <- as.factor(Extracted_data$Subject)
Extracted_data <- data.table(Extracted_data)
```

Using aggreate function
```
Ave_Data <- aggregate(. ~Subject + Activity, Extracted_data, mean)
Ave_Data <- Ave_Data[order(Ave_Data$Subject,Ave_Data$Activity),]
write.table(Ave_Data, file = "Final_Table.txt", row.names = FALSE)
```
