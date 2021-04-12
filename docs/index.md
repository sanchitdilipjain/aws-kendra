## Amazon Kendra

**Introduction**
- Amazon Kendra is precise and simple to leverage enterprise search service that’s backed by machine learning. Kendra provides powerful natural language search functionalities to the websites and applications so the end-users can simply look up the information they need within the vast amount of content spread across your company.

**Tutorial**
- This tutorial will focus on below section
  
  - Deploy Kendra Index
  - Ingesting Documents
  - Adding FAQs

- Deploy Kendra Index

    - An index holds information that is indexed from a data source, documents that are added directly to the index, and FAQs. There are two methods to deploy an Index with Amazon Kendra, first is programmatically leveraging AWS CLI or the AWS SDKs and the second is via the Amazon Kendra console.
    - Follow the below steps to set up the Amazon Kendra index
    
        1. Traverse to the <a href="https://console.aws.amazon.com/kendra/">Amazon Kendra console</a> 

           <img src="images/image1.png" class="inline"/> 
           
        2. Select on Create an Index 

           <img src="images/image2.png" class="inline"/>    
        
        3. Specify index details, fill the following fields and choose Next

            - Index name: name of the index
            - IAM Role: IAM role you want to attach with the index

              <img src="images/image3.png" class="inline"/> 
        
        4. Configure user access control, we will select no for this tutorial
        
           <img src="images/image4.png" class="inline"/> 
        
        5. Click Developer Edition and click on Create.
        
           <img src="images/image5.png" class="inline"/> 
        
        6. Wait till the index deployment is completed.
        
           <img src="images/image6.png" class="inline"/> 
        
        7. After the index has been deployed we will be able to move to the next step.
        
           <img src="images/image7.png" class="inline"/> 

- Ingesting Document

    - There are 3 ways of ingesting documents to Amazon Kendra:
      - Connectors: S3, Salesforce, ServiceNow, RDS, Sharepoint, and, OneDrive
      - FAQ documents that contain questions and answers, that are ingested by using either the console or the CreateFaq API.
      - Using BatchPutDocument API that can take inline blobs and S3 locations for documents.
    - In this tutorial, we will index a set of AWS whitepapers in pdf format, these documents are persisted on separate directories within the archive depending on their category.
    - The dataset can be downloaded here: <a href="https://github.com/sanchitdilipjain/aws-kendra/blob/main/AWS_Whitepapers.zip">AWS_Whitepapers.zip</a> 
        
        1. Traverse to the <a href="https://console.aws.amazon.com/s3/">Amazon S3 console</a>
  
           <img src="images/image8.png" class="inline"/> 
           
        2. Create an S3 bucket to persist the documents and create the folder whitepapers

           <img src="images/image9.png" class="inline"/>   
           
           <img src="images/image10.png" class="inline"/> 
        
        3. Download the zip folder <a href="https://github.com/sanchitdilipjain/aws-kendra/blob/main/AWS_Whitepapers.zip">AWS_Whitepapers.zip</a>, Unzip it and upload it to S3 under whitepapers folder

           <img src="images/image11.png" class="inline"/> 
        
        4. Post that go to the <a href="https://console.aws.amazon.com/kendra/">Amazon Kendra console</a>, go to your index and click on Datasources
    
           <img src="images/image12.png" class="inline"/> 
        
        5. Click S3 and click on Add Connector
    
           <img src="images/image13.png" class="inline"/> 
        
        6. Provide a name for connector and Select on Next
    
           <img src="images/image14.png" class="inline"/> 
           
        7. Provide the S3 bucket detail where you uploaded the documents
    
           <img src="images/image15.png" class="inline"/> 
        
        8. Under Additional configuration secction add the S3 folder where we uploaded the documents and click Add 
    
           <img src="images/image16.png" class="inline"/> 
        
        9. Select a New IAM Role and provide name for the new IAM role
    
           <img src="images/image17.png" class="inline"/> 
           
        10. Under Set sync run schedule Select Run on demand and click on Next
    
            <img src="images/image18.png" class="inline"/> 
        
        11. Click on Add data source, After the creation process is complete, click on Sync Now.
    
            <img src="images/image19.png" class="inline"/>
            
            <img src="images/image20.png" class="inline"/>
            
            <img src="images/image21.png" class="inline"/>
            
            <img src="images/image22.png" class="inline"/>
            
            <img src="images/image23.png" class="inline"/>
        
        12. Now navigate to Kendra’s built-in Search Console to test the queries. For example **what service has eleven nines of durability?**

            <img src="images/image24.png" class="inline"/>
            
            <img src="images/image25.png" class="inline"/>
    
 - Adding FAQs
    
    - Amazon Kendra contains a deep learning model which look up precisely for frequently asked questions (FAQ) which are ingested as independent question-answer pairs. We can add questions and answers (FAQs) directly to the index using the console or the CreateFaq operation.
    - FAQ is save in a file that we can persist in S3 bucket. It can we a comma-separated values (.csv) files or, JSON files.
    - FAQ file can be downloaded here: <a href="https://github.com/sanchitdilipjain/aws-kendra/blob/main/FAQ.csv">FAQ.csv</a> 
       
        1. Traverse to the <a href="https://console.aws.amazon.com/s3/">Amazon S3 console</a>
  
           <img src="images/image8.png" class="inline"/> 
        
        2. Create a folder in the S3 bucket called faqs and upload the csv file.
  
           <img src="images/image26.png" class="inline"/> 
        
        3. Post that go to the <a href="https://console.aws.amazon.com/kendra/">Amazon Kendra console</a>, go to your index and click on FAQs
    
           <img src="images/image27.png" class="inline"/> 
        
        4. Select FAQ
  
           <img src="images/image28.png" class="inline"/> 
        
        5. Provide name for the new FAQ
  
           <img src="images/image29.png" class="inline"/> 
        
        6. Provide the FAQ file type i.e .csv file - Custom
    
           <img src="images/image30.png" class="inline"/> 
        
        7. Provide the S3 bucket detail where we uploaded the FAQ file
  
           <img src="images/image31.png" class="inline"/> 
           
        8. Select a New IAM Role and provide name for the new IAM role   
           
           <img src="images/image32.png" class="inline"/> 
           
        10. Click “Add” and After the FAQ is created you will see a message like this
            
            <img src="images/image33.png" class="inline"/> 
            
            <img src="images/image34.png" class="inline"/>  
        
        11. Now navigate to Kendra’s built-in Search Console to test the queries. For example **What is the AWS Well-Architected Framework?**

            <img src="images/image24.png" class="inline"/>
            
            <img src="images/image35.png" class="inline"/>  

