# AI Observability Platform
> Building an observable, quantifiable and actionable risks and controls in multi-agent systems


## Problem Statement
* No systematic approach to understanding cost, performance and effectiveness of controls
* Existing evaluations are only scoped to individual agents
* Performance and cost impact of controls requires effort to measure

## Negative Impacts
* Unjustified investments in control products
* Control requirements may be overstated or understated
* Increased effort in performing basic analysis or research


## Context Digram
![Observatory](./images/Observatory.png)

## Sequence Diagram

```mermaid
sequenceDiagram
    autonumber
    actor User as User
    participant FE as Frontend App (ReactJS)
    participant API as Platform API (FastAPI)
    participant EQ as Environment Queue
    participant XQ as Experiment Queue
    participant EO as Environments Orchestrator
    participant XO as Experiments Orchestrator
    participant PDB as Platform DB (Postgres)
    participant K8S as K8s API
    participant SR as Scenario Runner (K8s Job)
    participant PL as Planner Agent
    participant RA as Research Agent
    participant WA as Writer Agent
    participant CS as Control Services
    participant PR as Presidio Adapter
    participant NG as NemoGuardrail Adapter
    participant LF as LlamaFirewall Adapter
    participant TR as Tools and Resources
    participant TI as Telemetry Ingestion
    participant RE as Risk Engine
    participant GE as Goals Engine
    participant RS as Reporting Service
    participant TDB as TraceLog DB
    participant MDB as Metrics DB
    participant ART as Artifacts / Reports

    %% ===== Environment & Experiment Setup =====
    User->>FE: Define Environment / Experiment / Controls / Goals
    FE->>API: Submit request
    API->>PDB: Persist definition
    API->>EQ: Enqueue Environment Creation Job
    API->>XQ: Enqueue Experiment Creation Job

    EQ->>EO: Consume Environment job
    EO->>K8S: Create/Inspect/Delete Environment Resources
    K8S-->>EO: Desired state materialized
    EO->>PDB: Update environment status

    XQ->>XO: Consume Experiment job
    XO->>K8S: Create/Inspect/Delete Experiment Resources
    K8S->>PDB: Sync state
    XO->>PDB: Update experiment status

    K8S-->>API: Environment and Execution Lifecycle Events

    %% ===== Scenario Execution =====
    API->>SR: Trigger Scenario Execution (EKS Namespace)
    SR->>PL: Trigger Planner Agent

    PL->>RA: Delegate research task
    PL->>WA: Delegate writing task

    %% ===== Controlled Tool Call Flow =====
    RA->>CS: POST /process (tool call request)
    CS->>PR: Screen for PII
    PR-->>CS: PII scan result
    CS->>NG: Validate against guardrail policy
    NG-->>CS: Policy decision
    CS->>LF: Firewall / threat check
    LF-->>CS: Firewall verdict
    CS-->>RA: Approved/blocked response

    RA->>TR: Tool Call
    TR-->>RA: Tool result

    WA->>CS: POST /process (tool call request)
    CS-->>WA: Approved/blocked response
    WA->>TR: Tool Call
    TR-->>WA: Tool result

    RA-->>PL: Research result
    WA-->>PL: Writer result

    %% ===== Telemetry & Evidence Collection =====
    SR->>TI: Scenario Execution Events (actions and results)
    PL->>TI: Agent traces / interactions
    TI->>TDB: Store raw telemetry/traces

    TI->>RE: Forward telemetry for risk scoring
    TI->>GE: Forward telemetry for goal evaluation
    RE->>GE: Correlate risk vs goal outcomes
    RE->>MDB: Persist risk metrics
    GE->>MDB: Persist goal/outcome metrics

    RE->>RS: Risk findings
    GE->>RS: Goal evaluation results
    RS->>ART: Publish Artifacts / Reports

    TI-->>API: Control decisions, latency feedback
    API-->>FE: Environment/Experiment status update
    FE-->>User: Display results, metrics, reports
```
