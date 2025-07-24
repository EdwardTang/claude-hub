# Orchestrator Service

The Orchestrator service is the brain of Oppie, implementing Monte Carlo Tree Search (MCTS) using LangGraph for intelligent task planning and execution.

## Key Components

- **MCTSOrchestrator**: Main orchestration engine that manages the MCTS algorithm
- **TaskPlanner**: Breaks down complex tasks into actionable steps
- **StateManager**: Manages agent state and context across planning cycles

## Architecture

```
┌─────────────────┐
│  GitHub Event   │
└────────┬────────┘
         │
    ┌────▼────┐
    │  MCTS   │◄──── LangGraph
    │  Tree   │      Workflows
    └────┬────┘
         │
┌────────▼────────┐
│ Action Selection│
└─────────────────┘
```

## Usage

```typescript
import { MCTSOrchestrator } from '@oppie/orchestrator';

const orchestrator = new MCTSOrchestrator({
  maxDepth: 10,
  explorationConstant: 1.41,
  simulationCount: 100
});

const plan = await orchestrator.planTask(githubIssue);
```
