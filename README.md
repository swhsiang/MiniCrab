# MiniCrab — Minimal Python AI Agent SDK

MiniCrab is a lightweight toolkit for building AI agents with minimal dependencies and opinionated defaults. It favors clarity over abstraction so you can prototype fast, read the code easily, and extend only what you need.

## Features
- Small, readable core with type hints and zero heavy frameworks.
- Simple task/agent abstractions that stay close to vanilla Python.
- uv-managed environment for reproducible installs and fast isolated runs.
- Pytest-friendly utilities for stubbing models and IO.

## Installation
```bash
uv sync             # install locked dependencies into .venv
uv run python -m mini_crab --help
```
Requirements: Python 3.11+ and uv installed (`pipx install uv` or see https://github.com/astral-sh/uv).

## Quickstart
```python
from mini_crab import Agent, Task

task = Task("summarize a paragraph")
agent = Agent(model="gpt-4o-mini")  # or your adapter

response = agent.run(task, context="Keep it concise.")
print(response.text)
```
Run it:
```bash
uv run python examples/basic.py
```

## Development
- Format & lint: `uv run ruff format` and `uv run ruff check`.
- Tests: `uv run pytest -q`.
- Local entrypoint: `uv run python -m mini_crab`.
- Keep new modules under `src/mini_crab/`; mirror tests in `tests/`.

## Configuration
- Model/provider settings come from environment variables; prefer `.env` for local values (never commit secrets).
- Defaults aim for safe offline behavior; explicit enablement is required for network-bound calls.

## Contributing
- Follow the guidelines in `AGENTS.md`.
- Use present-tense, imperative commit messages (e.g., `Add agent runner`).
- Add tests for behavior changes and update examples when APIs shift.

## License
Apache-2.0. See `LICENSE`.
