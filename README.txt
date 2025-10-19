# SUSY Anomaly Detection in ATLAS Open Data — 2 Jets + 2 Leptons + MET
![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)
![ROOT](https://img.shields.io/badge/ROOT-Data%20Analysis-3776AB?logo=cern&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-IA%20and%20Collision-EE4C2C?logo=pytorch&logoColor=white)
![ATLAS](https://img.shields.io/badge/ATLAS-Open%20Data-black)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)

## Description
This project explores **possible supersymmetric (SUSY) signatures** using **ATLAS Open Data** from the 2015–2016 Run 2 proton-proton collisions.  
We aim to identify **anomalous events** in the **2 jets + 2 leptons + MET** topology that may hint at **physics beyond the Standard Model**.

The analysis is divided into two main parts:  
1. **Data Analysis** — Extraction and computation of kinematic observables from ATLAS ROOT ntuples.  
2. **IA and Collision** — Application of an **Autoencoder neural network (PyTorch)** to detect rare or unexpected events.

---

## Objective
- Access and analyze ATLAS Run 2 open data (2015–2016).  
- Build a high-level kinematic feature dataset from ROOT files.  
- Use **unsupervised machine learning (Autoencoder)** to find anomalies that could correspond to **SUSY-like events**.  
- Visualize potential new physics candidates using standard collider observables.

---

## Dataset
**Source:** [ATLAS Open Data — Run 2 2015+2016 2J2LMET30 skim](https://opendata.cern.ch/record/93934)
*! Download all files from this link and copy into ATLAS data*

| Property | Description |
|-----------|--------------|
| Experiment | ATLAS |
| Data years | 2015–2016 |
| Center-of-mass energy | √s = 13 TeV |
| Selection | 2 jets, 2 leptons, MET > 30 GeV |
| Variables used | `m_ll`, `met`, `n_jets`, `n_bjets`, `ht`, `meff`, `dR_ll`, `j1_pt`, `j2_pt` |

Each event represents a reconstructed proton-proton collision consistent with **leptonic plus hadronic final states**, suitable for **SUSY searches** involving invisible particles.

---

## Methodology

### 🔹 Data Analysis (Physics Feature Construction)
1. **Load ROOT data** using `uproot` and `awkward` arrays.  
2. **Apply event selection:** 2 jets, 2 leptons, and missing transverse energy (MET > 30 GeV).  
3. **Compute derived variables:**
   - Invariant mass of leptons (`m_ll`)
   - Total transverse energy (`HT`)
   - Effective mass (`Meff`)
   - Angular separation (`ΔR_ll`)
   - Transverse mass (`mT_lep1`)
4. **Export dataset** as a CSV file for ML analysis.

### 🔹 IA and Collision (Anomaly Detection)
1. **Preprocessing:** scale features using `StandardScaler`.  
2. **Model:** Autoencoder (encoder-decoder) built in **PyTorch**.  
3. **Training:** minimize reconstruction error on normal events.  
4. **Evaluation:** compute reconstruction loss for all events.  
5. **Detection:** select top 1% highest-error events as **SUSY candidates**.  
6. **Visualization:** plot anomalies on `MET` vs `HT` and other kinematic planes.

---

## Results
- The Autoencoder successfully models the dominant Standard Model event topology.  
- Events with **high reconstruction error** correspond to **outliers** — candidates for **new physics**.  
- These events are saved in `susy_candidates.csv` for further physical inspection and hypothesis testing.

---S

## Acknowledgments
- **ATLAS Collaboration** for making the Run 2 Open Data available.  
- **CERN Open Data Portal** for open access and documentation.  
- Based on open research principles for **High-Energy Physics + Artificial Intelligence** integration.

---

## Author
Developed by **Amílcar Torres**, 2025  
Exploring **Supersymmetry and AI in Collider Physics**
