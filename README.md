# SepsisMIMIC
Sepsis prediction during ICU Stays	
We provide two ways to get our final models. One way is to use our provided data (folder H0, H1, H2, H3, H4, H5, H24) directly. The other way is to start from MIMIC III database. Both ways need to be run in bigdata docker environment.

## Method 1: Get the results from the sample data provided
Run Modeling.ipynb in bigdata docker environment directly with the provided data H0 to H24.	
This jupyter notebook builds the core predictive models from the ETL results and compares the performance on different hours preceding sepsis onset.	



## Method 2: Get the results from the MIMIC III database

Follow these instructions to get the final predictive modeling for Sepsis Benchmarking of ICU Stays from MIMIC III database.

- Download all csv from MIMIC III, build the postgreSQL database with the given code from MIMIC.
mimic-code/buildmimic/postgres

- Put all csv files in a location: /mnt/host/home/jbzhang/mimic/

- run ETL_00.sql with postgreSQL to get sepsis label

- Run ETL_01.ipynb to build the cohort. Note that you must add your own database connection information to make this notebook run.

- run ETL_02 to ETL_05 in Python3 Anaconda: 
  Before running, gather the list of routine vital signs and save it to a csv in the data folder.
  On the command line, you can run in the data directory:
    cat D_ITEMS.csv | grep "Routine Vital Signs" > routine_vitals_signs.csv
    Or you can move the routine_vitals_signs.csv present in this directory to the data directory.
  Make sure you run the following code in the data directory where all csv files from MIMIC located:


- run ETL_06.json to perform feature construction. It is a zeppelin notebook and must be run in the bigdata docker environment. This notebook will produce the data in this repository **(H0, H1, H2, H3, H4, H5, H24)**  

- run Modeling.ipynb to get the final model and results comparison
