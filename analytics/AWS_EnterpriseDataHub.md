# Enterprise Data Hub in AWS 
> A unified analytics platform for service delivery and insights manangers to retrive accurate north-star metrics on a monthly and quarterly basis and extract actionable insights

## Problem Statement
* Data points are fragmented from various sources such as PDFs, chatbot and call logs
* Critical KPIs are required to be updated with both historical data from legacy platform and new data from incumbent cloud platform. 
* ~50,000 cases/month from various channels such as physical walk-ins, emails, web portal, call stream and interactive chatbot.  

## Business Opportunity
1. Create a one-stop data analytics platform where users can generate and view reports from a single source of truth
2. Address discoverability gap and accelerating time-to-insights
3. Enable management to obtain a 360 view of contact centre operations


## Solution
1. Integrate data sources into a single data lake.
2. Data processing job will be automated and event-driven leveraging message queues and event buses.
3. Data is ingested from isolated virtual private cloud (VPC) accounts to accomodate air-gapped netowrk architecture.
4. PII information will be encrypted to SHA-256 UUID during migration to accomomdate data residency requirements.

## High Level Design
![EDHHLD](./images/EDH_HLD.png)


## Context Diagram
![EDHContextDiagram](./images/EDH_ContextDiagram.png)


## Architecture Trade-Offs
* Batch trades freshness for simpler, predictable processing
* Quality checks reduce incomplete or inconsistent reporting
* S3 preserves original data; lifecycle policies * manage storage cost
* Redshift provides governed reporting; Athena supports flexible analysis
* Role-based access separates business, analyst and admin responsibilities
* Monitoring, metadata and notifications support reliable operations


## Sequence Diagram
![SequenceDiagram](./images/HLD_DE_SequenceDiagram.png)


## Business Outcomes


## Point of Failure and Mitigation