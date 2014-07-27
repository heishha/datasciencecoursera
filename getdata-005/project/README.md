### run_analysis.R
#### Analysis of Human Activity Recognition Using Smartphones Dataset

#### Author
A H Hsieh
https://github.com/heishha

#### Raw data
The script `run_analysis.R` uses the UCI Human Activity Recognition Using Smartphones Dataset
as described at
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones# (retrieved 26 Jul 2014).

#### Script behavior
The script downloads the data file and unzips it if the data has not already been downloaded (into a subdirectory named "data").
Out of the full data set, the script deals only with the features estimates data involving means and standard deviations. The script includes mean frequency and angles between mean vectors in the data of interest.
The script merges the subject, features of interest, and activity data from the separate raw data files. It combines the training and test data, then finds the average of the features estimates of interest per subject, per activity.

#### Name conversion details
The feature estimate column names in the output are drawn from the feature estimate names in the raw data, except with all "(", ")", ",", "-" characters converted to ".". For example, the raw data feature estimate name
```
tBodyAcc-mean()-X
```
is converted to
```
tBodyAcc.mean...X
```
One extra conversion is that the feature estimate name in the raw data:
```
angle(tBodyAccMean,gravity)
```
is further normalized to indicate that the gravity vector is the mean:
```
angle.tBodyAccMean.gravityMean.
```
A second extra conversion is that the feature estimate name in the raw data:
```
angle(tBodyAccJerkMean),gravityMean)
```
is further normalized to correctly remove the "." replacement for the extraneous ")":
```
angle.tBodyAccJerkMean.gravityMean.
```

#### Output
The resulting data is output into a file named `data/tidyHARAverages.txt`. 
The values for the features in this tidy data set are the **averages** of the given features per subject, per activity.

#### Handling the output
The result file is best read into R using 
```
read.table( "tidyHARAverages.txt", header = TRUE)
```
