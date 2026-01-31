## Contents of `EpoAdapt.zip`

Unzipping the archive reveals a “single working directory” layout. In particular, the Colab notebooks invoke the experiment runner directly via shell calls such as

`!python3 outdegree_opt_mut.py -adjacency_file graph100-01.txt -outdegree_file graph100_eps.txt -algo EPOAdapt -budget 100 -probability 0.05 -T 4 -times 1`

so the runner script and the dataset files it references are expected to be reachable relative to the notebook’s working directory.

The extracted structure is:

- `outdegree/`  
  Graph datasets used in all experiments (e.g., `graph100`, `graph200`, `insecta`). The experiment scripts are configured so that EpoAdapt and baselines evaluate on identical data originating from this shared dataset directory.

- `scripts_EpoAdapt/`  
  Experiment-driving Colab notebooks and supporting code for EpoAdapt. The notebooks run the main Python runner (e.g., `outdegree_opt_mut.py`) via `!python3 ...` commands and compute the summary results used for reporting.

- `Results/`  
  Precomputed logs and outputs for **EpoAdapt runs only**. These are the artifacts the notebooks use to produce the EpoAdapt entries in the paper’s tables/plots.

- `EPOL/`  
  Baseline code and outputs for EPOL-style comparisons. This folder contains the baseline Python implementation and the baseline-driving notebooks/scripts under `EPOL/scripts/` (EPOMC/EPOL, POMC, FPOMC). For these scripts to run, the dataset folder (`outdegree/`) must be present inside `EPOL/` so relative file paths resolve correctly. The directory `EPOL/Results_01/` contains the resulting logs/outputs used by the notebooks to produce the baseline entries in the paper’s tables/plots (notably the \(B=100\) plots).
  
## Reproducibility guide (what is precomputed vs rerunnable)

The notebooks are provided in a verification-friendly form: notebook metadata has been scrubbed for anonymity, but run outputs and result calculations are preserved so that the logged runs and the derived summary numbers corresponding to the paper’s tables/figures can be inspected directly. The same notebooks can also be executed end-to-end to regenerate logs and recompute summaries, provided the directory structure is kept intact (especially that the runner scripts and the `outdegree/` data are in the expected relative locations).
