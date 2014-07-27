### run_analysis.R

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
