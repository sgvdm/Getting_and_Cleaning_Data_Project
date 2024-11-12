
# Getting and Cleaning Data Project

The "Getting and Cleaning Data" project processes the **Human Activity Recognition Using Smartphones** dataset into a tidy format suitable for analysis. This project involves transforming raw sensor data from wearable devices to produce a clean dataset with averages of selected variables for each subject-activity combination.

## Project Overview

This project is part of a data cleaning course focused on preparing data from accelerometer and gyroscope sensors attached to 30 subjects performing various activities. The resulting tidy dataset captures the average of each variable for every activity and subject.

## Files

1. **`run_analysis.R`**: The main R script that downloads, unzips, processes, and tidies the data.
2. **`tidy_data.txt`**: The final tidy dataset with averages for each activity and each subject.
3. **`CodeBook.md`**: Describes variables, data transformations, and the final dataset structure.

## Script Workflow (`run_analysis.R`)

1. **Data Download and Extraction**: Downloads and extracts the dataset.
2. **Data Merging**: Combines training and test datasets.
3. **Extraction of Measurements**: Filters columns with mean and standard deviation measurements.
4. **Labeling Activities**: Replaces activity codes with descriptive names.
5. **Renaming Columns**: Improves column names for readability.
6. **Aggregating Data**: Computes the average of each variable grouped by subject and activity.
7. **Saving Output**: Exports the tidy dataset to `tidy_data.txt`.

To run the script, execute the following command in R:

```r
source("run_analysis.R")
```

## Additional Instructions

This project showcases data cleaning using the **UCI HAR Dataset** collected from Samsung Galaxy S smartphones. The main files in the repository include:

- **`run_analysis.R`**: The R script performing data cleaning and transformation.
- **`tidy_data.txt`**: The final tidy dataset.
- **`CodeBook.md`**: Description of the dataset variables and transformations.

### Data Cleaning Steps

1. Merges training and test datasets.
2. Extracts measurements on mean and standard deviation.
3. Uses descriptive activity names.
4. Labels dataset columns with clear names.
5. Creates a second tidy dataset with averages for each variable by activity and subject.

To execute the analysis, open `run_analysis.R` in R and execute it. The script will download, clean, and output `tidy_data.txt` in the working directory.


Please consult the Codebook.md for details on variables and transformations performed.
