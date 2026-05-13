# Extended Dependencies & Frameworks

This file contains all extended repositories and frameworks for Project-PI, organized by functional category. These are critical components for predictive simulation, agentic AI, and decision systems.

## Repository Categories

### Core
- **@karpathy/autoresearch** - https://github.com/karpathy/autoresearch

### Infrastructure & Containers
- **fluxcd/source-controller** - https://github.com/fluxcd/source-controller
  - Container: https://github.com/fluxcd/source-controller/pkgs/container/source-controller
- **external-secrets/external-secrets** - https://github.com/external-secrets/external-secrets
  - Container: https://github.com/external-secrets/external-secrets/pkgs/container/external-secrets

### Agent-Based Modeling & Simulation
- **Mesa** - https://github.com/mesa/mesa
  - Agent-based modeling framework for simulating complex systems
- **SimPy (via AdamBuruzs/simpy_ejector)** - https://github.com/AdamBuruzs/simpy_ejector
  - Discrete event simulation library

### Predictive Simulation (MiroFish + AlphaGo style)
- **KataGo** - https://github.com/lightvector/KataGo
  - Open AlphaGo-style MCTS engine, adaptable for various domains

### Reinforcement Learning at Scale
- **Ray & Ray RLlib** - https://github.com/ray-project/ray
  - Distributed reinforcement learning framework

### Market & Sector Analysis
- **FinGPT (Alpaca + FinGPT)** - https://github.com/AI4Finance-Foundation/FinGPT
  - LLM for market/sector trend analysis and financial insights

### News & Data Feeds
- **GDELT Doc API** - https://github.com/alex9smith/gdelt-doc-api
  - NewsAPI + GDELT for live disruptor/news feeds integration

### Recommendations Engine
- **Evidently AI** - https://github.com/evidentlyai/evidently
  - Decision impact analysis + drift detection
- **CausalML (Uber)** - https://github.com/uber/causalml
  - Causal inference framework for decisions
- **What-If Tool (Google)** - https://github.com/PAIR-code/what-if-tool
  - Counterfactual simulation and impact analysis

### Agentic AI & Business Workflows
- **Microsoft AutoGen** - https://github.com/microsoft/autogen
  - Multi-agent conversation frameworks and business workflows
- **CrewAI** - https://github.com/crewAIInc/crewAI
  - Role-based agentic teams with specialized agents
- **LangGraph (LangChain)** - https://github.com/langchain-ai/langgraph
  - Stateful agent orchestration and workflows
- **OpenAI Swarm** - https://github.com/openai/swarm
  - Lightweight agent handoffs and coordination

### Mind Map / Impact Visualization
- **D3.js** - https://github.com/d3/d3
  - Force graph visualization and interactive diagrams
- **Cytoscape.js** - https://github.com/cytoscape/cytoscape.js
  - Network and impact maps visualization
- **React Flow (xyflow)** - https://github.com/xyflow/xyflow
  - Node-based UI for decision trees and workflow visualization

## How to Use

### Load All Extended Dependencies (JavaScript/Node.js)

```javascript
const fs = require('fs');
const path = require('path');

// Load extended dependencies
const extendedDeps = JSON.parse(
  fs.readFileSync(path.join(__dirname, 'extended-dependencies.json'), 'utf8')
);

// Get all repositories in a specific category
function getByCategory(category) {
  return extendedDeps.repositories.filter(r => r.category === category);
}

// Example: Get all agentic AI frameworks
const agenticFrameworks = getByCategory('agentic-ai');
console.log(agenticFrameworks);

// Get a specific repository
const autoGen = extendedDeps.repositories.find(r => r.name === 'microsoft/autogen');
console.log(autoGen.url); // https://github.com/microsoft/autogen
```

### Load All Extended Dependencies (Python)

```python
import json
import os

# Load extended dependencies
with open(os.path.join(os.path.dirname(__file__), 'extended-dependencies.json'), 'r') as f:
    extended_deps = json.load(f)

# Get all repositories in a specific category
def get_by_category(category):
    return [r for r in extended_deps['repositories'] if r.get('category') == category]

# Example: Get all visualization frameworks
viz_frameworks = get_by_category('visualization')
for framework in viz_frameworks:
    print(f"{framework['name']}: {framework['url']}")

# Get a specific framework
autogen = next(r for r in extended_deps['repositories'] if r['name'] == 'microsoft/autogen')
print(autogen['description'])
```

### Filter by Category

```javascript
// Available categories:
const categories = [
  'core',
  'infrastructure',
  'agent-based-modeling',
  'simulation',
  'predictive-simulation',
  'reinforcement-learning',
  'market-analysis',
  'news-feeds',
  'recommendations-engine',
  'agentic-ai',
  'visualization'
];

categories.forEach(cat => {
  console.log(`${cat}:`, getByCategory(cat));
});
```

## Integration Strategy

### 1. **Agent Orchestration Stack**
- Use **LangGraph** or **AutoGen** for workflow coordination
- Deploy with **CrewAI** for role-based teams
- Coordinate with **OpenAI Swarm** for lightweight handoffs

### 2. **Predictive Simulation Pipeline**
- Initialize with **Mesa** for agent-based modeling
- Use **SimPy** for discrete event simulation
- Apply **KataGo** MCTS for decision prediction
- Augment with **Ray RLlib** for reinforcement learning optimization

### 3. **Decision Impact System**
- Use **Evidently AI** for monitoring decision quality
- Apply **CausalML** for causal analysis
- Visualize with **What-If Tool** for counterfactuals

### 4. **Real-Time Data & Analysis**
- Fetch market data with **FinGPT**
- Ingest news/disruptors with **GDELT API**
- Display in **D3.js** force graphs

### 5. **Visualization & UI**
- Build dashboards with **React Flow** (xyflow)
- Create network maps with **Cytoscape.js**
- Render interactive charts with **D3.js**

## File Structure

```
dependencies/
├── repositories.json              # Original 4 core repos
├── extended-dependencies.json     # All 19 new repos & frameworks
├── README.md                      # Original setup guide
└── EXTENDED-README.md            # This comprehensive guide
```

## Next Steps for Claude Code Integration

When Claude accesses these files, it should:

1. Parse both JSON files into dependency maps
2. Filter by category based on use case
3. Generate import/installation commands
4. Create integration templates for multi-framework workflows
5. Build orchestration patterns for agentic systems

---

**Last Updated:** 2026-05-13
**Total Repositories:** 19
**Categories:** 11
