# Smart-Vehicle-Monitoring-System
Azure Data Engineering

This Project gives insight into efficient Monitoring of Vehicle using Azure.

![Architecture diagram](https://user-images.githubusercontent.com/107489749/209940216-e9e32d59-2864-4dbe-a351-7759cdfa914d.png)

## Resources used 

1. Amazon S3 
2. Data Factory
3. Key vault
4. Datalake Gen2
5. SQL database

## Process step

1. IOT device installed in the vechicle send data (engine temperature, location, km.. etc) to Amazon S3 bucket every fifteen minutes in hierarchical manner (*folder name/year/month/date/files.json*).
2. ADF will trigger a pipeline every one hour and collect all the newly received files and move it Azure Gen2 account (*landing folder*) in hierarchical manner.
3. Once the files received in landing folder, Azure Function will validate the whether received file is a json file or not.
4. If the validation is sucessufull, then file moved to *staging* folder else moved to *rejected* folder.
5. File received in the *staging folder* is further processed by second pipeline of ADF and stored in SQL database.


## Functionalities covered as part of This project

1. Role Based Access, Access Control List, Managed Identity *(Azure/AWS)*
2. Data Factory - Copy activity, Storage Event trigger, Linked service, pipeline/activity parameter 
3. Azure Functions 
4. Key vault - Keys, secrets  
5. Datalake Gen2 - Shared Access Signatures (SAS), Lifecycle management
6. AWS S3 - S3 bucket, Acess Keys, ACL ,IAM polices, Cross-origin resource sharing (CORS)
