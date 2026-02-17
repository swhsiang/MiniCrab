# Repository Guidelines

## Project Structure & Module Organization
- Keep runtime code under `src/mini_crab/`; prefer small, single-responsibility modules with clear public interfaces. 
- Place tests in `tests/` mirroring the package layout; fixtures belong in `tests/fixtures/`. 
- Use `examples/` for runnable snippets that demonstrate SDK usage, and `scripts/` for one-off maintenance helpers. 
- Store shared assets (sample data, prompts) in `assets/` with a README describing provenance and licensing. 

## Build, Test, and Development Commands
- Install and lock dependencies with `uv sync`; re-lock upgrades with `uv lock --upgrade`. 
- Run the package locally with `uv run python -m mini_crab` (or target the specific module you are developing). 
- Execute the full test suite with `uv run pytest`; add `-q` for concise output. 
- Lint/format (when configured) via `uv run ruff check` and `uv run ruff format`; keep zero warnings before opening a PR. 

## Coding Style & Naming Conventions
- Follow PEP 8 and prefer explicit type hints; enable `from __future__ import annotations` for forward refs. 
- Functions, variables, and modules use `snake_case`; classes use `CapWords`; constants are `UPPER_SNAKE_CASE`. 
- Favor pure, side-effect–light functions; isolate I/O behind clear interfaces. 
- Docstrings follow Google style; include argument/return types and expected side effects. 

## Testing Guidelines
- Use `pytest`; name files `test_*.py` and tests `test_*`; group behavior-oriented cases over unit internals. 
- Add regression tests for every bug fix; prefer parametrization over loops to cover variants. 
- Keep tests hermetic: no network or filesystem writes outside temporary directories; seed randomness deterministically. 
- Track meaningful coverage locally with `uv run pytest --cov=mini_crab --cov-report=term-missing`. 

## Commit & Pull Request Guidelines
- Commits use present-tense imperatives (`Add uv setup`, `Fix parser error`); keep summaries under ~72 characters. 
- Each PR includes a short description, linked issue (if any), test results, and notes on risk/rollout. 
- When changing behavior or APIs, include before/after examples and update relevant docs or examples. 
- Squash only if it improves clarity; otherwise keep logically separated commits for review. 

## Security & Configuration Tips
- Never commit secrets; `.env` is ignored—store credentials locally and document required keys in `README.md`. 
- Pin dependency versions via `uv.lock`; avoid system-wide installs. 
- Prefer configuration via environment variables with safe defaults; validate inputs at process start. 
