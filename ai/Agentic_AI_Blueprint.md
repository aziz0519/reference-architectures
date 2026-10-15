# Building a Production Grade Agentic AI Blueprint (BFSI)
> Enabling a Agentic Banking application from demo to production at scale

1. [Context](#context)
2. [Problem Statement](#problem-statement)
3. [Agentic AI Blueprint](#full-scale-agentic-ai-blueprint)
4. [Step 1: Demo and Proof-of-Concept](#step-1-demo-and-proof-of-concept)
5. [Step 2: Enabling Agent access to the Bank's API ](#step-2-enabling-the-agent-access-to-the-banks-internal-data-through-apis)
6. [Step 3: Introduce Domain-specific Agents](#step-3-create-domain-specific-sub-agents-and-assign-only-those-tools-it-needs-access-to)
7. [Step 4: An Agent Supervisor or Orchestrator](#step-4-who-decides-which-agent-answers)
8. [Step 5: Expose Tool via MCP Servers](#step-5-expose-tools-via-mcp-servers-to-create-a-loosely-coupled-design)
9. [Step 6: Adding Authentication and short-lived credentials](#step-6-authentication)
10. [Step 7: Adding Authorization](#step-7-authorization)
11. [Step 8: Hybrid LLMs setup for different tasks](#step-8-split-llm-into-self-hosted-and-open-weight)
12. [Step 9: Memory and State Management](#step-9-memory-and-state-management)
13. [Step 10: Addressing data residency requirements](#step-10-pii-never-leaves-the-bank)
14. [Step 11: Agent Evaluation Suite](#step-11-agent-evaluation-suite)
15. [Step 12: Monitoring and Observability](#step-12-agentops-and-llmops-monitoring--observability)
16. [Step 13: Adding a Cost Tracker](#step-13-finops-cost-management)
17. [Step 14: Edge Layer Security](#step-14-defense-in-depth-edge-layer-security)

## Context
A bank's customer service lead has reported that 300,000 calls were made last month

75% of them asked three questions:
* What's is my balance?
* What was this debit from my account?
* Send me cheque book

## Problem Statement
* Average call handling time, four minutes
* Every year bank pays millions of dollars to the network provider

But the bank's mobile and web app already has all of this. Why are they still calling?

Because the app has multiple screens and some of the customers don't know how to navigate these screens to find out what they need. So they will find it easier to ask their questions to a customer support person over a call. 


## Business Opportunity and Solution
* Having an AI-native application that can securely perform banking transactions to automate simple queries such as checking of bank balance and updating of particulars
* Evolution of agentic payments where bank transfers can be made almost autonomous with high-value transactions requiring human-in-the-loop approvals
* Enabling banking workforce to focus on providing value on other areas such as customer relationship management and building trust with high net worth clients  

## Full Scale Agentic AI Blueprint

![AgenticAI](./images/AgenticAI_Blueprint.png)

#### Step 1: Demo and Proof-of-Concept

```mermaid
flowchart LR
    subgraph Services
        b
        c
    end 

    a["User Interface"] --> b["API"] --> c["Agent"] --> d["LLM"]

```

#### Step 2: Enabling the agent access to the bank's internal data through APIs

```mermaid
---
look: classic
layout: dagre
---
flowchart LR
    subgraph Bank's Internal API
        e
        f
        g
        h
    end 

    a["User Interface"] 
    b["API"]  
    c["Agent"] 
    d("LLM")
    e["Balance Enquiry"]
    f["Transaction Details"]
    g["Statement Request"]
    h["KYC Update"]

    a --> b
    b --> c
    c --> d
    c --> e
    c --> f
    c --> g
    c --> h

```

#### Step 3: Create domain specific sub agents and assign only those tools it needs access to 

```mermaid
flowchart LR
    subgraph Accounts Agent
        e
    end
    subgraph Transaction Agent
        f
        g
    end
    subgraph Service Agent
        h
    end 

    a["User Interface"] 
    b["API"]  
    c["Agent"] 
    d("LLM")
    e["Balance Enquiry"]
    f["Transaction Details"]
    g["Statement Request"]
    h["KYC Update"]

    a --> b
    b --> c
    c --> d
    c --> e
    c --> f
    c --> g
    c --> h

```
* Accounts Agent - Check the balance of a customer CASA (Current or Savings Account)
* Transactions Agent - Check the latest transactions of a customer e.g Date of Salary Credited
* Service Agent - Update a customers's particulars e.g. change of address or contact number

#### Step 4: Who decides which agent answers?
```mermaid
flowchart LR
    subgraph Acccounts Tool
        e
    end
    subgraph Transaction Tool
        f
        g
    end
    subgraph Service Tool
        h
    end
    subgraph Agents
        c
        j
        k
        l
    end

    a["User Interface"] 
    b["API"]  
    c{"Supervisor Agent"} 
    d("LLM")
    e["Balance Enquiry"]
    f["Transaction Details"]
    g["Statement Request"]
    h["KYC Update"]
    j["Accounts Agent"]
    k["Transactions Agent"]
    l["Service Agent"]

    a --> b
    b --> c
    c --> d
    c --> j
    c --> k
    c --> l 
    j --> e 
    k --> f
    k --> g
    l --> h 

```


#### Step 5: Expose tools via MCP servers to create a loosely coupled design

```mermaid
flowchart LR
    subgraph Acccounts Tool
        e
    end
    subgraph Transaction Tool
        f
        g
    end
    subgraph Service Tool
        h
    end
    subgraph Agents
        c
        j
        k
        l
    end

    a["User Interface"] 
    b["API"]  
    c{"Supervisor Agent"} 
    d("LLM")
    e["Balance Enquiry"]
    f["Transaction Details"]
    g["Statement Request"]
    h["KYC Update"]
    j["Accounts Agent"]
    k["Transactions Agent"]
    l["Service Agent"]
    m("Accounts MCP Server")
    n("Transactions MCP Server")
    p("Service MCP Server")

    a --> b
    b --> c
    c --> d
    c --> j
    c --> k
    c --> l 
    j --> m
    k --> n
    l --> p
    m --> e
    n --> f
    n --> g
    p --> h

```
* MCPs decouple agents from tools by routing capabilities through dedicated modular servers


#### Step 6: Authentication
```mermaid
flowchart LR
    subgraph Acccounts Tool
        e
    end
    subgraph Transaction Tool
        f
        g
    end
    subgraph Service Tool
        h
    end
    subgraph Agents
        c
        j
        k
        l
    end

    a["User Interface"] 
    b["API"]  
    c{"Supervisor Agent"} 
    d("LLM")
    e["Balance Enquiry"]
    f["Transaction Details"]
    g["Statement Request"]
    h["KYC Update"]
    j["Accounts Agent"]
    k["Transactions Agent"]
    l["Service Agent"]
    m("Accounts MCP Server")
    n("Transactions MCP Server")
    p("Service MCP Server")
    q["Authentication"]

    a --> b
    b --> c
    c --> d
    c --> j
    c --> k
    c --> l 
    j --> m
    k --> n
    l --> p
    m --> e
    n --> f
    n --> g
    p --> h
    a -.SAML.-> q

```


#### Step 7: Authorization

```mermaid
flowchart LR
    subgraph Acccounts Tool
        e
    end
    subgraph Transaction Tool
        f
        g
    end
    subgraph Service Tool
        h
    end
    subgraph Agents
        c
        j
        k
        l
    end

    a["User Interface"] 
    b["API"]  
    c{"Supervisor Agent"} 
    d("LLM")
    e["Balance Enquiry"]
    f["Transaction Details"]
    g["Statement Request"]
    h["KYC Update"]
    j["Accounts Agent"]
    k["Transactions Agent"]
    l["Service Agent"]
    m("Accounts MCP Server")
    n("Transactions MCP Server")
    p("Service MCP Server")
    q["Authentication"]
    r["Authorization </br> RBAC </br> ABAC"]

    a --> b
    b --> c
    c --> d
    c --> j
    c --> k
    c --> l 
    j --> m
    k --> n
    l --> p
    m --> e
    n --> f
    n --> g
    p --> h
    a -.SAML.-> q
    r --> c

```

#### Step 8: Split LLM into Self-Hosted and Open Weight
```mermaid
flowchart LR
    subgraph LLM
    a
    b
    end

    a["Self-hosted"]
    b["Open-Weight models"]

```
#### Step 9: Memory and State Management
```mermaid
flowchart LR
    A[("Session Store")]
```

```mermaid
flowchart TD
    subgraph Session Store
    A
    B
    C
    D
    end
    A["Working Memory / Context RAM"]
    B["Procedural Memory"]
    C["Epsiodic Memory"]
    D["Semantic Memory"]

    B -.skillmd.-> A
    C -.RAG (topic search).-> A
    D -.RAG for relevance.-> A
```
##### Types of Memory
* Working Memory: Current session memory
* Episodic Memory: Dated events and past chat history
* Semantic Memory: Durable facts and user profile
* Procedural Memory: Instructions and Skills

#### Step 10: PII Never Leaves the Bank
```mermaid
flowchart LR
    A["PII Redaction"]
```
#### Step 11: Agent Evaluation Suite
```mermaid
flowchart LR
    A["Agent Eval Suite </br> RAGAS </br> DeepEval </br> LLM-as-a-Judge"]
```

#### Step 12: AgentOps and LLMOps (Monitoring & Observability)
```mermaid
flowchart LR
    subgraph Observability
    A
    B
    C
    end

    A["Prompts </br> Agent Calls </br> Tool Calls"]
    B["CPU </br> Memory </br> Disk Utilization"]
    C["p95/p99 Latency"]
```
#### Step 13: FinOps (Cost Management)
```mermaid
flowchart LR
    A["Cost Management </br> Cost per request </br> Cost per Agent Call </br> Cost per Tool Call"]
```
#### Step 14: Defense in Depth (Edge Layer Security)
```mermaid
flowchart LR
    A["Edge Layer Security </br> Web Application Firewall </br> DDoS </br> Rate Limits </br> API Gateway"]
```