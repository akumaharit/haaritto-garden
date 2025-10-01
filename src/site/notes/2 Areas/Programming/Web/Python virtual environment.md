---
{"dg-publish":true,"permalink":"/2-areas/programming/web/python-virtual-environment/","created":"2025-10-01T21:06:57.270+07:00","updated":"2025-10-01T21:07:52.713+07:00"}
---

Normally, if you install a Python package with `pip`, it gets installed system-wide (or user-wide). This can lead to problems:
- Different projects needing different versions of the same package.
- Risk of breaking existing code when upgrading a library.
A virtual environment solves this by creating a **self-contained folder** with its own `python` executable and `site-packages` directory.

### How it works
- You create one with:
    `python -m venv myenv`
- This makes a folder called `myenv/` containing a Python interpreter and its own package directory.
- You **activate** it (on Linux/Mac):
    `source myenv/bin/activate`
    or (on Windows):
    `myenv\Scripts\activate`
- When activated, running `python` or `pip install` uses the environment’s interpreter and packages, not the global ones.
- You can **deactivate** it with:
    `deactivate`

### Benefits
- Keeps projects independent.
- Makes it easier to reproduce and share setups (often paired with `requirements.txt`).
- Prevents version conflicts.
👉 In short: A Python virtual environment is like a sandbox for each project, so they don’t interfere with each other.