# pytest-tattletale

[![CI](https://github.com/tomada1114/pytest-tattletale/actions/workflows/ci.yml/badge.svg)](https://github.com/tomada1114/pytest-tattletale/actions/workflows/ci.yml)
[![codecov](https://codecov.io/gh/tomada1114/pytest-tattletale/branch/main/graph/badge.svg)](https://codecov.io/gh/tomada1114/pytest-tattletale)
[![PyPI](https://img.shields.io/pypi/v/pytest-tattletale)](https://pypi.org/project/pytest-tattletale/)
[![Python](https://img.shields.io/pypi/pyversions/pytest-tattletale)](https://pypi.org/project/pytest-tattletale/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

pytest plugin that names which test polluted process-global state, and what exactly changed

## Quickstart

```bash
pip install pytest-tattletale
# or
uv add pytest-tattletale
```

```python
from pytest_tattletale import add

result = add(1, 2)  # 3
```

## Design Philosophy

Every choice in this template has a reason. If you disagree with a decision,
you know exactly what to change and why it was there in the first place.

### Why `src/` layout?

The `src/` layout prevents accidental imports of the local package during
development and testing. It ensures that tests always run against the
*installed* version, catching packaging errors before they reach users.

### Why strict mypy + comprehensive Ruff rules?

Type errors and lint issues are cheapest to fix at write time. Strict settings
from day one mean every line of code is held to the same standard — there is
never a "legacy" codebase to clean up. LLMs generating code also benefit from
strict rules: they produce higher-quality output when constraints are clear.

### Why zero runtime dependencies?

A library template should not impose opinions about logging, HTTP clients, or
data validation. You add what you need. Starting from zero keeps the dependency
tree small and avoids conflicts with downstream users.

### Why Just over Make?

Just has cleaner syntax (no mandatory tabs), better cross-platform support, and
more readable recipe definitions. It is a task runner, not a build system —
which is exactly what a Python project needs.

### Why AGENTS.md and .claude/?

AI-assisted development is the norm, not the exception. `AGENTS.md` gives any
coding agent (Claude Code, Codex, Cursor, Gemini CLI, ...) the context it
needs to match your project's standards; `CLAUDE.md` imports it and adds
Claude Code specifics. The committed `.claude/` directory goes further than
prose: path-scoped rules load conventions only when relevant files are
touched, hooks deterministically auto-format edited files, block edits to
`uv.lock`/`.env*` and `--no-verify`/force-push commands, and run ruff + mypy
before the agent ends a turn, while a reviewed permission allowlist covers
local build/lint/test commands only — commit, push, and PR creation always
stay behind human approval.

### Why 80% coverage minimum?

80% is high enough to catch most regressions but low enough to avoid
test-for-the-sake-of-testing. Branch coverage is enabled, so conditional logic
is meaningfully tested.

## Development

See [CONTRIBUTING.md](CONTRIBUTING.md) for full setup instructions.

```bash
uv sync --all-groups
# Optional but recommended when working in a Git checkout
uv run pre-commit install --install-hooks
just check
```

`just install` installs pre-commit hooks automatically when the project lives in
a Git repository and skips that step for "Use this template" bootstrap copies
before Git is initialized.

For packaging verification, run `just smoke` (or `uv build && uv run python scripts/smoke_test.py`)
to install the freshly built wheel into a temporary virtual environment and
confirm the distribution imports from the wheel, not from `src/`.

## Documentation

- [Getting Started](https://tomada1114.github.io/pytest-tattletale/getting-started/)
- [API Reference](https://tomada1114.github.io/pytest-tattletale/reference/)

## License

[MIT](LICENSE)
