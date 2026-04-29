# Dependencies Folder

This folder contains metadata and references to external repositories that your Project-PI codebase depends on or integrates with.

## Repositories Included

- **@garrytan/gstack** - https://github.com/garrytan/gstack
- **@nextlevelbuilder/ui-ux-pro-max-skill** - https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
- **@pbakaus/impeccable** - https://github.com/pbakaus/impeccable
- **@alchaincyf/huashu-design** - https://github.com/alchaincyf/huashu-design

## How to Use

### In JavaScript/Node.js

```javascript
const fs = require('fs');
const path = require('path');

// Load the repositories metadata
const repositoriesData = JSON.parse(
  fs.readFileSync(path.join(__dirname, 'repositories.json'), 'utf8')
);

// Access a specific repository
const gstack = repositoriesData.repositories.find(r => r.repo === 'gstack');
console.log(gstack.url); // https://github.com/garrytan/gstack
```

### In Python

```python
import json
import os

# Load the repositories metadata
with open(os.path.join(os.path.dirname(__file__), 'repositories.json'), 'r') as f:
    repositories_data = json.load(f)

# Access all repositories
for repo in repositories_data['repositories']:
    print(f"{repo['name']}: {repo['url']}")
```

### Accessing with Claude

When coding with Claude, you can reference this file to:
- Get repository URLs
- Access repository IDs
- Find owner information
- Maintain a centralized list of dependencies

## File Structure

```
dependencies/
├── repositories.json    # Metadata for all referenced repositories
└── README.md           # This file
```

Each repository entry contains:
- `name`: Full package-style name
- `owner`: GitHub username
- `repo`: Repository name
- `url`: GitHub repository URL
- `id`: GitHub repository ID
