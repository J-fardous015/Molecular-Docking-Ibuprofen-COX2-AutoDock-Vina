# Molecular Docking of Ibuprofen into COX-2(PDB: 1COX2)

>Ibuprofen docked into the COX-2 active site using AutoDock Vina, shows a best binding affinity of −7.572 kcal/mol, which is in the published COX-2 inhibitor range (-6.5 to -8.0 kcal/mol)


![Python](https://img.shields.io/badge/Python-3.10-blue)
![AutoDock Vina](https://img.shields.io/badge/AutoDock_Vina-1.2.5-green)
![RDKit](https://img.shields.io/badge/RDKit-2024.09-red)
![Platform](https://img.shields.io/badge/Platform-Google_Colab-yellow)

---
## Overview

COX-2 or Cyclooxygenase is a well validated inflammatory pain target, and Ibuprofen is from a common NSAID group. This is a computational simulation project demonstrate how Ibuprofen bind in the COX-2 active site by suing a structured base molecular docking. The protein crystal structure of COX-2 co-crystallized with SC-558 inhibitor, consider as a binding pocket or active site. COX-2 was collected from protein databank as a PDB formate, later converted to PDBQT format using RDKit, Meeko, Vina etc tools. For Ibuprofen, SMILES was collected, converted it in a SDF file, then in a PDBQT format. Target and protein docked using AutoDock Vina, results shown a best pose of binding affinity of −7.572 kcal/mol out of 10 considered pose.  



---
## Background

Cyclooxygenase, a natural enzym present in our human body. COX-2 reamins inactive in general state, activate when any injury or inflammation occured in the body. It produce prostaglandins molecules which sends chemical signal to the brain, that are responsible for pain or inflammation response in the body. Ibuprofen is a well known COX-2 inhibitor from NSAID (Non-Steroidal Anti-Inflammatory Drug) group. Ibuprofen binds in COX-2 active site, and exerts its anti-inflammatory effects by blocking it. This projects demonstrate the complete docking pipeline of Ibuprofen in COX-2 active site from a raw PDB structure to a 3D binding pose visulaization . 

---

## Protein and Ligand




