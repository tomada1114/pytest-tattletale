# pytest-tattletale

pytest plugin that names which test polluted process-global state, and what exactly changed

## Installation

=== "pip"

    ```bash
    pip install pytest-tattletale
    ```

=== "uv"

    ```bash
    uv add pytest-tattletale
    ```

## Quick Example

```python
from pytest_tattletale import add

result = add(1, 2)
print(result)  # 3
```

## Next Steps

- [Getting Started](getting-started.md) — setup and first steps
- [API Reference](reference.md) — full API documentation
- [Contributing](contributing.md) — how to contribute
