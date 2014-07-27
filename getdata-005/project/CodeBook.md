## Analysis of Human Activity Recognition Using Smartphones Dataset

### Script Overview
#### Raw data
The script `run_analysis.R` uses the UCI Human Activity Recognition Using Smartphones Dataset
as described at
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones# (retrieved 26 Jul 2014).

#### Script behavior
The script downloads the data file and unzips it if the data has not already been downloaded (into a subdirectory named "data").
Out of the full data set, the script deals only with the features data involving means and standard deviations.
The script merges the subject, features of interest, and activity data from the separate data files. It combines the training and test data, then finds the average of the features of interest per subject, per activity.

#### Output
The resulting data is output into a file named `data/tidyAverages.txt`. 
The values for the features in this tidy data set are the **averages** of the given features per subject, per activity.

#### Handling the output
The result file is best read into R using 
```
read.table( "tidyAverages.txt", header = TRUE)
```

### Source Data
The following description of the raw data source is drawn directly from the feature description in the
data bundled at http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones#
(retrieved 26 Jul 2014).

> The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 
> 
> The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. 

#### Source data reference

> [1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

#### Feature Selection 

The following description of the raw data source is drawn directly from the feature description in the
data bundled at http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones#
(retrieved 26 Jul 2014).

> The features selected for this data set come from the accelerometer and gyroscope 3-axial raw signals 
> tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a 
> constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass 
> Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration 
> signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) 
> using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 
> 
> Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk 
> signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional 
> signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, 
> tBodyGyroMag, tBodyGyroJerkMag). 
>
> Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, 
> fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to 
> indicate frequency domain signals). 
> 
> These signals were used to estimate variables of the feature vector for each pattern:  
> '-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
> 
> tBodyAcc-XYZ

> tGravityAcc-XYZ

> tBodyAccJerk-XYZ

> tBodyGyro-XYZ

> tBodyGyroJerk-XYZ

> tBodyAccMag

> tGravityAccMag

> tBodyAccJerkMag

> tBodyGyroMag

> tBodyGyroJerkMag

> fBodyAcc-XYZ

> fBodyAccJerk-XYZ

> fBodyGyro-XYZ

> fBodyAccMag

> fBodyAccJerkMag

> fBodyGyroMag

> fBodyGyroJerkMag


From each of these signals, where applicable, the following variables were estimated.

mean: Mean value

std: Standard deviation

meanFreq: Weighted average of the frequency components to obtain a mean frequency


Additional vectors were obtained by averaging the signals in a signal window sample for angle variables. 

angle.gravityMean

angle.tBodyAccMean

angle.tBodyAccJerkMean

angle.tBodyGyroMean

angle.tBodyGyroJerkMean


See the full enumeration of the table columns below

### Units
Features are normalized and bounded within [-1,1].

### Data Dictionary
* Subject
> 1...30
> Unique identifier for each volunteer subject

* Activity
> Activity identifier
  1. WALKING
  2. WALKING_UPSTAIRS
  3. WALKING_DOWNSTAIRS
  4. SITTING
  5. STANDING
  6. LAYING

The following columns are the averages of the data for the feature variables as described in the section 
**Feature Selection**. The column names are composed as follows:
`feature`.`estimated variable`.`XYZ component, if applicable`

* tBodyAcc.mean...X
* tBodyAcc.mean...Y
* tBodyAcc.mean...Z
* tBodyAcc.std...X
* tBodyAcc.std...Y
* tBodyAcc.std...Z
* tGravityAcc.mean...X
* tGravityAcc.mean...Y
* tGravityAcc.mean...Z
* tGravityAcc.std...X
* tGravityAcc.std...Y
* tGravityAcc.std...Z
* tBodyAccJerk.mean...X
* tBodyAccJerk.mean...Y
* tBodyAccJerk.mean...Z
* tBodyAccJerk.std...X
* tBodyAccJerk.std...Y
* tBodyAccJerk.std...Z
* tBodyGyro.mean...X
* tBodyGyro.mean...Y
* tBodyGyro.mean...Z
* tBodyGyro.std...X
* tBodyGyro.std...Y
* tBodyGyro.std...Z
* tBodyGyroJerk.mean...X
* tBodyGyroJerk.mean...Y
* tBodyGyroJerk.mean...Z
* tBodyGyroJerk.std...X
* tBodyGyroJerk.std...Y
* tBodyGyroJerk.std...Z
* tBodyAccMag.mean..
* tBodyAccMag.std..
* tGravityAccMag.mean..
* tGravityAccMag.std..
* tBodyAccJerkMag.mean..
* tBodyAccJerkMag.std..
* tBodyGyroMag.mean..
* tBodyGyroMag.std..
* tBodyGyroJerkMag.mean..
* tBodyGyroJerkMag.std..
* fBodyAcc.mean...X
* fBodyAcc.mean...Y
* fBodyAcc.mean...Z
* fBodyAcc.std...X
* fBodyAcc.std...Y
* fBodyAcc.std...Z
* fBodyAcc.meanFreq...X
* fBodyAcc.meanFreq...Y
* fBodyAcc.meanFreq...Z
* fBodyAccJerk.mean...X
* fBodyAccJerk.mean...Y
* fBodyAccJerk.mean...Z
* fBodyAccJerk.std...X
* fBodyAccJerk.std...Y
* fBodyAccJerk.std...Z
* fBodyAccJerk.meanFreq...X
* fBodyAccJerk.meanFreq...Y
* fBodyAccJerk.meanFreq...Z
* fBodyGyro.mean...X
* fBodyGyro.mean...Y
* fBodyGyro.mean...Z
* fBodyGyro.std...X
* fBodyGyro.std...Y
* fBodyGyro.std...Z
* fBodyGyro.meanFreq...X
* fBodyGyro.meanFreq...Y
* fBodyGyro.meanFreq...Z
* fBodyAccMag.mean..
* fBodyAccMag.std..
* fBodyAccMag.meanFreq..
* fBodyBodyAccJerkMag.mean..
* fBodyBodyAccJerkMag.std..
* fBodyBodyAccJerkMag.meanFreq..
* fBodyBodyGyroMag.mean..
* fBodyBodyGyroMag.std..
* fBodyBodyGyroMag.meanFreq..
* fBodyBodyGyroJerkMag.mean..
* fBodyBodyGyroJerkMag.std..
* fBodyBodyGyroJerkMag.meanFreq..

The following columns are the averages of the data for the averaged feature angle variables as described in the section 
**Feature Selection**. The column names are composed as follows:
angle.`feature``Estimated variable`.

* angle.tBodyAccMean.gravity.
* angle.tBodyAccJerkMean..gravityMean.
* angle.tBodyGyroMean.gravityMean.
* angle.tBodyGyroJerkMean.gravityMean.
* angle.X.gravityMean.
* angle.Y.gravityMean.
* angle.Z.gravityMean.


