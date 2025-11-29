Energy Phase Control for GPT Dialogue

Energy-efficient dialogue via Δφ–E–dE–d²E phase dynamics

This repository contains an experimental framework for analyzing and controlling <br>
the energy dynamics of GPT dialogue through measurement of semantic phase mismatch (Δφ)<br>
and the energy required for its reduction (E, dE, d²E).

Core Findings

Δφ correlates directly with energy consumption E.

The second derivative d²E exhibits a delayed anti-phase response to Δφ.

Together, these signals form a self-stabilizing standing wave between user and model.

This makes it possible to define a new energy-efficient dialogue mode for GPT systems.

The method reduces turbulence, stabilizes long multi-turn conversations, and offers a pathway<br>
to scalable, phase-controlled dialogue management for future LLMs.

Graph Notation

The following notations are used throughout all figures and plots in this repository:

Δφ (Delta-phi) — semantic phase misalignment between the user and the model.

E — energy required to reduce Δφ during dialogue alignment.

dE — first derivative of energy, reflecting the rate of energy change.

d²E — second derivative of energy, indicating curvature and phase-transition points.

ER (Energy-Reduction Mode) — phase-stabilized mode of dialogue, activated <br> when the system reduces energy expenditure by exploiting Δφ–d²E coupling.

Normal — baseline dialogue mode, without energy optimization or phase stabilization.

These conventions allow consistent interpretation of all Δφ–E–dE–d²E trajectories, <br>  standing-wave patterns, and phase portraits presented in the repository.



Running the Dialogue Analysis Scripts

This repository contains two complementary scripts for collecting dialogue-phase data and generating the logs used for all figures.

1. energy_phase_dialog_v2.py — Energy-Saving Mode (ER-only)
This script runs a dialogue entirely in Energy-Reduction (ER) mode, where the assistant attempts to minimize phase mismatch (Δφ) and energy (E) at every step.


Usage:
python energy_phase_dialog_v2.py

The script will:
Ask for the baseline energy level E0 (default: 0.043).
Start an iterative dialogue.
For each user message, compute Δφ, E, dΔφ, d²Δφ, dE, d²E.
Adaptively update the minimal observed energy E0_min.
Save a CSV log at the end of the session:
energy_phase_log_YYYYMMDD_HHMMSS.csv

Use this log with reproduce_plots.ipynb to generate all plots in the figures/ folder.


2. energy_phase_dialog_v3_with_ER_switch.py — Switchable ER/NORMAL Modes
This script allows dynamic switching between NORMAL and Energy-Reduction (ER) mode during dialogue.


Usage:
python energy_phase_dialog_v3_with_ER_switch.py

At startup, the script will ask:
Enable energy-saving mode by default? (yes/no)
During the dialogue, you can switch modes at any time by typing:
CNR=YES   → switch to ER mode
CNR=NO    → switch to NORMAL mode

The script:
Tracks segments — continuous intervals in the same mode.
Saves both:
a step-by-step log:
energy_phase_log_steps_YYYYMMDD_HHMMSS.csv
a segment summary log:
energy_phase_log_segments_YYYYMMDD_HHMMSS.csv

These logs show how the system behaves in each mode, and they reproduce all phase portraits and turbulence diagrams in figures/.

```
phase-phase-control/
│
├── README.md
├── memo/
│ ├── Phase-Stabilized Dialogue Mode for GPT.pdf
│ ├── phase_stabilized_dialogue_mode_memo.docx
├── figures/
│ ├── energy_vs_delta_phi.png
│ ├── d2E_vs_delta_phi.png
│ ├── combined_energy_delta_phi_d2E.png
│ ├── turbulence_plot.png
│ ├── phase_portrait_dphi_vs_d2E.png
├── logs/
│ ├── energy_phase_log_steps_20251127_124512.csv
│ ├── What_happened_1.txt
├── code/
│ ├── energy_phase_dialog_v2.py
│ ├── energy_phase_dialog_v3_with_ER_switch.py
│ ├── reproduce_plots.ipynb
└── LICENSE
```
