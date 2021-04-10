## Amazon Kendra

**Introduction**
- Amazon Kendra is precise and simple to leverage enterprise search service that’s backed by machine learning. Kendra provides powerful natural language search functionalities to the websites and applications so the end-users can simply look up the information they need within the vast amount of content spread across your company.

**Tutorial**
- This tutorial will focus on below section
  
  - Deploy Kendra Index
  - Ingestion Documents
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

- Ingestion Document

    - There are 3 ways of ingesting documents to Amazon Kendra:
      - Connectors: S3, Salesforce, ServiceNow, RDS, Sharepoint, and, OneDrive
      - FAQ documents that contain questions and answers, that are ingested by using either the console or the CreateFaq API.
      - Using BatchPutDocument API that can take inline blobs and S3 locations for documents.
    - In this tutorial, we will index a set of AWS whitepapers in pdf format, these documents are persisted on separate directories within the archive depending on their category.
    - The dataset can be downloaded here: <a href="https://github.com/sanchitdilipjain/aws-kendra/blob/main/AWS_Whitepapers.zip">AWS_Whitepapers.zip</a> 

 
        

