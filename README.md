# Automate-Data-Lake-using-AWS-Lake-Formation

## Objective

- Create an AWS Glue workflow using a Lake Formation blueprint.
- Automate the Lake Formation data lake setup process with an AWS Glue workflow.
- Create a custom AWS Glue workflow.

## Step 1: Set up Lake Formation

### Task 1.1: Register your Amazon S3 storage

Lake Formation manages access to designated storage locations in Amazon S3. Register the storage locations you want to be part of the data lake.

<img width="655" height="115" alt="{FBF1674C-F62F-4DBC-B603-F0ADEFFEE1A6}" src="https://github.com/user-attachments/assets/4cc46b81-2db8-4eb0-8342-80aaceb93c1a" />

1. Add myself
2. Choose Data lake locations

<img width="334" height="229" alt="{BEA34675-16A9-4CB1-881C-0D6C1A5F8014}" src="https://github.com/user-attachments/assets/6b9eefe7-419a-4a52-9d1d-1bf327b2ee3c" />

3. Click on register location

<img width="1844" height="511" alt="{C935A24C-06C4-4AB1-8169-D2FD30A39C0F}" src="https://github.com/user-attachments/assets/24e7c9a4-4e91-4042-93b8-159fd6b451a7" />

4. Fill details of s3 URl
5. Choose a value for IAM role from the drop down
6. Permision mode -> Lake formation

<img width="1825" height="230" alt="{97967CAE-F353-4D51-8E46-ABEB64818514}" src="https://github.com/user-attachments/assets/71382834-f389-4b5b-bb0e-5a26cff6d86e" />

7. Click Register location
8. Goto permissions

<img width="329" height="197" alt="{D25BD138-72FC-4FAD-A788-6F9C2762CDD0}" src="https://github.com/user-attachments/assets/ab05e2ea-b3d5-46e6-a44c-9574057a69bb" />

9. Click on Grant

<img width="751" height="646" alt="{60B55263-3E29-4DDD-944E-75B57D0D995F}" src="https://github.com/user-attachments/assets/7f1241a4-9070-4f7f-9d24-5ab1b6e4c31f" />

10. Pick IAM users and role
11. Paste your storage locations path
12. Click Grant

Amazon S3 bucket data/ folder is now registered as the storage location for your data lake.

### Task 1.2: Create a database

1. Create database - in data catalog click on create databases

<img width="326" height="302" alt="{A2997B18-A297-4AD1-8BAC-A4A618E72506}" src="https://github.com/user-attachments/assets/cd8a16f5-4d87-4b70-a90a-1dda108ba471" />

<img width="998" height="765" alt="{4D2FE9E6-26B2-471E-AA75-39FAC571E38D}" src="https://github.com/user-attachments/assets/10116e87-e587-4be9-a460-3f1bd1020e59" />

2. Provide the name of db
3. Provide the location
4. Click create database

I have successfully registered your Amazon S3 data storage and created a database.

## Step 2: Use a Lake Formation blueprint to create an AWS Glue workflow

A workflow encapsulates a complex multi-job extract, transform, and load (ETL) activity. Workflows generate AWS Glue crawlers, jobs, and triggers to orchestrate the loading and updating of data. Lake Formation runs and tracks a workflow as a single entity. You can configure a workflow to run on-demand or on a schedule.

Workflows you create in Lake Formation are visible in the AWS Glue console as a directed acyclic graph (DAG). Each DAG node is a job, crawler, or trigger. To monitor progress and troubleshoot, you can track the status of each node in the workflow.

1. Select Blueprints in ingestion

<img width="328" height="91" alt="{FBC50FA5-A4DD-4E94-943F-957951B1C4C9}" src="https://github.com/user-attachments/assets/f2ea9e07-f25b-4076-9d9b-0c6156c6c6ab" />

2. USe blueprint
3. Choose Blueprint type

<img width="880" height="465" alt="{1C16798D-2D7F-4A6B-892C-C84EE6447698}" src="https://github.com/user-attachments/assets/1528a416-073a-4f08-bb3c-c3c71d9dd854" />

4. Import source

<img width="1243" height="325" alt="{1B65B4B0-BE58-4436-83C6-A856754C3074}" src="https://github.com/user-attachments/assets/3003a136-5384-4a52-bec7-d2a5bb579e48" />

5. Import Target

<img width="1293" height="464" alt="{41690500-D8C8-474B-B538-0AB57DE139A1}" src="https://github.com/user-attachments/assets/882b4cae-3a92-46f3-a1d9-e58aa94ff1cd" />

6. Pick target database -> paste s3 url -> data format as Parquet

7. Import frequency

<img width="1249" height="225" alt="{078AC287-8C5E-4352-8543-6EC93DFDE531}" src="https://github.com/user-attachments/assets/ef05768a-073d-41e8-bfdc-33862275b164" />

8. Import options

<img width="1479" height="548" alt="{F6A464ED-9D95-4603-BAC2-03DCB99F4234}" src="https://github.com/user-attachments/assets/d8eec6d7-4d45-4672-b9a6-13e871113867" />

9. Enter Workflow name -> Pick IAM role -> Enter table prefix -> Create

You have successfully used a Lake Formation blueprint to create an AWS Glue workflow that automatically adds new content to your data lake.

## STEP 3: Run and monitor the workflow

### Task 3.1: Run the workflow

1. Start the workflow
2. Next goto Glue

<img width="554" height="162" alt="{9DBCC3A8-99DE-4D70-9F09-4E0EDF4D9836}" src="https://github.com/user-attachments/assets/1a98cca9-4cb6-419a-8b2d-e8b2a57e1c2e" />

3. In Data Integration and ETL choose Workflows (orchestration)

<img width="307" height="457" alt="{4BC221C5-8414-487B-BCB1-9C63EEE2A9B6}" src="https://github.com/user-attachments/assets/48160dfe-984c-492f-9f2f-84c9be218b6e" />

4. Goto history tab -> choose your run -> view run details

<img width="1371" height="698" alt="{835227B6-17AF-4F9E-924D-23798D3788CF}" src="https://github.com/user-attachments/assets/f0e8f0f4-b66f-4c1f-865c-6fe1c3a7c091" />

- A start node that starts your workflow.
- A pre_crawler job node that changes the workflow state to DISCOVERING.
- A pre_crawler trigger node that starts the crawler.
- A crawler node that discovers the source schema.
- A post_crawler trigger node that launches a post_crawler job node.
- A post_crawler job node that changes the workflow state to IMPORTING.
- An etl trigger node that launches an etl job node.
- An etl job node that completes the ETL work.
- A post_etl trigger that launches a post_etl job node.
- A post_etl job node that changes the workflow state to COMPLETED.

***All are succeeded

## Task 4.2: Explore AWS Glue workflows

1. Workflows (orchestration) -> Add workflow -> Name your workflow -> Create workflow

<img width="1220" height="409" alt="{F2E51263-4501-49D4-8ABB-83003B079950}" src="https://github.com/user-attachments/assets/31173b26-1d82-438c-844f-3706e924131b" />

you will see empty graph after click on the newly created workflow

<img width="1543" height="384" alt="{991C1FB4-214B-48D7-B8FF-51F17199AEF0}" src="https://github.com/user-attachments/assets/172ca102-0f35-44be-a741-e59f57985241" />

- Start: A node that starts the workflow.
- Trigger: A node that activates a job based on an event.
- Job: A node that completes work.
- Crawler: A node that discovers a source schema.

2. Click on Add trigger
3. Choose clone existing

<img width="882" height="320" alt="{229FBDD5-EB0A-46B6-87D8-BB3F754FE895}" src="https://github.com/user-attachments/assets/3da00640-8c95-4511-bd9c-309bec83c867" />

4. Choose your trigger -> Add

<img width="884" height="358" alt="{75C1D7FD-38AF-4071-96CE-EBEB857A527D}" src="https://github.com/user-attachments/assets/388ea4b6-ba86-4650-99bd-2a9899985749" />
** Start node is created

5. Next create trigger that will start AWS Glue Crawler
6. Click on Add trigger -> Add new

<img width="1008" height="655" alt="{44046A3C-2832-4B15-AEB2-A28B1FC5FF69}" src="https://github.com/user-attachments/assets/e8483849-8e34-4262-bb4f-d2d0efd14b3a" />

7. Name your trigger -> Trigger Logic -> Start after ALL watched event -> Add

<img width="1048" height="578" alt="{4FAC8982-856F-43F4-9B53-0D3408C6FEE4}" src="https://github.com/user-attachments/assets/f87e4793-0745-4298-87b9-9b2617875122" />

** Now we have 4 nodes

8. After previously added trigger -> click on Add node -> Choose Crawlers -> Add

<img width="1020" height="117" alt="{D361E4DB-2BCC-445F-B029-E9EB49A4231E}" src="https://github.com/user-attachments/assets/eb9be9d4-797e-4122-a1f8-a173722aa85a" />

** A trigger and a crawler are added. There are now four nodes in your workflow.

Next, create a trigger that waits for the crawler to finish.

9. Choose the crawler node, and then choose Add trigger.
10. Name your trigger -> Trigger Logic -> Start after ALL watched event -> Add
11. After the post_crawl_trigger node -> Add node -> Jobs tab -> Choose the job that contains post_crawl in its name

<img width="975" height="295" alt="{E452901A-3140-42BB-858B-4BFEE8617F12}" src="https://github.com/user-attachments/assets/2607c5f4-e4c9-4f2c-a5d0-4b2b68ec65d8" />

** A trigger and a job node are added. There are now six nodes in your workflow.

At this point, your workflow starts a job that triggers a crawler. Then, a trigger notifies the next job when the crawler is done.

<img width="1237" height="257" alt="{3B1F0177-BC73-4EE9-A916-61F25FF1A185}" src="https://github.com/user-attachments/assets/812bd4e0-3e31-48e9-a8c3-10406a689018" />

12. Create a trigger that waits for the ETL job to finish.
13. Choose the crawler node, and then choose Add trigger -> Add node -> Jobs tab -> Choose the job that contains post_crawl in its name

<img width="1365" height="302" alt="{9EB18D2D-2882-44A3-9918-A7E3A11301A7}" src="https://github.com/user-attachments/assets/9f5cc503-80b3-4fd4-8509-4a508fb3e83c" />

** A trigger and a post_etl job node are added. There are now 10 nodes in your workflow.

## Conclusion
You have successfully done the following:

- Created an AWS Glue workflow using a Lake Formation blueprint.
- Automated the Lake Formation data lake setup process with an AWS Glue workflow.
- Created a custom AWS Glue workflow.
































