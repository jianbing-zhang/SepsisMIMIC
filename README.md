# SepsisMIMIC
Sepsis prediction during ICU Stays	

## Get the results from the sample data provided
Run Modeling.ipynb in bigdata docker environment with the provided data H0 to H24.	
This jupyter notebook builds the predictive models from the ETL results and compares the performance on different hours preceding sepsis onset.	

## Get the results from the MIMIC III database

Follow these instructions to get the final predictive modeling for Sepsis Benchmarking of ICU Stays from MIMIC III database.

- Download all csv from MIMIC III, build the postgreSQL database with the given code from MIMIC.
mimic-code/buildmimic/postgres

- Python3 Anaconda: 
  Before running ETL01.py, gather the list of routine vital signs and save it to a csv in the data folder.
  On the command line, you can run in the data directory:
    cat D_ITEMS.csv | grep "Routine Vital Signs" > routine_vitals_signs.csv
    Or you can move the routine_vitals_signs.csv present in this directory to the data directory.
  Make sure you run the following code in the data directory or in a directory where the data directory can be reached through cd ../data/
  Run ETL01.py. This script will output a file called routine_vitals_events.csv in the data directory.
  Run ETL02.py. This script will save a file called ETL_output.csv, which contains the cleaned feature data.
  Run ETL03.py. This script will save two files, one called antibiotics.csv and the other antibiotics_culture.csv to the data directory.
  Run ETL04.py. This script will save one file, ETL_04_output.csv to the data directory.
  
- to be filled: sql

- Run ETL_01_....ipynb to build the cohort. Note that you must add your own database connection information to make this notebook run.	
- (Add more ETL part)	

- Follow the ETL_04_output.csv result from last step, Spark Dataframe with scala was used to perform feature construction. 
 Follow the zeppelin notebook to get the final trainable dataframe. It will automatically save the csv to get the final trainable dataset.
 \- Environment: Spark DataFrame with Scala. 
 \- Zeppelin note: ETL_04_Feature_Construction.json
 \- Use the Zeppelin to import the above json file to get the runnable note. 
 \- Remember to change the file path of ETL_04_output.csv in the first block of zeppelin notebook.
    **The actual csv are provided in this repository (H0, H1, H2, H3, H4, H5, H24)**
