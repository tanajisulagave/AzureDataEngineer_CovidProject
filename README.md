
****Azure Data Engineer Project - Covid 19 by Ramesh Ratnswami****

**Architecure Diagram :-**

![Covid Reporting Project](https://github.com/user-attachments/assets/06bd2707-787a-4255-a748-db0b4369fb19)

**Data Ingestion**

**Model 1:-** Ingesting Data from Blob storage
	In this model we are ingesting data from  storage account(Blob storage) and load into ADLS gen 2 account
 	
  Azure Data Factory:-
1)  Validation Activity:- This activity looking the file present in stotage location or not.
2)  Get MetaData:- This activity check meta data of the file such as countof columns, size, File exists or not .
3)  If Acitivty:- Based on output of the Getmeta activity IF activity execute.
4)  Copy Acitivty:- This activity take data from blob storage and load into ADLS Gen2 account.

**Model 2:-** Ingesing data from HTTP website and load into ADLS gen 2 account
We have 4 files on ECDC website we can ingesting those files and load into ADLS Gen 2 account
Note:- For saferside we can copy 4 files on GITHUB and use HTTP connector for Git Hub also.
1) Create one JSON file with Base URL , Relative URL and SinkFileName
  Example:-
      {
        "sourceBaseURL":"https://github.com",
        "sourceRelativeURL":"cloudboxacademy/covid19/raw/main/ecdc_data/cases_deaths.csv",
        "sinkFileName":"cases_deaths.csv"
        },
2)  Save JSON file on blob storage account container and create dataset for JSON connector
3)  Lookup Activity : Create this activity for looking up data this file
4)  Foreach activity- This activity take output data from lookup file provide this details to copy acitity to copy data from HTTP and load to ADLS gen 2 
5)  Copy Activity:- This activity take data from HTTP / GITHUB and load into Gen 2 account

 **Data Transformation**

 
