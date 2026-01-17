# Newton Loop - Anytime Optimization Framework

**Newton Loop** is a generic anytime optimization framework that uses disk artifacts and CLI tools to solve domain-agnostic problems through evaluation-advice-execution cycles.

## Features

- **Algorithm-Agnostic**: Pluggable architecture where you provide domain-specific optimization logic
- **Anytime Optimization**: Continuous improvement with evaluation-advice-execution cycles
- **CLI Tool Integration**: External command-line tools required - no fallbacks
- **Disk-Based State**: All problem state as artifacts on disk, never in memory
- **Safety First**: Validation gates, audit trails, and rollback capabilities
- **Language Agnostic**: Algorithms can be implemented in any programming language

## Installation

```bash
pip install newton-loop
```

**Prerequisites**: Python 3.11+

## Quick Start

```bash
# Run optimization on existing workspace
newton run <workspace-path> --max-iterations 100

# Check status
newton status <execution-id>
```

See [QUICKSTART.md](QUICKSTART.md) for detailed examples.

## Usage

### Commands

```bash
newton run <path>               # Execute optimization loop
newton step <path>              # Execute single iteration
newton status <execution-id>    # Check execution status
newton report <execution-id>    # Generate optimization report
```

### Workspace Structure

```
workspace/
├── problem/
│   ├── GOAL.md         # Optimization objectives
│   └── CONSTRAINTS.md  # Problem constraints
├── tools/              # CLI tools (evaluator, advisor, executor)
├── solution.json       # Current solution
├── state/              # Execution state
└── evidence/           # Audit trail
```

## Architecture

### Framework Components

- **Optimization Orchestrator**: Coordinates evaluation-advice-execution cycles
- **Workspace Controller**: File operations and validation
- **Results Processor**: Analysis and reporting
- **Safety Validator**: Validation gates and controls

### Algorithm Components (User Provided)

- **Evaluator**: Assesses solution quality and returns metrics
- **Advisor**: Generates improvement recommendations
- **Executor**: Applies recommended changes

### CLI Tool Integration

Tools communicate via environment variables and file artifacts:

```bash
# Tools receive NEWTON_* environment variables
# Evaluator writes score to $NEWTON_SCORE_FILE
# Advisor writes recommendations to $NEWTON_ADVISOR_DIR
# Executor updates solution and writes logs to $NEWTON_EXECUTOR_DIR
```

## How It Works

Newton Loop orchestrates **evaluation-advice-execution** cycles:

1. **Evaluator**: Analyzes current solution and writes score to file
2. **Advisor**: Reviews evaluation and generates recommendations
3. **Executor**: Applies changes and updates solution state

### Tool Communication

Tools communicate via environment variables (`NEWTON_*`) and file artifacts. All tools must exit 0 for success.

**Key Environment Variables:**
- `NEWTON_WORKSPACE_PATH`: Workspace location
- `NEWTON_SCORE_FILE`: Where evaluator writes numeric score
- `NEWTON_EVALUATOR_DIR`: Evaluator output directory
- `NEWTON_ADVISOR_DIR`: Advisor output directory
- `NEWTON_EXECUTOR_DIR`: Executor output directory

## Documentation

- **[Quick Start](QUICKSTART.md)** - Get started quickly
- **[Examples](docs/examples/)** - Sample use cases
- **[API Reference](docs/api-reference/)** - Complete command documentation

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make changes with tests
4. Submit pull request

## License

See LICENSE file for details.
