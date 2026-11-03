# Sample Reference Architectures
The following repository is a collection of reference architectures for various business use cases ranging from AI, Analytics to large-scale project such as Migration and Security. Names of companies will be undisclosed for confidentiality and NDA compliance. 


[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)


## AI
* [Bias Detection in Public Cloud](/ai/Bias_Testing_to_Public_Cloud.md)
* [Agentic Data Translator](./ai/Agentic_Data_Translator.md)
* [Generative AI Evaluation Service](/ai/GenAI_Evaluation_Service.md)
* [GenAI Enterprise Knowledge Assistant in AWS](/ai/AWS_GenAI_Knowledge_Assistant.md)
* [Production Grade Agentic AI Blueprint](/ai/Agentic_AI_Blueprint.md)
* [AI Observability Toolkit](/ai/Observatory.md)
* [Policy-Driven Governance for Agentic Systems](./ai/Policy_Driven_AIGovernance.md) 

## Analytics
* [Enterprise Data Hub in AWS](/analytics/AWS_EnterpriseDataHub.md)
* [Lambda Architecture in Snowflake](/analytics/DataEngineering_LambdaArch.md)
* Databricks Unity Catalog Architecture

## Migration and Modernization
* Migration of workloads from on-prem to sovereign cloud


## Networking
* VPC Peering
* Air-Gapped Architecture
* [3-Tier Architecture in AWS](/networking/3Tier_AWS_Achitecture.md)
* [3-Tier Architecture in GCP](/networking/3Tier_GCP_Architecture.md)


## Security
* Secure an application using the STRIDE framework

```text 
reference-architecture/
|   AGENTS.md
|   CODE_OF_CONDUCT.md
|   CONTRIBUTING.md
|   LICENSE
|   README.md
|   structure.txt
|   
+---ai
|   |   Agentic_AI_Blueprint.md
|   |   Agentic_Data_Translator.md
|   |   AWS_GenAI_Knowledge_Assistant.md
|   |   Bias_Testing_to_Public_Cloud.md
|   |   GenAI_Evaluation_Service.md
|   |   Observatory.md
|   |   Policy_Driven_AIGovernance.md
|   |   ResponsibleAI_Architecture.md
|   |   
|   \---images
|           ADT_CoreGCO.png
|           ADT_Data_Products.png
|           AgenticAI_Blueprint.png
|           Bias_Testing_DBX.png
|           BT_Process.png
|           GenAi_Eval_Solution_Arch.png
|           GenAI_HLD.png
|           GES_HLD.png
|           GES_Workflow.png
|           Observatory.png
|           Sentry_Graph.png
|           
+---analytics
|   |   AWS_EnterpriseDataHub.md
|   |   DataEngineering_LambdaArch.md
|   |   
|   \---images
|           EDH_ContextDiagram.png
|           EDH_HLD.png
|           HLD_DE_SequenceDiagram.png
|           IVRS_EDH.png
|           LambdaArch_HLD.png
|           
+---devops
|       Kinesis_Firehose_TF.md
|       Web_App_Architecture.md
|       
+---interview-questions
|       AI-Architect.md
|       Data-Architect.md
|       
+---migration
|   |   Bitbucket_GitHub_Migration.md
|   |   Migration_OnPrem_Cloud.md
|   |   
|   \---images
+---networking
|   |   3Tier_AWS_Architecture.md
|   |   3Tier_GCP_Architecture.md
|   |   
|   \---images
|           3_tier_aws.jpeg
|           arch-todo.svg
|           
\---security
    |   Defense_in_depth.md
    |   Least_Privilege_Access.md
    |   
    \---images
```