# Jupyter Notebook in Teaching

One self-contained Jupyter notebook for a 60-minute session on Jupyter Notebook,
its use in teaching, and how AI can help prepare teaching material. It runs on an
ordinary laptop CPU.

**Main file:** `Jupyter_in_Teaching_FEM_and_PINNs.ipynb`

| Part | Content |
|:--:|:--|
| 1 | **Introduction to Jupyter Notebook**: what Jupyter is, front-end / server / kernel, getting started, cells and shortcuts, Markdown and LaTeX, kernel state and hidden-state pitfalls, rich output and magics, notebooks in teaching, AI assistance for preparing notebooks |
| 2 | **Finite elements for the 1D heat equation**: weak form, P1 elements in space (method of lines, mass and stiffness matrices), backward Euler and Crank-Nicolson in time, stiffness and the explicit stability limit, snapshots, an animation and a space-time plot of the solution, and L2 / H1 error analysis with convergence studies in space and time |
| 3 | **Physics-informed neural networks for the 2D Navier-Stokes equations**: what PINNs are, the incompressible Navier-Stokes equations and Kovasznay flow, PyTorch essentials, implementing and training a PINN (Adam + L-BFGS), visualization and validation |

The notebook starts with a contents list; the references for all three parts are
collected at the end. Each part runs on its own
after the Setup cells, so you can also jump directly to Part 2 or Part 3.

## Setup (once)

**Option A: conda** (Anaconda, Miniconda or Miniforge)

```bash
conda env create -f environment.yml
conda activate jshare
jupyter lab
```

**Option B: pip + virtual environment**

```bash
python -m venv jshare-env
source jshare-env/bin/activate        # Windows: jshare-env\Scripts\activate
python -m pip install -r requirements.txt
jupyter lab
```

Requirements: Python 3.9-3.12, NumPy (1.x or 2.x), SciPy, Matplotlib, JupyterLab,
and PyTorch (CPU build is enough; only Part 3 needs it). No GPU, internet
connection or data files are needed.

## How to use

- Run the cells from top to bottom with **Shift+Enter**, or use
  **Kernel > Restart Kernel and Run All Cells...** (about 1.5 minutes in total; almost
  all of it is the PINN training in Section 3.6, about 1 minute).
- The notebook is delivered **with its outputs saved**, so it can be shown or read
  without running anything. For a clean student copy use
  **Edit > Clear Outputs of All Cells** (or
  `jupyter nbconvert --clear-output --inplace Jupyter_in_Teaching_FEM_and_PINNs.ipynb`).
- Cells that only draw figures are collapsed; click the bar to the left of a cell to
  expand it.
- The movie in Section 2.5 is an HTML/JavaScript player. In a freshly opened notebook
  it may only play after re-running that cell or trusting the notebook
  (**File > Trust Notebook**).
- On a slow laptop, halve `n_adam` and `n_lbfgs` in the `CONFIG` cell of Section 3.5.

## Files

```text
Jupyter-share/
|-- Jupyter_in_Teaching_FEM_and_PINNs.ipynb   # the merged 60-minute notebook (main file)
|-- README.md
|-- requirements.txt                           # pip dependencies
|-- environment.yml                            # conda environment "jshare"
```

Saved outputs were produced with Python 3.10, NumPy 1.26, SciPy 1.13,
Matplotlib 3.8 and PyTorch 2.2 (CPU). Timings and the last digits of the PINN
errors differ slightly between machines.
