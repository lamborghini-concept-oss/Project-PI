# Dependencies Folder

This folder contains metadata and references to all external repositories, frameworks, and libraries that your Project-PI codebase integrates with or depends on.

**Key Feature**: Each framework includes installation commands that Claude Code can execute programmatically!

---

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

## 🚀 Quick Installation

### Auto-Install All Frameworks (Claude Code)

```javascript
const fs = require('fs');
const { execSync } = require('child_process');

// Read repository metadata
const repositories = JSON.parse(
  fs.readFileSync('./dependencies/repositories.json', 'utf8')
);

// Install all Python packages
repositories.forEach(repo => {
  if (repo.pypiCommand) {
    console.log(`Installing ${repo.name}...`);
    try {
      execSync(repo.pypiCommand, { stdio: 'inherit' });
    } catch (error) {
      console.error(`Failed to install ${repo.name}: ${error.message}`);
    }
  }
});

// Install all npm packages
repositories.forEach(repo => {
  if (repo.npmCommand) {
    console.log(`Installing ${repo.name}...`);
    try {
      execSync(repo.npmCommand, { stdio: 'inherit' });
    } catch (error) {
      console.error(`Failed to install ${repo.name}: ${error.message}`);
    }
  }
});
```

### Python Auto-Install Script

```python
import json
import subprocess
import sys

# Load repository metadata
with open('./dependencies/repositories.json', 'r') as f:
    repositories = json.load(f)

# Install all Python packages
for repo in repositories:
    if 'pypiCommand' in repo:
        print(f"Installing {repo['name']}...")
        try:
            subprocess.run(repo['pypiCommand'].split(), check=True)
        except subprocess.CalledProcessError as e:
            print(f"Failed to install {repo['name']}: {e}")

# Install Node packages if needed
for repo in repositories:
    if 'npmCommand' in repo:
        print(f"Installing {repo['name']} via npm...")
        try:
            subprocess.run(repo['npmCommand'].split(), check=True)
        except subprocess.CalledProcessError as e:
            print(f"Failed to install {repo['name']}: {e}")
```

---

## 📦 Installation Commands Reference

### Agentic AI

| Framework | Install Command |
|-----------|-----------------|
| **AutoGen** | `pip install pyautogen` |
| **CrewAI** | `pip install crewai` |
| **LangGraph** | `pip install langgraph` |
| **OpenAI Swarm** | `pip install openai-swarm` |

### Simulation & Modeling

| Framework | Install Command |
|-----------|-----------------|
| **Mesa** | `pip install mesa` |
| **SimPy** | `pip install simpy` |
| **KataGo** | `git clone https://github.com/lightvector/KataGo.git && cd KataGo && ./build.sh` |
| **Ray RLlib** | `pip install 'ray[rllib]'` |

### Market Analysis & Data

| Framework | Install Command |
|-----------|-----------------|
| **FinGPT** | `git clone https://github.com/AI4Finance-Foundation/FinGPT.git && pip install -r requirements.txt` |
| **GDELT** | `pip install gdelt` |

### Recommendations Engine

| Framework | Install Command |
|-----------|-----------------|
| **Evidently AI** | `pip install evidently` |
| **CausalML** | `pip install causalml` |
| **What-If Tool** | `pip install witwidget` |

### Visualization

| Framework | Install Command | CDN Link |
|-----------|-----------------|----------|
| **D3.js** | `npm install d3` | https://d3js.org/d3.v7.min.js |
| **Cytoscape.js** | `npm install cytoscape` | https://cdnjs.cloudflare.com/ajax/libs/cytoscape/3.28.1/cytoscape.umd.js |
| **React Flow** | `npm install reactflow` | N/A |

### UI/UX Design Systems

| Framework | Install Command |
|-----------|-----------------|
| **gstack** | `npm install gstack` |
| **ui-ux-pro-max-skill** | `git clone https://github.com/nextlevelbuilder/ui-ux-pro-max-skill.git` |
| **impeccable** | `npm install impeccable` |
| **huashu-design** | `git clone https://github.com/alchaincyf/huashu-design.git` |

### DevOps & Container Management

| Framework | Install Command | Docker Pull |
|-----------|-----------------|-------------|
| **Flux CD** | `helm repo add fluxcd https://charts.fluxcd.io && helm install flux-source-controller fluxcd/source-controller` | `docker pull ghcr.io/fluxcd/source-controller:latest` |
| **External Secrets** | `helm repo add external-secrets https://charts.external-secrets.io && helm install external-secrets external-secrets/external-secrets` | `docker pull ghcr.io/external-secrets/external-secrets:latest` |

---

## 📚 Documentation Links

### Loading Dependencies in JavaScript/Node.js

```javascript
const fs = require('fs');
const path = require('path');

// Load all repositories
const repositories = JSON.parse(
  fs.readFileSync(path.join(__dirname, 'repositories.json'), 'utf8')
);

// Find a framework and get its install command
const autogen = repositories.find(r => r.name === 'AutoGen');
console.log(`Installing: ${autogen.installCommand}`);
console.log(`Docs: ${autogen.documentation}`);

// Programmatically get all install commands
const installCommands = repositories
  .filter(r => r.installCommand)
  .map(r => ({ name: r.name, command: r.installCommand }));

console.table(installCommands);
```

### Loading Dependencies in Python

```python
import json
import os

# Load all repositories
with open(os.path.join(os.path.dirname(__file__), 'repositories.json'), 'r') as f:
    repositories = json.load(f)

# Find a framework
mesa = next(r for r in repositories if r['name'] == 'Mesa')
print(f"Installing: {mesa['installCommand']}")
print(f"Docs: {mesa['documentation']}")

# Filter by category and get commands
simulation = [r for r in repositories if 'Simulation' in r.get('category', '')]
for framework in simulation:
    print(f"{framework['name']}: {framework.get('installCommand', 'N/A')}")
```

### Accessing with Claude Code

```javascript
// Get all installation commands for a category
const agentic = repositories.filter(r => r.category === 'Agentic AI');
agentic.forEach(framework => {
  console.log(`${framework.name}:`);
  console.log(`  Install: ${framework.installCommand}`);
  console.log(`  Docs: ${framework.documentation}`);
  console.log(`  GitHub: ${framework.url}`);
});
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

- **Installation Configuration**: See `repositories.json`
- **Integration Architecture**: See `FRAMEWORK_GUIDE.md`
- **Container Registries**: 
  - Flux CD: https://github.com/fluxcd/source-controller/pkgs/container/source-controller
  - External Secrets: https://github.com/external-secrets/external-secrets/pkgs/container/external-secrets

---

## 💡 Use Cases for Claude Code

### 1. **Auto-Install Dependencies**
```javascript
const repo = repositories.find(r => r.name === 'AutoGen');
execSync(repo.installCommand, { stdio: 'inherit' });
```

### 2. **Generate Setup Documentation**
```javascript
repositories.forEach(r => {
  console.log(`## ${r.name}\n`);
  console.log(`Install: ${r.installCommand}\n`);
  console.log(`Docs: ${r.documentation}\n`);
});
```

### 3. **Docker Container Setup**
```javascript
const devopsRepos = repositories.filter(r => r.category.includes('DevOps'));
devopsRepos.forEach(r => {
  if (r.dockerPull) {
    console.log(`${r.name}: ${r.dockerPull}`);
  }
});
```

### 4. **Filter by Language Support**
```javascript
// Get all npm-installable packages
const npmPackages = repositories.filter(r => r.npmCommand);
// Get all pip-installable packages
const pythonPackages = repositories.filter(r => r.pypiCommand);
```

---

## 📁 Files Structure

```
dependencies/
├── repositories.json     # Metadata with install commands for all 23 frameworks
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
  "installCommand": "Primary install method (pip/npm/git clone)",
  "pypiCommand": "pip install command (if available)",
  "npmCommand": "npm install command (if available)",
  "dockerPull": "Docker pull command (DevOps only)",
  "cdnLink": "CDN link for frontend libs",
  "documentation": "Official documentation URL",
  "githubPages": "GitHub README/wiki link"
}
```

---

## 📝 Adding New Frameworks

To add a new framework to the dependencies:

1. Add entry to `repositories.json` with all installation commands
2. Update relevant sections in `FRAMEWORK_GUIDE.md`
3. Include category classification
4. Add all relevant install commands (pip, npm, helm, docker, etc.)

Example:
```json
{
  "name": "New Framework",
  "owner": "github_owner",
  "repo": "repository_name",
  "url": "https://github.com/owner/repo",
  "category": "Category Name",
  "installCommand": "pip install new-framework",
  "pypiCommand": "pip install new-framework",
  "documentation": "https://docs.example.com"
}
```

---

## ✨ Categories at a Glance

| Category | Count | Install Type | Purpose |
|----------|-------|--------------|---------|
| Agentic AI | 4 | pip | Multi-agent orchestration |
| Simulation | 4 | pip/git/cmake | Modeling & predictions |
| Market Analysis | 2 | pip/git | Trend & disruptor detection |
| Recommendations | 3 | pip | Decision intelligence |
| Visualization | 3 | npm/CDN | Interactive UI rendering |
| UI/UX | 4 | npm/git | Design systems |
| DevOps | 2 | helm/docker | Infrastructure & secrets |
| Research | 1 | pip/git | AutoML & research |
| **Total** | **23** | **Mixed** | **Complete tech stack** |

---

## 🎯 Quick Setup Command (All Frameworks)

**For Python developers:**
```bash
pip install pyautogen crewai langgraph openai-swarm mesa simpy gdelt evidently causalml witwidget
pip install 'ray[rllib]'
```

**For Node.js developers:**
```bash
npm install d3 cytoscape reactflow gstack impeccable
npm install @langchain/langgraph @tensorflow/tfjs @pair-code/what-if-tool
```

**For DevOps (Kubernetes):**
```bash
helm repo add fluxcd https://charts.fluxcd.io
helm repo add external-secrets https://charts.external-secrets.io
helm install flux-source-controller fluxcd/source-controller
helm install external-secrets external-secrets/external-secrets
```

---

**Last Updated**: 2026-05-13  
**Total Frameworks**: 23  
**Installation Methods**: pip, npm, helm, docker, git clone  
**Status**: ✅ Ready for Claude Code Auto-Installation
