# Scenario 1 – Modernising a legacy Big Data Platform

## Context

* A mid-to-large enterprise has operated a traditional big data stack for 8–10 years. The current estate includes:
    * On-premise Hadoop (HDFS, Hive, Spark, some legacy MapReduce jobs).
    * A separate enterprise data warehouse running mission-critical reporting.
    * A patchwork of ETL tools feeding both the lake and the warehouse.
    * Approximately 200 internal users across analytics, finance, operations and risk.
    * Around 2 PB of data under management, growing at roughly 30% year-on-year.

## Pain points

* Rising hardware refresh and software licensing costs.
* Slow batch cycles; SLAs are increasingly missed.
* No meaningful real-time or streaming capability.
* Schema rigidity making it hard to onboard new data sources.
* A growing backlog of ML and AI use cases the current platform cannot serve.
* Specialist skills (e.g. MapReduce, legacy Hive tuning) are increasingly hard to hire.

## The Ask
> Propose a migration strategy and target-state architecture to move this organisation onto a next-generation data lake or lake house platform. Your response should cover:

* Target architecture — cloud vs hybrid, storage layer, open table format choice, compute engines, and the rationale for each.
* Treatment of the warehouse — consolidate into the Lakehouse, keep separate, or federate? 
* Migration approach — phasing, what moves first, parallel running, cutover, decommissioning.
* Data and workload mapping — how you would categorise existing workloads and decide their migration path.
* Risk and mitigation — data gravity, downtime tolerance, skills gap, cost overrun, business continuity.
* People and operating model — team structure, upskilling, ways of working during and after migration.
* Success metrics — what KPIs would prove the programme delivered value?

## Constraints to Assume
* Budget envelope is finite — assume executive scrutiny on TCO.
* The business cannot tolerate more than 4 hours of unplanned downtime on critical reporting.
* Regulatory data must remain auditable throughout the transition. Data must remain on-prem within the region.

# Scenario 2 – Greenfield, Next Generation Data Lake System

## Context
> A growing organisation is building its data platform from scratch and wants a modular, customisable lake architecture that can flex as the business evolves. Expected characteristics:
•	Diverse sources: transactional databases, SaaS APIs, IoT and event streams, third-party file feeds.
•	Multiple consumer personas: analysts, data scientists, business applications, external partners.
•	Strict regulatory obligations across multiple jurisdictions (assume GDPR-equivalent at minimum).
•	Expectation of rapid growth: 10x data volume and 5x user base within 3 years.
•	Strong preference for open standards and avoidance of deep vendor lock-in where reasonable.

## Pain points
•	A growing backlog of AI use cases that need the same data.
•	Security is a must but must be flexible to apply based on its use cases.
•	Performance is key for good user experiences.
•	Data is the crown jewel of the organization. E.g. How do you ensure data resiliency against ransomware, corruption, etc
•	Price is limited. Open source is encouraged however support must still meet SLA.

## The ask
> Propose an end-to-end reference architecture covering the full data lifecycle. Your response should address each of the following capability areas:
1. Ingestion
•	Batch, streaming and CDC patterns.
•	Schema evolution and source variety.
•	Late-arriving and out-of-order data.
2. Storage and zoning
•	Zone design (raw / curated / consumption, or equivalent).
•	File and table format choices.
•	Partitioning, clustering and compaction strategy.
3. Transformation and processing
•	Engine choices and when to use which.
•	Orchestration and dependency management.
•	Support for SQL-first and code-first practitioners.
•	Testing, CI/CD and data contracts.
4. Analytics and consumption
•	BI, ad-hoc analytics, ML and feature stores.
•	Data sharing with internal and external consumers.
•	Semantic layer and self-service strategy.
5. Identity and access
•	Authentication and federation.
•	Fine-grained authorisation — row, column, and tag-based controls.
•	Service identities vs human identities.
6. Governance
•	Catalog, lineage and discovery.
•	Data quality framework.
•	Classification, stewardship and ownership model.
•	Policy as code, where applicable.
7. Security
•	Encryption at rest and in transit, key management.
•	Network isolation and perimeter design.
•	PII handling, tokenisation, masking.
•	Audit, monitoring and incident response.

Cross-cutting questions to address
•	Customisability — where have you deliberately designed for swappable components, and what have you locked in?
•	Cost control — how do costs behave from year one to year five?
•	Scalability — what breaks first as you 10x the data?
•	Operating model — who owns what, and how do teams interact with the platform?

Be prepared for follow-up scenarios
During Q&A we may pose curveballs such as:
•	"Budget is halved — what stays, what goes?"
•	"A regulator mandates data residency in a new jurisdiction — how does your design respond?"
•	"An acquisition doubles the data volume in six months — what changes?"
•	"A critical vendor sunsets a key product — how exposed are you?"
