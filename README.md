# Orka_DE_Coding_challenge
# Data Engineer Orka Coding challenge solution Documentation

Data pipeline documentation that outlines approach to the solution

## Data pipeline Summary
|----------------------------------|------------------------------------------------------------------------------------------------------|
|**********************************|******************************************************************************************************|
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Aspect                            | Description
|----------------------------------|------------------------------------------------------------------------------------------------------|
|**********************************|******************************************************************************************************|
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Overview                          | The solution outlines the following aspects:
|                                  | 1) read from 3 different sources into SQLite DB tables
|		                               | 2) perform validation on data ingested into SQLite tables
|		                               | 3) create a target table after performing transformation on the input tables
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Architecture                      | Flat single pipeline from sources -> SQLite3 tables (Data lake imitation) -> Target SQLite3 table
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Data Sources                      | Local system files, 3 -> JSON file, CSV file, SQLite3 table
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Data Transformation               | Stage #1: Data sources                         -> SQLite3 tables (Data lake imitation)
|                                  | Stage #2: SQLite3 tables (Data lake imitation) -> Target SQLite table (SQL Join operation)
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Data Storage                      | Local System RAM
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Data Processing and Orchestration | Python Runtime
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Data Destinations                 | SQLite3 table
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Monitoring and Alerting           | Python coding guardrails
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Security and Access Control       | None considered
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Maintenance and Support           | 
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Version History                   | 1.0
|----------------------------------|------------------------------------------------------------------------------------------------------|
|Change Log                        | Initial commit
|----------------------------------|------------------------------------------------------------------------------------------------------|


## SW pre-requisites/ installation
1) SQLite3
	1) Visit the official SQLiteStudio website at https://sqlitestudio.pl/index.rvt.
	2) On the website, navigate to the "Download" section.
	3) Select the appropriate version of SQLiteStudio for your operating system (Windows, macOS, Linux).
	4) Download the installer for your operating system.
	5) Run the downloaded installer.
	6) Follow the instructions in the installer to complete the installation.
	7) Once the installation is complete, you should be able to launch SQLiteStudio from your application menu or desktop shortcut.

2) Python 3.7 or higher (also install python packages json, pandas, sqlite3)
	1) Visit the official Python website at https://www.python.org/downloads/.
	2) Click on the "Downloads" tab.
	3) Scroll down and select the latest Python 3.x version for Windows/ Mac/ Linux.
	4) Download the installer appropriate for your system (32-bit or 64-bit).
	5) Run the downloaded installer.
	6) In the installation wizard, make sure to check the box that says "Add Python to PATH" and then click "Install Now".
	7) Follow the instructions in the wizard to complete the installation.
    8) Run the command: 'pip install json pandas sqlite3'

3) Pycharm (IDE) or any other Code editor to view code


## Program Execution steps
1) Place all files under the unzipped folder in a single file location
2) Open the main.py from any of the IDE and execute from the IDE or
3) Open a terminal or command prompt
4) Navigate to the directory where you saved the main.py Python file using the cd command (e.g., cd path/to/file)
5) Once you are in the correct directory, you can run the Python program by entering the command: python3 main.py


## Random Notes/ Thought process documentation
We need to follow principle of decoupling Data ingestion logic from Data ETL logic.
Also make code as generic as possible- for purpose of reusability 
Code so that it supports extensibility, to enable adding new modules to existing functionality

While designing a solution for the DWH problem, I thought it would be better if we started with maintaining all raw data into a Lake data table, since data is coming in from various different data sources; so that this would give us data in its 'raw' form, to better perform any data profiling and understand it.

Once all data is in the data lake table (SQLite db table); we'll need to decide what columns from the lake tables are really important, keeping in mind the target data model.

Take forward only the needed columns from the lake tables into another 'hub' stage. Perform any transformations needed to make data consistent and to maintain integrity.


## Next steps/ Potential for improvement
1) Move the table schemas into a separate json file, to make it generic and a one place stop for all table schemas.
2) Handle logic for (Change Data capture) and incremental data loads into the lake from the original source data.
3) Currently the data stored in the csv file is throwing a warning with regard to pandas deducing the schema automatically. This can be gracefully handled.
4) Date formats across the data sources are inconsistent. This can be fixed to become consistent.

