# Bias Testing Migration to Databricks
> Enabling data scientists to evaluate machine learning and generative AI application for bias outputs against verified demographic sources.

## Problem Statement
* High volume of machine learning and generative ai applications deployed in Databricks 
* Existing bias testing tool is avaliable in Hadoop environment
* Data residency requirements: Account number of customer which is PII cannot be migrated over the cloud environment

 ### Bias Testing Pipeline (AWS-Native)
 * Step Functions
    * Gives visual state tracking, retry/error handling per step, auditability at each stage of pipeline
 * Lambda Functions
    * Invokes pipeline to generate bias testing reults on a CRON schedule
* AWS Glue
   * Peform complex data transformation with encrypted and TransUnion data 

## Bias Testing Process
![BTHLD](./images/BT_Process.png)


## Tech Stack
* **Platform**: Databricks
* **Database**: PostgreSQL