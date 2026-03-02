# UV Guide

`uv` is an extremely fast Python package manager and resolver, written in Rust. It is used in this project to manage dependencies, virtual environments, and to run scripts in a reproducible way.

## Why use `uv`?

- **Fast**: Much faster than `pip` and `conda`.
- **Reliable**: Uses a lockfile (`uv.lock`) to ensure consistent environments across different machines.
- **Convenient**: Automatically manages virtual environments without needing to activate them manually (when using `uv run`).

## Common Commands

### 1. Project Setup
To install all dependencies and set up the project environment:
```bash
uv sync
```
This command reads `pyproject.toml` and `uv.lock`, creates a `.venv` directory (if it doesn't exist), and installs all necessary packages.

### 2. Running Code
Always prefix your commands with `uv run` to ensure they run within the project's virtual environment:
```bash
uv run python -m vlbench.indomain.train method=ivon model=resnet20 dataset=cifar10
```
This avoids the need to manually "activate" the environment.

### 3. Adding/Removing Dependencies
To add a new package:
```bash
uv add <package-name>
```

To remove a package:
```bash
uv remove <package-name>
```

### 4. Updating the Lockfile
If you want to update all project dependencies to their latest compatible versions:
```bash
uv lock --upgrade
```

## Tips

- You can still use standard tools inside the environment if you activate it manually: `source .venv/bin/activate`. However, using `uv run` is generally recommended for consistency.
- If you have multiple Python versions installed, `uv` will automatically find the correct one or download it for you.
