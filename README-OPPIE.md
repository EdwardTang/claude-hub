# Oppie - AI-Powered GitHub Development Agent

Oppie is an autonomous AI agent built on Claude-Hub that uses Monte Carlo Tree Search (MCTS) and LangGraph to plan and execute complex software development tasks. It extends the Claude-Hub webhook system with advanced reasoning capabilities, persistent state management, and intelligent task orchestration.

## 🎯 What is Oppie?

Oppie transforms GitHub issues into completed pull requests through intelligent planning and execution. Unlike simple code generation tools, Oppie:

- **Plans Before Acting**: Uses MCTS to explore multiple solution paths and select optimal approaches
- **Manages Complex State**: Tracks progress across sessions with Neo4j graph database
- **Learns from Experience**: Improves task execution through Q-learning and experience replay
- **Handles Edge Cases**: Gracefully recovers from errors and adapts strategies

## 🚀 Key Features

### Intelligent Planning with MCTS
- Explores multiple implementation strategies before coding
- Evaluates trade-offs between different approaches
- Selects optimal paths based on learned patterns

### Advanced State Management
- **Neo4j**: Stores MCTS trees and agent memory
- **Redis**: Caches active sessions and intermediate results
- **AWS S3**: Persists conversation history and artifacts

### LangGraph Integration
- Structured workflow execution
- Conditional branching based on context
- Parallel task processing
- State checkpointing and rollback

### Extended Claude-Hub Capabilities
- All existing Claude-Hub webhook features
- Enhanced PR review with architectural analysis
- Multi-file refactoring coordination
- Test-driven development workflows

## 🏗️ Architecture

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  GitHub Events  │────▶│  Webhook Handler │────▶│  Task Analyzer  │
└─────────────────┘     └──────────────────┘     └─────────────────┘
                                                           │
                                                           ▼
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│   Neo4j Graph   │◀────│   MCTS Planner   │◀────│ LangGraph Agent │
└─────────────────┘     └──────────────────┘     └─────────────────┘
                                                           │
                                                           ▼
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Redis Cache    │◀────│ State Manager    │────▶│  Claude Code    │
└─────────────────┘     └──────────────────┘     └─────────────────┘
```

## 🛠️ Technology Stack

- **Core**: Node.js + TypeScript
- **AI**: Claude Code API + LangGraph.js
- **Planning**: Custom MCTS implementation
- **Databases**: Neo4j (graph), Redis (cache)
- **Storage**: AWS S3 (artifacts), MinIO (local dev)
- **Container**: Docker + Docker Compose
- **Testing**: Jest + End-to-end test framework

## 📋 Prerequisites

- Node.js 20+
- Docker & Docker Compose
- GitHub account with webhook access
- Claude API access (via Anthropic API key or AWS Bedrock)
- Neo4j instance (included in Docker Compose)
- Redis instance (included in Docker Compose)

## 🚀 Quick Start

1. **Fork and Clone**
   ```bash
   git clone git@github.com:YourUsername/claude-hub.git oppie
   cd oppie
   ```

2. **Configure Environment**
   ```bash
   cp .env.example .env
   # Edit .env with your credentials
   ```

3. **Start Services**
   ```bash
   docker compose up -d
   ```

4. **Initialize Database**
   ```bash
   npm run db:init
   ```

5. **Test Webhook**
   ```bash
   npm run test:webhook -- --repo YourOrg/YourRepo --issue 1
   ```

## 📖 Documentation

- [Complete Setup Guide](./docs/oppie/setup-guide.md)
- [MCTS Implementation](./docs/oppie/mcts-architecture.md)
- [LangGraph Workflows](./docs/oppie/langgraph-flows.md)
- [API Reference](./docs/oppie/api-reference.md)
- [Development Guide](./docs/oppie/development.md)

## 🧪 Testing

```bash
# Unit tests
npm test

# Integration tests
npm run test:integration

# End-to-end tests
npm run test:e2e

# MCTS performance tests
npm run test:mcts-perf
```

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

## 📄 License

This project extends Claude-Hub and is licensed under the MIT License. See [LICENSE](./LICENSE) for details.

## 🙏 Acknowledgments

Built on top of the excellent [Claude-Hub](https://github.com/claude-hub/claude-hub) project.