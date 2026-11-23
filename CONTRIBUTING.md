# Contributing to Pong-Game

Thank you for your interest in contributing! This guide explains how to get the project running on your machine.

---

## 1. Prerequisites

| Requirement | Minimum version |
|-------------|----------------|
| Python      | 3.6+           |
| Git         | any recent version |

Python's built-in `turtle` module is used for the game — no third-party packages are required, so there is **no `requirements.txt`** in this repository.

---

## 2. Clone the repo and set up a virtual environment

```bash
# Clone
git clone https://github.com/Just-in-time14/Pong-Game.git
cd Pong-Game

# Create and activate a virtual environment (recommended)
python -m venv .venv

# macOS / Linux
source .venv/bin/activate

# Windows (Command Prompt)
.venv\Scripts\activate.bat

# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

---

## 3. Install dependencies

This project has **no external dependencies**. It relies only on Python's standard library (`turtle`, `time`). No `pip install` step is needed.

---

## 4. Run the full test suite

> **Note:** This repository does not currently include automated tests. If you add tests (e.g. using `pytest`), place them in a `tests/` directory at the repo root and run:
>
> ```bash
> pytest
> ```
>
> Until tests are added, you can verify the game works by running it manually:
>
> ```bash
> python main.py
> ```

---

## 5. Run a single test file or a single test

Once tests exist, you can target a specific file or test with:

```bash
# Run a single test file
pytest tests/test_ball.py

# Run a single test by name
pytest tests/test_ball.py::test_bounce_wall
```

---

## 6. Troubleshooting

### `ModuleNotFoundError: No module named 'turtle'`
`turtle` is part of the Python standard library. This error usually means you are using a minimal Python build (common on some Linux distributions). Install the full Python package:

```bash
# Debian / Ubuntu
sudo apt-get install python3-tk
```

### `ModuleNotFoundError: No module named 'pytest'`
`pytest` is not installed in your current environment. Install it with:

```bash
pip install pytest
```

Make sure your virtual environment is activated before running `pip`.

### `_tkinter.TclError` or blank/frozen window on Linux
The `turtle` module requires a display. If you are on a headless server, you need a virtual display:

```bash
sudo apt-get install xvfb
Xvfb :99 -screen 0 1024x768x24 &
export DISPLAY=:99
python main.py
```
