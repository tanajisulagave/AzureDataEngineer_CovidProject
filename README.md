
****Azure Data Engineer Project - Covid 19 by Ramesh Ratnswami****

**Architecure Diagram :-**

![Covid Reporting Project](https://github.com/user-attachments/assets/06bd2707-787a-4255-a748-db0b4369fb19)

**Data Ingestion**

**Model 1:-** Ingesting Data from Blob storage
	In this model we are ingesting data from  storage account(Blob storage) and load into ADLS gen 2 account
 	
  Azure Data Factory:-
  	1)Validation Activity:- This activity looking the file present in stotage location or not
     	2)Get MetaData:- This activity check meta data of the file such as countof columns, size, File exists or not .
       	3)If Acitivty:- Based on output of the Getmeta activity IF activity execute.
	4)Copy Acitivty:- This activity take data from blob storage and load into ADLS Gen2 account.


**Model 2:-** Ingesing data from HTTP website and load into ADLS gen 2 account
	we have 4 files on covid 19 website we 

 **Data Transformation**

 
