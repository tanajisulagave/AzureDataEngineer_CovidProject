
****Azure Data Engineer Project - Covid 19 by Ramesh Ratnswami****

**Architecure Diagram :-**

![Covid Reporting Project](https://github.com/user-attachments/assets/06bd2707-787a-4255-a748-db0b4369fb19)

**Data Ingestion**

![image](https://github.com/user-attachments/assets/adaac4cc-489a-42d8-ab59-231d809945e6)



**Model 1:-** Ingesting Data from Blob storage
	In this model we are ingesting data from  storage account(Blob storage) and load into ADLS gen 2 account
 
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

![image](https://github.com/user-attachments/assets/37ed783f-dc48-464c-a325-69ef38a42661)

 
**Model 3:-** 	**Data Transformation using Dataflows , Azure HDInsights and Azure Databricks**
 
In this model we are transforming data with using various tool and transformed data will load into processed folder in ADLS gen 2 account.

A)	**Azure Data Flows:-** We are creating data flows for transforming data and cleanined data will load into Processed container in ADLS gen 2 account using Dataflow activity in Azure Data Factory.

Example:-

![image](https://github.com/user-attachments/assets/cc4660a1-fc93-4915-a6ba-98945e11893b)

B)	**Azure HDInsight:-** we are transfoming testing file using this Azure service 
	for this service we need to create Managed Identity and provide access to this managed identity into ADLS gen2 cotainer using IAM

C)	**Azure Databricks:-** Transforming Population File	
		By using sevice principle we can mount the ADLS Gen 2 container into ADB using Pysprk.
		we can create pyspark notebook for transorming the data and will load into processed container.

Create Pipeline into ADF and call above 3 activity for transforming the data.

 
 **Data Load into Azure SQL server Database**

![image](https://github.com/user-attachments/assets/fce45dbe-f4e0-4b2d-9b3d-eda4010f9bdd)

we have transformed data into ADLS gen 2 account now we need toadd this data into database 

 
