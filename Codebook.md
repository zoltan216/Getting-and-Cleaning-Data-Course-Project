GitHub contains a code book that modifies and updates the available codebooks with the data to indicate all the variables and summaries calculated, along with units, and any other relevant information.

#Codebook
####This codebook identifies all the modifications and updates from the original analysis that was downloaded from 
<https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip>.

For the final out file `Final_Table.txt`, the following variables header names were transformed from:
```{r}
tBodyAcc-mean()-X
tBodyAcc-mean()-Y
tBodyAcc-mean()-Z
tBodyAcc-std()-X
tBodyAcc-std()-Y
tBodyAcc-std()-Z
tGravityAcc-mean()-X
tGravityAcc-mean()-Y
tGravityAcc-mean()-Z
tGravityAcc-std()-X
tGravityAcc-std()-Y
tGravityAcc-std()-Z
tBodyAccJerk-mean()-X
tBodyAccJerk-mean()-Y
tBodyAccJerk-mean()-Z
tBodyAccJerk-std()-X
tBodyAccJerk-std()-Y
tBodyAccJerk-std()-Z
tBodyGyro-mean()-X
tBodyGyro-mean()-Y
tBodyGyro-mean()-Z
tBodyGyro-std()-X
tBodyGyro-std()-Y
tBodyGyro-std()-Z
tBodyGyroJerk-mean()-X
tBodyGyroJerk-mean()-Y
tBodyGyroJerk-mean()-Z
tBodyGyroJerk-std()-X
tBodyGyroJerk-std()-Y
tBodyGyroJerk-std()-Z
tBodyAccMag-mean()
tBodyAccMag-std()
tGravityAccMag-mean()
tGravityAccMag-std()
tBodyAccJerkMag-mean()
tBodyAccJerkMag-std()
tBodyGyroMag-mean()
tBodyGyroMag-std()
tBodyGyroJerkMag-mean()
tBodyGyroJerkMag-std()
fBodyAcc-mean()-X
fBodyAcc-mean()-Y
fBodyAcc-mean()-Z
fBodyAcc-std()-X
fBodyAcc-std()-Y
fBodyAcc-std()-Z
fBodyAcc-meanFreq()-X
fBodyAcc-meanFreq()-Y
fBodyAcc-meanFreq()-Z
fBodyAccJerk-mean()-X
fBodyAccJerk-mean()-Y
fBodyAccJerk-mean()-Z
fBodyAccJerk-std()-X
fBodyAccJerk-std()-Y
fBodyAccJerk-std()-Z
fBodyAccJerk-meanFreq()-X
fBodyAccJerk-meanFreq()-Y
fBodyAccJerk-meanFreq()-Z
fBodyGyro-mean()-X
fBodyGyro-mean()-Y
fBodyGyro-mean()-Z
fBodyGyro-std()-X
fBodyGyro-std()-Y
fBodyGyro-std()-Z
fBodyGyro-meanFreq()-X
fBodyGyro-meanFreq()-Y
fBodyGyro-meanFreq()-Z
fBodyAccMag-mean()
fBodyAccMag-std()
fBodyAccMag-meanFreq()
fBodyBodyAccJerkMag-mean()
fBodyBodyAccJerkMag-std()
fBodyBodyAccJerkMag-meanFreq()
fBodyBodyGyroMag-mean()
fBodyBodyGyroMag-std()
fBodyBodyGyroMag-meanFreq()
fBodyBodyGyroJerkMag-mean()
fBodyBodyGyroJerkMag-std()
fBodyBodyGyroJerkMag-meanFreq()
angle(tBodyAccMean,gravity)
angle(tBodyAccJerkMean),gravityMean)
angle(tBodyGyroMean,gravityMean)
angle(tBodyGyroJerkMean,gravityMean)
angle(X,gravityMean)
angle(Y,gravityMean)
angle(Z,gravityMean)
Subject
Activity
```

### Then the variable names where transformed to:
To transform the `gsub` function was used to fix the column headers to be more descriptive.

`"Acc" to Acceleration`
`"Gyro" to Gyroscope`
`"BodyBody" to Body`
`"Mag" to Magnitude`
`"f" to Frequency`
`"t" to Time`
`"tBody" to TimeBody`
`"-mean()" to Mean`
`"-std()" to STD`
`"-freq()" to Frequency`
`"angle" to Angle`
`"gravity" to Gravity`

###The resulting variable names:
```
TimeBodyAccelerationMean()-X
TimeBodyAccelerationMean()-Y
TimeBodyAccelerationMean()-Z
TimeBodyAccelerationSTD()-X
TimeBodyAccelerationSTD()-Y
TimeBodyAccelerationSTD()-Z
TimeGravityAccelerationMean()-X
TimeGravityAccelerationMean()-Y
TimeGravityAccelerationMean()-Z
TimeGravityAccelerationSTD()-X
TimeGravityAccelerationSTD()-Y
TimeGravityAccelerationSTD()-Z
TimeBodyAccelerationJerkMean()-X
TimeBodyAccelerationJerkMean()-Y
TimeBodyAccelerationJerkMean()-Z
TimeBodyAccelerationJerkSTD()-X
TimeBodyAccelerationJerkSTD()-Y
TimeBodyAccelerationJerkSTD()-Z
TimeBodyGyroscopeMean()-X
TimeBodyGyroscopeMean()-Y
TimeBodyGyroscopeMean()-Z
TimeBodyGyroscopeSTD()-X
TimeBodyGyroscopeSTD()-Y
TimeBodyGyroscopeSTD()-Z
TimeBodyGyroscopeJerkMean()-X
TimeBodyGyroscopeJerkMean()-Y
TimeBodyGyroscopeJerkMean()-Z
TimeBodyGyroscopeJerkSTD()-X
TimeBodyGyroscopeJerkSTD()-Y
TimeBodyGyroscopeJerkSTD()-Z
TimeBodyAccelerationMagnitudeMean()
TimeBodyAccelerationMagnitudeSTD()
TimeGravityAccelerationMagnitudeMean()
TimeGravityAccelerationMagnitudeSTD()
TimeBodyAccelerationJerkMagnitudeMean()
TimeBodyAccelerationJerkMagnitudeSTD()
TimeBodyGyroscopeMagnitudeMean()
TimeBodyGyroscopeMagnitudeSTD()
TimeBodyGyroscopeJerkMagnitudeMean()
TimeBodyGyroscopeJerkMagnitudeSTD()
FrequencyBodyAccelerationMean()-X
FrequencyBodyAccelerationMean()-Y
FrequencyBodyAccelerationMean()-Z
FrequencyBodyAccelerationSTD()-X
FrequencyBodyAccelerationSTD()-Y
FrequencyBodyAccelerationSTD()-Z
FrequencyBodyAccelerationMeanFreq()-X
FrequencyBodyAccelerationMeanFreq()-Y
FrequencyBodyAccelerationMeanFreq()-Z
FrequencyBodyAccelerationJerkMean()-X
FrequencyBodyAccelerationJerkMean()-Y
FrequencyBodyAccelerationJerkMean()-Z
FrequencyBodyAccelerationJerkSTD()-X
FrequencyBodyAccelerationJerkSTD()-Y
FrequencyBodyAccelerationJerkSTD()-Z
FrequencyBodyAccelerationJerkMeanFreq()-X
FrequencyBodyAccelerationJerkMeanFreq()-Y
FrequencyBodyAccelerationJerkMeanFreq()-Z
FrequencyBodyGyroscopeMean()-X
FrequencyBodyGyroscopeMean()-Y
FrequencyBodyGyroscopeMean()-Z
FrequencyBodyGyroscopeSTD()-X
FrequencyBodyGyroscopeSTD()-Y
FrequencyBodyGyroscopeSTD()-Z
FrequencyBodyGyroscopeMeanFreq()-X
FrequencyBodyGyroscopeMeanFreq()-Y
FrequencyBodyGyroscopeMeanFreq()-Z
FrequencyBodyAccelerationMagnitudeMean()
FrequencyBodyAccelerationMagnitudeSTD()
FrequencyBodyAccelerationMagnitudeMeanFreq()
FrequencyBodyAccelerationJerkMagnitudeMean()
FrequencyBodyAccelerationJerkMagnitudeSTD()
FrequencyBodyAccelerationJerkMagnitudeMeanFreq()
FrequencyBodyGyroscopeMagnitudeMean()
FrequencyBodyGyroscopeMagnitudeSTD()
FrequencyBodyGyroscopeMagnitudeMeanFreq()
FrequencyBodyGyroscopeJerkMagnitudeMean()
FrequencyBodyGyroscopeJerkMagnitudeSTD()
FrequencyBodyGyroscopeJerkMagnitudeMeanFreq()
Angle(TimeBodyAccelerationMean,Gravity)
Angle(TimeBodyAccelerationJerkMean),GravityMean)
Angle(TimeBodyGyroscopeMean,GravityMean)
Angle(TimeBodyGyroscopeJerkMean,GravityMean)
Angle(X,GravityMean)
Angle(Y,GravityMean)
Angle(Z,GravityMean)
Subject
Activity
```

## Data Transformation
A new data table was created using aggregate by Subject and Activity.
The average of each variable was taken for each activity and each subject and 
the results can be examined in the file named `Final_table.txt`.




