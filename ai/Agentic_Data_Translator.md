# Agentic Data Translator

## Problem Statement
* 2500+ business users and data analyst depend on specialist-served analytics
* 1.7m ad-hoc SQL queries / year across the organization
* Enterprise analytics today requires SQL / data specialist support, creating 2+ day delays before users can access actionable insights

## Business Opportunity
* Shift analysts time from query chasing to decision-making
* Enable data analyst to directly explore data, interpret results, and answer business questions without needing to understand backend schemas, tables or SQL logic


## Solution
* Agentic Text2SQL for governed self-served analytics
* NL chat interface that generate schema-aware SQL, retrieves data faster, reduces inconsistent query logic, and creates the foundation for conversational analytics across business units

1. A multi-agent data assistant to solve
    * High cost of analytics: Too much time spent translating business into SQL
    * High complexity: Even a small number of tables can be extremely complex (e.g 800 columns)
    * Discoverability gap 

2. Data Products
	- NLQ --> SQL generation for Data Products
	- Executes SQL on Databricks and returns results
	- Data Products are pre-aggregated and simpler --> improves reliability and adoption

3. Core/GCO Tables
	- Used to understand what exists in Core/GCO
	- Helps identify "What's available today vs What's in Data Products"
	- Support data discovery and roadmap alignment

4. Answers questions like 
	- Do we have X attributes/metric in Data Products today? If not, is it available in Core/GCO? Which table/field?