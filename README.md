# Getting_and_Cleaning_Data_Project
Getting &amp; Cleaning Data Assignment / Coursera
# Human Activity Recognition Using Smartphones: Project Code Book

## Introduction

This code book describes the data, variables, and transformations used in the analysis of the Human Activity Recognition Using Smartphones dataset. It provides instructions on obtaining the data, running the analysis script, and interpreting the results.

## Data Source

- **Dataset**: Human Activity Recognition Using Smartphones
- **Source**: UCI Machine Learning Repository
- **URL**: [Dataset Link](https://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)
- **Citation**: Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. A Public Domain Dataset for Human Activity Recognition Using Smartphones. 21st European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013.

## Setup and Execution

### Download the Data

1. Download the dataset from the URL provided above.
2. Unzip the file into your R working directory, maintaining the folder structure.

### R Environment

- Ensure R (version 3.5.0 or later) is installed.
- Required package: `data.table` (version 1.14.0 or later).
- Install the package if necessary: `install.packages("data.table")`.

### Run the Analysis

1. Place the "run_analysis.R" script in your working directory.
2. In R or RStudio, run: `source("run_analysis.R")`.

## Script Overview: run_analysis.R

The script performs the following main steps:

1. **Loading and Merging Data**
   - Loads training and test datasets for subjects, activities, and measurements.
   - Reads feature vectors and activity labels.
   - Combines the training and test datasets using `rbind()`.

2. **Feature Selection**
   - Extracts only the measurements containing mean and standard deviation values.

3. **Descriptive Naming**
   - Adds descriptive activity names.
   - Renames dataset columns for clarity.

4. **Creating Tidy Data**
   - Groups by subject and activity, calculating averages for each variable.
   - Saves the tidy dataset to "tidy_dataset_with_average_values.txt".

**Note**: The code assumes that all data files are present in the same directory, unzipped, with their original names.

## Detailed Data Processing Steps

1. **Data Loading**:
   - Features and activity labels are loaded using `fread()`.
   - A custom function `load_data()` loads subject, activity, and measurement data for both training and test sets.

2. **Data Merging**:
   - Training and test datasets are combined using `rbind()`.

3. **Feature Selection**:
   - Only measurements containing "mean()" or "std()" are selected using `grep()`.

4. **Descriptive Naming**:
   - Activities are labeled with descriptive names by merging with activity labels.
   - `gsub()` is used to make variable names more readable.

5. **Tidy Dataset Creation**:
   - Data is grouped by subject and activity.
   - The mean of each measurement is calculated for each group.

6. **Output Generation**:
   - The final tidy dataset is written to "tidy_dataset_with_average_values.txt" using `fwrite()`.

## Variables in the Tidy Dataset

- **`subject`**: Participant identifier (integer, 1-30).
- **`activity`**: Activity performed (factor with 6 levels: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING).
- **Measurement Variables (3-68)**:
  - Time and frequency domain variables.
  - Prefixes include "Time" or "Frequency".
  - "Accelerometer" or "Gyroscope" indicates the sensor type.
  - "Body" or "Gravity" specifies the signal source.
  - "Jerk" denotes signals derived from body linear acceleration and angular velocity.
  - "Magnitude" represents the magnitude of three-dimensional signals.
  - "Mean" or "STD" indicates the type of measurement.
  - "X", "Y", or "Z" denotes the axis of measurement, where applicable.

  **Example variables**:
  - `TimeBodyAccelerometerMeanX`
  - `FrequencyBodyGyroscopeSTDY`
  - `TimeGravityAccelerometerMagnitudeMean`

## Output

- **File**: "tidy_dataset_with_average_values.txt"
- **Format**: Space-separated text file
- **Dimensions**: 180 rows (30 subjects * 6 activities) by 68 columns (subject, activity, 66 measurements)
- **Description**: Each row represents the average of each variable for a specific subject and activity.

## Notes

- The script uses `data.table` for efficient data manipulation.
- Only measurements explicitly labeled as "mean()" or "std()" in the original dataset are included.
- All measurements are normalized and bounded within [-1,1].
- The averages in the tidy dataset are calculated from these normalized values.

For more details on the original dataset and features, refer to the "features_info.txt" file in the original data package.

