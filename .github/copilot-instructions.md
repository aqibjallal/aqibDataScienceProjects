<!-- Generated: update after review -->
# Copilot instructions for this repository

This repository is a small GitHub Codespace project centered on Jupyter notebooks. The goal of these instructions is to help AI coding agents be immediately productive by pointing to the project's structure, workflows, and concrete examples.

- **Big picture**: primary artifacts are under `notebooks/` (analysis and experiments) and `data/` (CSV fixtures). There is no packaged Python application or tests. Treat notebooks as the working source-of-truth for experiments (see `notebooks/image-classifier.ipynb`).

- **Key files/dirs**:
  - `notebooks/` — main work; open these in the Jupyter kernel. Example: `notebooks/image-classifier.ipynb` imports `torch`/`torchvision`.
  - `data/atlantis.csv` — sample dataset used by notebooks; prefer reading this directly for data-driven changes.
  - `requirements.txt` — authoritative dependency list; update it when adding packages.
  - `.devcontainer/` — contains Codespace/devcontainer materials; `hello.ipynb` is a minimal example kernel.

- **How to run / developer workflow (discoverable)**:
  1. Open the repository in GitHub Codespaces or the devcontainer so VS Code configures the Python environment automatically.
 2. Start the Jupyter server or open notebooks directly in VS Code's Notebook editor.
 3. Install dependencies locally (if not using devcontainer):

```
pip install -r requirements.txt
```

  - When adding or changing packages, update `requirements.txt` and re-run installs.

- **Project-specific conventions**:
  - Notebook-first development: prefer modifying notebooks in-place over creating new Python packages. When extracting reusable code, place modules in a new top-level package directory and add an entry to `requirements.txt` if external deps are required.
  - Keep data fixtures small and checked in under `data/` for reproducibility.

- **Patterns & examples**:
  - If adding model training code, mirror the layout used by `notebooks/image-classifier.ipynb`: data load → transforms → model definition (PyTorch) → training loop → metrics/logging in notebook cells.
  - Dependencies: heavy ML libs (`torch`, `torchvision`) are present in `requirements.txt`; expect slower installs in Codespaces and large wheel downloads. Consider advising users to use the devcontainer which pre-configures the environment.

- **Integration & external dependencies**:
  - `requirements.txt` lists pip packages used by notebooks. No external APIs or services are referenced in the repository.

- **What AI agents should do (concrete, repo-specific tasks)**:
  - For code changes: open the notebook that uses the code (link to `notebooks/`), propose minimal, incremental notebook edits and include runnable cell snippets.
  - When introducing new dependencies, add them to `requirements.txt` and include the exact `pip` command to reproduce installs.
  - When refactoring from notebook to module, create a new package folder (e.g., `src/`), move functions/classes, and add small example notebook cells showing usage.

- **What NOT to do**:
  - Do not assume there is a test suite or CI configuration unless added; do not add broad refactors across many notebooks without user confirmation.

If anything is unclear or you want more detail in a specific area (tests, packaging, CI, or refactor guidance), tell me which part to expand or provide an example for and I will iterate.
