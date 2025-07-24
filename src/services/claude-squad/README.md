# Claude Squad Service

Manages parallel execution of multiple Claude instances for complex, multi-faceted tasks.

## Key Components

- **ClaudeSquadManager**: Orchestrates multiple Claude agents
- **TaskDistributor**: Intelligently distributes subtasks to agents
- **ResultAggregator**: Combines results from multiple agents

## Features

- Parallel task execution
- Load balancing across Claude instances
- Result synthesis and conflict resolution
- Progress tracking and coordination

## Usage

```typescript
import { ClaudeSquadManager } from '@oppie/claude-squad';

const squad = new ClaudeSquadManager({
  maxAgents: 5,
  taskTimeout: 300000
});

const results = await squad.executeParallel(subtasks);
```
