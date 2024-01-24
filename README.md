# Tokyo-olympic-azure-data-engineering-project
In this project, we will be using the various Azure data services which are used for Data Ingestion, Transformation and loading . The services are Azure Datafactory, Azure Databricks, Azure Data Lake Storage Gen2(ADLS), Azure synapse analytics, Azure Serverless Database and Power BI.

### Overview
Here, we are extracting the data from an external data source using a service in azure called as Azure Datafactory, which is used to create piplines and to provide connection using various external sources. After making the connection, we will store the data in ADLS . Then we will perform the transformation by cleaning the data, removing the duplicates, and changing the datatypes according to the source file.

The transformed data has been then stored in another container in ADLS and move the data to Azure synapse analytics for analysis. In synapse analytics , we do query processing to find out the required insights from the data. We will also store the same data into the SQL serverless database so other people in the organization can get access to it.

Finally, we will prepare the dashboard using power BI.

### Prerequisites
Before you get started with this project, make sure you have the following prerequisites in place:

1. Laptop: You'll need a laptop or computer to work on this project

2. Stable Internet Connection: Ensure you have a stable internet connection for accessing cloud services and resources

3. Basics of Python and SQL: Familiarity with Python and SQL will be beneficial for working with data processing and analysis tasks

4. Azure Account: You'll need an Azure account to utilize Azure services such as Data Lake Gen2, Azure Data Factory, Azure Databricks, and Azure Synapse Analytics
   
5. Power BI dekstop: If you are thinking to create dashboard you need to install power bi dekstop

### Data Source
Original Dataset link from kaggle: https://www.kaggle.com/datasets/arjunprasadsarkhel/2021-olympics-in-tokyo.

If you want to download same dataset in csv format please go to the Data folder of my same project github repository.

### Services/Tools Used
1. Azure Data Factory
2. ADLS Gen2
3. Azure Databricks
4. Azure Synapse Analytics
5. App Registrations
6. Azure SQL serverless database
7. Power BI Dekstop

### Project Architecture
To visualize the architecture of this project, please refer to our Miro board:

![architecture](https://github.com/AnkDug/tokyo-olympic-azure-data-engineering-project/assets/55326423/9c5cc667-fdcc-45e4-b1ea-86114d202270)



##### 1. Data Ingestion
We already understood that we are using the Kaggle data - 2021 Olympics as our data source, then we will copy the data from data source to the ADLS using Azure data factory by creating linked service between azure data factory and the data source.
Firstly, we have created the Storage Account and containers with folders for storing the raw data and transformed data.

Next, we will create the Azure Data Factory and make a connection with the source by creating linked connections.

Please refer the Screenshot 1,2 & 3 given in the same repository. 

#### 2. Data Transformation and Loading
After the data gets stored in the Data Storage, then we will make another connection to azure databricks using an App registration service.
Note: Do not share the Client ID and Tenant Id with anyone and also the secret value.

there we will perform some pyspark transformations to filter the data , and change the datatypes of the data according to the requirement. Please refer the pyspark script of data transformation.

The used pyspark code in the project is under the code section. During the process , you might some error due to the access, there we should provide an access to the Storage Blob Data Contributor.

After applying the above tranformations, again we will store the data into ADLS (data storage). From there, the azure synapse analytics uses the data from ADLS.

Also we stored the same data by creating views into the different serverless SQL Database so other people in the organization can see it and easily connect it to the dashboard.

Please refer the Screenshot 4,5,6 & 7 given in the same repository. 

#### 3. Data Analysis
The penultimate step here after doing transformation is to do some analytics by loading the data to azure synapse analytics and find various insights from the transformed data. Please refer the synpase analytics file for this.

Ran different SQL queries using Azure Synapse Analytics to gain insights from the transformed data. Identified trends, statistics, and patterns related to the Olympics data. Used Power BI to connect the data from Data Lake Storage Gen2 to visualize the data.

#### 4. Visualization
Please refer the image of power BI dashboard

![image](https://github.com/AnkDug/tokyo-olympic-azure-data-engineering-project/assets/55326423/dd537a66-8cd4-4ffa-91b4-2bb37c5ea0bf)

### Refrences:
Complete guide for this project by Darshil Parmar- https://www.youtube.com/watch?v=IaA9YNlg5hM

Power BI- https://www.youtube.com/watch?v=V-s8c6jMRN0 & https://www.youtube.com/watch?v=Rpa8mDH7mes&t=1987s








