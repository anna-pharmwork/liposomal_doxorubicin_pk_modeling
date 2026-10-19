# PBPK/Compartmental Modeling of Liposomal Doxorubicin

> A hybrid physiologically-based pharmacokinetic (PBPK) model evaluating the impact of controlled drug release and saturable MPS clearance on doxorubicin cardiotoxicity.

## 📋 Overview
This project implements a 6-compartment hybrid PK model to simulate the distribution of both liposomal and free doxorubicin in a murine model. The model specifically investigates how the liposomal release rate ($k_{release}$) and saturable Mononuclear Phagocyte System (MPS) clearance affect the peak concentration ($C_{max}$) in cardiac tissue, providing a mechanistic explanation for the cardioprotective effects of PEGylated liposomal doxorubicin (e.g., Doxil).

## 🧬 Model Structure
The model tracks two distinct forms of the drug across key physiological compartments:
1. **Liposomal DOX**: Plasma, MPS (liver/spleen aggregate), Tumor tissue.
2. **Free DOX**: Plasma, Heart tissue, Tumor tissue.

**Key Mechanisms Modeled:**
- **EPR Effect**: Passive accumulation of liposomes in tumor tissue.
- **Saturable MPS Clearance**: Modeled using Michaelis-Menten kinetics to account for macrophage capacity limits at high doses.
- **First-Order Release**: Controlled release of free DOX from liposomes in plasma and tumor compartments.
- **Perfusion-Limited Distribution**: For free DOX between plasma and heart tissue.

## 📊 Key Findings (Sensitivity Analysis)
- At physiologically relevant release rates ($k_{release}$ = 0.001–0.005 h⁻¹), the peak concentration ($C_{max}$) of free doxorubicin in heart tissue is reduced by **>95%** compared to the free drug formulation.
- The relationship between $k_{release}$ and cardiac $C_{max}$ is non-linear, plateauing at higher release rates due to perfusion limits ($Q_{heart}$).

## 🛠 Tools & Implementation
- **Language**: R (v4.4.1)
- **Packages**: `deSolve` (for solving stiff ODE systems via LSODA), `ggplot2` (for publication-ready visualization), `optim` (for parameter calibration).
- **Data**: Calibrated against published preclinical data (Luo et al., 2017; Cao et al., 2025).

## 📂 Repository Structure
- `doxorubicin_model.R`: Main R script containing the ODE system, parameter definitions, and solving logic.
- `sensitivity_analysis.R`: Script performing one-at-a-time sensitivity analysis on $k_{release}$.
- `results/`: Folder containing generated concentration-time profiles and sensitivity plots.
- `README.md`: This file.

## 🚀 How to Run
1. Ensure R and the `deSolve` and `ggplot2` packages are installed.
2. Source the `doxorubicin_model.R` script.
3. The script will output concentration-time plots for plasma and heart compartments, comparing free vs. liposomal DOX.
