# Project-PI Framework & Dependencies Guide

This document outlines all frameworks, repositories, and integrations for the Project-PI system.

## Core Architecture

### 1. **Agentic AI Business Structure**
Orchestrating multi-agent workflows for autonomous decision-making and business operations.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **AutoGen** | [microsoft/autogen](https://github.com/microsoft/autogen) | Multi-agent business workflows with collaborative agents |
| **CrewAI** | [crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) | Role-based agentic teams with specialized functions |
| **LangGraph** | [langchain-ai/langgraph](https://github.com/langchain-ai/langgraph) | Stateful agent orchestration and workflow control |
| **OpenAI Swarm** | [openai/swarm](https://github.com/openai/swarm) | Lightweight agent handoff mechanisms |

### 2. **Predictive Simulation & Modeling**
Building sophisticated simulation engines for market and behavioral prediction.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **Mesa** | [mesa/mesa](https://github.com/mesa/mesa) | Agent-based modeling framework for complex systems |
| **SimPy** | [AdamBuruzs/simpy_ejector](https://github.com/AdamBuruzs/simpy_ejector) | Discrete event simulation engine |
| **KataGo** | [lightvector/KataGo](https://github.com/lightvector/KataGo) | Open AlphaGo-style MCTS engine for strategic decisions |
| **Ray RLlib** | [ray-project/ray](https://github.com/ray-project/ray) | Reinforcement learning at massive scale |

### 3. **Market & Trend Analysis**
Real-time market intelligence and disruptor detection.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **FinGPT** | [AI4Finance-Foundation/FinGPT](https://github.com/AI4Finance-Foundation/FinGPT) | Market and sector trend analysis with Alpaca |
| **GDELT Document API** | [alex9smith/gdelt-doc-api](https://github.com/alex9smith/gdelt-doc-api) | Live disruptor and news feed integration |

### 4. **Recommendations & Decision Engine**
Intelligent recommendations with causal inference and impact analysis.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **Evidently AI** | [evidentlyai/evidently](https://github.com/evidentlyai/evidently) | Decision impact tracking and drift detection |
| **CausalML** | [uber/causalml](https://github.com/uber/causalml) | Causal inference for business decisions |
| **What-If Tool** | [PAIR-code/what-if-tool](https://github.com/PAIR-code/what-if-tool) | Counterfactual simulation and scenario analysis |

### 5. **Visualization & UI**
Interactive visualization of decision trees, impact maps, and system dynamics.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **D3.js** | [d3/d3](https://github.com/d3/d3) | Force-directed graphs for mind maps |
| **Cytoscape.js** | [cytoscape/cytoscape.js](https://github.com/cytoscape/cytoscape.js) | Network and impact map visualization |
| **React Flow** | [xyflow/xyflow](https://github.com/xyflow/xyflow) | Node-based UI for decision tree rendering |

### 6. **UI/UX & Design Systems**
Design foundations and component libraries.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **gstack** | [garrytan/gstack](https://github.com/garrytan/gstack) | Advanced UI/UX stack |
| **ui-ux-pro-max-skill** | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | Professional UI/UX patterns |
| **impeccable** | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | Design system framework |
| **huashu-design** | [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) | Design language and components |

### 7. **DevOps & Infrastructure**
Container management and secret orchestration.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **Flux CD Source Controller** | [fluxcd/source-controller](https://github.com/fluxcd/source-controller) | GitOps source management ([Container Registry](https://github.com/fluxcd/source-controller/pkgs/container/source-controller)) |
| **External Secrets** | [external-secrets/external-secrets](https://github.com/external-secrets/external-secrets) | Secret management integration ([Container Registry](https://github.com/external-secrets/external-secrets/pkgs/container/external-secrets)) |

### 8. **Research & AutoML**
Automated research and optimization frameworks.

| Framework | Repository | Purpose |
|-----------|-----------|---------|
| **autoresearch** | [karpathy/autoresearch](https://github.com/karpathy/autoresearch) | Autonomous research framework by Andrej Karpathy |

---

## System Integration Map

```
┌─────────────────────────────────────────────────────────────┐
│                    PROJECT-PI ARCHITECTURE                   │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│  ┌──────────────────────────────────────────────────────┐  │
│  │           AGENTIC AI ORCHESTRATION LAYER            │  │
│  │  (AutoGen → CrewAI → LangGraph → OpenAI Swarm)     │  │
│  └──────────────────────────────────────────────────────┘  │
│                          ↓                                    │
│  ┌──────────────────────────────────────────────────────┐  │
│  │         SIMULATION & PREDICTION ENGINE              │  │
│  │  (Mesa, SimPy, KataGo, Ray RLlib)                  │  │
│  └──────────────────────────────────────────────────────┘  │
│                          ↓                                    │
│  ┌──────────────────────────────────────────────────────┐  │
│  │        DATA SOURCES & MARKET INTELLIGENCE           │  │
│  │  (FinGPT, GDELT, NewsAPI, Real-time Feeds)        │  │
│  └──────────────────────────────────────────────────────┘  │
│                          ↓                                    │
│  ┌──────────────────────────────────────────────────────┐  │
│  │      RECOMMENDATIONS & DECISION ENGINE              │  │
│  │  (Evidently AI, CausalML, What-If Tool)            │  │
│  └──────────────────────────────────────────────────────┘  │
│                          ↓                                    │
│  ┌──────────────────────────────────────────────────────┐  │
│  │    VISUALIZATION & USER INTERFACE LAYER             │  │
│  │  (D3.js, Cytoscape.js, React Flow + UI Systems)   │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

---

## Quick Start Integration

### Loading Dependencies in Code

**JavaScript/Node.js:**
```javascript
const repositories = require('./repositories.json');

// Find a specific framework
const autogen = repositories.repositories.find(r => r.name === 'AutoGen');
console.log(`Using ${autogen.name}: ${autogen.url}`);
```

**Python:**
```python
import json

with open('repositories.json') as f:
    repos = json.load(f)

# Filter by category
agentic_ai = [r for r in repos['repositories'] if r.get('category') == 'Agentic AI']
for framework in agentic_ai:
    print(f"{framework['name']}: {framework['url']}")
```

---

## Categories

- **Agentic AI**: Multi-agent orchestration and workflow frameworks
- **Simulation**: Agent-based modeling and event simulation
- **Reinforcement Learning**: RL at scale with Ray RLlib
- **Market Analysis**: Financial and trend analysis
- **Data Sources**: Real-time news and market disruptors
- **Recommendations Engine**: Causal inference and impact detection
- **Visualization**: Interactive graphs and decision trees
- **UI/UX**: Design systems and component libraries
- **DevOps/Container**: Infrastructure and secret management
- **Core Research**: Research automation frameworks

---

## Integration Priorities

1. **Phase 1**: Agentic AI orchestration (AutoGen/CrewAI/LangGraph)
2. **Phase 2**: Simulation engines (Mesa/SimPy/KataGo)
3. **Phase 3**: Market data integration (FinGPT/GDELT)
4. **Phase 4**: Decision recommendations (CausalML/Evidently)
5. **Phase 5**: Visualization layer (D3.js/Cytoscape/React Flow)
6. **Phase 6**: DevOps & deployment (Flux CD/External Secrets)

