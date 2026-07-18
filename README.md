# Patient Treatment in the Emergency Department — Process Mining

Companion code repository for the exam project of **Business Information Systems**
(Prof. Paolo Ceravolo, Università degli Studi di Milano), Exam Call 20.07.2026 —
*Patient Treatment in the Emergency Department*.

Author: **Filippo Ferroni**

## Contents

The analysis is organised in five notebooks, one per phase of the
Knowledge Uplift Trail. Every result in the exam report cites the notebook
cell that produces it with the notation `NBxx-Cyy` (notebook + cell tag).

| Notebook | Phase |
|---|---|
| `NB01_Preprocessing.ipynb` | Audit, quality flags, dual raw/abstract view, case table |
| `NB02_Performance.ipynb` | KPIs, elapsed times, bottleneck, variant and distribution analysis |
| `NB03_DiscoveryConformance.ipynb` | Expected model, discovery (Alpha/Heuristics/Inductive), model selection, token replay + alignments, comparative mining |
| `NB04_PatternVariants.ipynb` | Additional question: binary phi mapping to context variants ("Variants of Variants") |
| `NB05_Prediction.ipynb` | Trace encoding, duration and admission prediction, improvement backlog |

`figures/` contains the aggregate figures exported by the notebooks and used
in the report.

## Data availability

The event log (`dataset_for_exam.csv`, 25,115 events / 1,820 stays) is
**anonymised but not public**: it is provided by the course exclusively for
this exam call and is therefore **not redistributed** here. For the same
reason the notebooks are published with their outputs cleared and the
row-level CSV exports are not included. With the dataset placed next to the
notebooks, running NB01 → NB05 in order reproduces every number and figure
of the report (fixed seeds, `random_state=42`).

## How to run

Each notebook is standalone and Colab-ready: the first cell installs the
pinned dependency (`pm4py==2.7.23.1`) and the dataset path is parameterised
at the top. Locally:

```bash
python3 -m venv ~/.venvs/bis-pm
~/.venvs/bis-pm/bin/pip install pm4py==2.7.23.1 scikit-learn seaborn scipy jupyterlab nbformat powerlaw
~/.venvs/bis-pm/bin/jupyter lab
```

Run order: `NB01` first (it exports the prepared views consumed by the
others), then `NB02`–`NB05` in any order (NB04 before NB05 to refresh the
phi features).
