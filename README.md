## Repo for K. Zammit's Work on Ringed Seal Detector ##


## Folder: _config ##

- recipe files and config files 
______________________


## Folder: _lockbox ##

- all annotation tables (original and edited)
- original_file_locations.xlsx: original locations of files on drive
- all_file_durations.xlsx: file durations, used by create database 
______________________


## Folder: _template ##

- template structure for creating detector
______________________


## 1_create_database.py ##

- creates database .h5 file from annotation csvs and spectrogram config
- calls meridian_utils create_database function 
- needs the "all_file_durations.xlsx" file which is currently hardcoded from the input folder
- currently forces all labels to be 1 for "bark" 
- makes annotation tables into ketos format, generates selection tables with set duration, generates negative segments 
______________________


## 2_train_classifier.py ##

- creates a .kt model 
- uses spectro config, database file, recipe file 
- calls meridian_utils train_classifier function which uses ResNet structure
______________________


## 3_create_detector.py ##

- creates a detections.csv file for the audio files within the "audio" folder 
- uses the trained model and audio .wav files 
- calls meridian_utils create_detector function 
______________________


## create_annotation_csvs.py ##

- creates annotation tables from raven tables 
- inputs are output directory for tables, pathway to folder containing all selection tables, and output filenames 
- outputs .csv files and a .xlsx with a list of all annotations 

Steps: 
1. Concatenate selection tables and add "site_name" column 
2. Format the table: calculate start and end times, rename some columns, add annotation_id (number of annotation within the same file)
3. Split files into train, validation, and future will also have test 
______________________


## meridian_utils.py ##

- houses all meridian based functions to create database, train classifier, and create detector 
______________________


## toolbox.py ##

- calls plotting functions: call length scatter plot, plot spectrograms 
- calls write file locations script 
______________________


## toolbox_utils.py ##

- houses functions called by toolbox.py
______________________


