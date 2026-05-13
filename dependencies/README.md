# Dependencies Folder

This folder contains metadata and references to all external repositories, frameworks, and libraries that your Project-PI codebase integrates with or depends on.

## 📋 What's Included

This dependencies folder manages 23 frameworks organized into 9 categories:

### **Agentic AI** (4 frameworks)
- AutoGen, CrewAI, LangGraph, OpenAI Swarm
- Multi-agent orchestration and business workflows

### **Simulation & Modeling** (4 frameworks)
- Mesa, SimPy, KataGo, Ray RLlib
- Agent-based modeling, discrete event simulation, MCTS, and RL at scale

### **Market Analysis & Data** (2 frameworks)
- FinGPT, GDELT Document API
- Real-time trend analysis and disruptor detection

### **Recommendations Engine** (3 frameworks)
- Evidently AI, CausalML, What-If Tool
- Decision impact, causal inference, and counterfactual analysis

### **Visualization** (3 frameworks)
- D3.js, Cytoscape.js, React Flow
- Force graphs, network maps, and decision tree UIs

### **UI/UX Design Systems** (4 frameworks)
- gstack, ui-ux-pro-max-skill, impeccable, huashu-design
- Professional design patterns and component libraries

### **DevOps & Container Management** (2 frameworks)
- Flux CD Source Controller, External Secrets
- GitOps and secret management with container registries

### **Research & AutoML** (1 framework)
- autoresearch (Karpathy)
- Autonomous research optimization

---

## 🚀 Quick Start

### Loading Dependencies in JavaScript/Node.js

```javascript
const fs = require('fs');
const path = require('path');

// Load all repositories
const repositories = JSON.parse(
  fs.readFileSync(path.join(__dirname, 'repositories.json'), 'utf8')
);

// Access a specific framework
const autogen = repositories.find(r => r.name === 'AutoGen');
console.log(`Framework: ${autogen.name}`);
console.log(`URL: ${autogen.url}`);
console.log(`Category: ${autogen.category}`);

// Filter by category
const agentic = repositories.filter(r => r.category === 'Agentic AI');
agentic.forEach(framework => {
  console.log(`- ${framework.name}: ${framework.url}`);
});
```

### Loading Dependencies in Python

```python
import json
import os

# Load all repositories
with open(os.path.join(os.path.dirname(__file__), 'repositories.json'), 'r') as f:
    repositories = json.load(f)

# Access a specific framework
mesa = next(r for r in repositories if r['name'] == 'Mesa')
print(f"Framework: {mesa['name']}")
print(f"URL: {mesa['url']}")
print(f"Category: {mesa['category']}")

# Filter by category
simulation_frameworks = [r for r in repositories if r['category'] == 'Simulation & Modeling']
print("Simulation Frameworks:")
for framework in simulation_frameworks:
    print(f"  - {framework['name']}: {framework['url']}")
```

### Accessing with Claude

When coding with Claude, reference this directory to:
- Retrieve framework URLs and GitHub repository links
- Access repository IDs and owner information
- Filter by category for specific use cases
- Maintain a centralized, version-controlled dependency manifest

---

## 📁 Files Structure

```
dependencies/
├── repositories.json     # Metadata for all 23 frameworks
├── FRAMEWORK_GUIDE.md    # Comprehensive architecture & integration guide
└── README.md            # This file
```

### `repositories.json` Schema

Each entry contains:
```json
{
  "name": "Framework Name",
  "owner": "github_username",
  "repo": "repository_name",
  "url": "https://github.com/owner/repo",
  "category": "Category Name",
  "containerRegistry": "Optional container registry URL (DevOps only)"
}
```

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│          PROJECT-PI FRAMEWORK LAYERS                │
├─────────────────────────────────────────────────────┤
│                                                      │
│  Layer 1: Agentic AI Orchestration                 │
│  (AutoGen → CrewAI → LangGraph → OpenAI Swarm)    │
│                                                      │
│  Layer 2: Simulation & Prediction                  │
│  (Mesa, SimPy, KataGo, Ray RLlib)                 │
│                                                      │
│  Layer 3: Data & Market Intelligence               │
│  (FinGPT, GDELT, NewsAPI, Real-time feeds)        │
│                                                      │
│  Layer 4: Recommendations & Decisions              │
│  (Evidently, CausalML, What-If Tool)              │
│                                                      │
│  Layer 5: Visualization & UI                       │
│  (D3.js, Cytoscape.js, React Flow)                │
│                                                      │
│  Layer 6: Infrastructure & DevOps                  │
│  (Flux CD, External Secrets, Container Mgmt)      │
│                                                      │
└─────────────────────────────────────────────────────┘
```

---

## 📖 Using the Framework Guide

For detailed information about each framework, its purpose, and integration strategies, see **`FRAMEWORK_GUIDE.md`**:

- **8 Framework Categories** with full breakdowns
- **System Integration Map** showing data flow
- **Code Examples** for each layer
- **6-Phase Implementation Strategy**
- **Quick-start Integration** examples

---

## 🔗 Key Resources

- **Repositories Configuration**: See `repositories.json`
- **Integration Architecture**: See `FRAMEWORK_GUIDE.md`
- **Container Registries**: 
  - Flux CD: https://github.com/fluxcd/source-controller/pkgs/container/source-controller
  - External Secrets: https://github.com/external-secrets/external-secrets/pkgs/container/external-secrets

---

## 💡 Use Cases

### For Development
```javascript
// Quickly reference any framework
const framework = repositories.find(r => r.repo === 'autogen');
```

### For Documentation
```python
# Generate dependency documentation
for repo in repositories:
    print(f"## {repo['name']}\n- URL: {repo['url']}\n- Category: {repo['category']}\n")
```

### For Claude AI Coding
All frameworks are pre-indexed and categorized for Claude to reference during code development, ensuring consistency and best practices across your Project-PI codebase.

---

## 📝 Adding New Frameworks

To add a new framework to the dependencies:

1. Add entry to `repositories.json` following the schema
2. Update relevant sections in `FRAMEWORK_GUIDE.md`
3. Include category classification
4. Add container registry URL if applicable (DevOps frameworks)

Example:
```json
{
  "name": "New Framework",
  "owner": "github_owner",
  "repo": "repository_name",
  "url": "https://github.com/owner/repo",
  "category": "Category Name"
}
```

---

## ✨ Categories at a Glance

| Category | Count | Purpose |
|----------|-------|---------|
| Agentic AI | 4 | Multi-agent orchestration |
| Simulation | 4 | Modeling & predictions |
| Market Analysis | 2 | Trend & disruptor detection |
| Recommendations | 3 | Decision intelligence |
| Visualization | 3 | Interactive UI rendering |
| UI/UX | 4 | Design systems |
| DevOps | 2 | Infrastructure & secrets |
| Research | 1 | AutoML & research |
| **Total** | **23** | **Complete tech stack** |

---

**Last Updated**: 2026-05-13  
**Total Frameworks**: 23  
**Status**: ✅ Ready for Claude AI Development
