# Molecular Docking of Ibuprofen into COX-2(PDB: 1COX2)

>Ibuprofen docked into the COX-2 active site using AutoDock Vina, shows a best binding affinity of −7.572 kcal/mol, which is in the published COX-2 inhibitor range (-6.5 to -8.0 kcal/mol)


![Python](https://img.shields.io/badge/Python-3.10-blue)
![AutoDock Vina](https://img.shields.io/badge/AutoDock_Vina-1.2.5-green)
![RDKit](https://img.shields.io/badge/RDKit-2024.09-red)
![PyMol](https://img.shields.io/badge/PyMOL-3.1.8-purple)
![Platform](https://img.shields.io/badge/Platform-Google_Colab-yellow)

---
## Overview

COX-2 or Cyclooxygenase is a well validated inflammatory pain target, and Ibuprofen is from a common NSAID group. This is a computational simulation project demonstrate how Ibuprofen bind in the COX-2 active site by suing a structured base molecular docking. The protein crystal structure of COX-2 co-crystallized with SC-558 inhibitor, consider as a binding pocket or active site. COX-2 was collected from protein databank as a PDB formate, later converted to PDBQT format using RDKit, Meeko, Vina etc tools. For Ibuprofen, SMILES was collected, converted it in a SDF file, then in a PDBQT format. Target and protein docked using AutoDock Vina, results shown a best pose of binding affinity of −7.572 kcal/mol out of 10 considered pose.  



---
## Background

Cyclooxygenase, a natural enzym present in our human body. COX-2 reamins inactive in general state, activate when any injury or inflammation occured in the body. It produce prostaglandins molecules which sends chemical signal to the brain, that are responsible for pain or inflammation response in the body. Ibuprofen is a well known COX-2 inhibitor from NSAID (Non-Steroidal Anti-Inflammatory Drug) group. Ibuprofen binds in COX-2 active site, and exerts its anti-inflammatory effects by blocking it. This projects demonstrate the complete docking pipeline of Ibuprofen in COX-2 active site from a raw PDB structure to a 3D binding pose visulaization . 

---

## Protein and Ligand

| Property | Details |
|---|---|
| Target protein | Cyclooxygenase-2 (COX-2) |
| Organism | *Mus musculus* (mouse) |
| PDB ID | [1CX2](https://www.rcsb.org/structure/1CX2) |
|Co-crystallised ligand | SC-558 (residue: S58) |
| Ligand tested | Ibuprofen |
| Ibuprofen SMILES | `CC(C)CC1=CC=C(C=C1)C(C)C(=O)O` |


---

##  Method

### 1. Protein Preparation
- Protein (`1CX2`) downloaded from RCSB PDB
- Remove water molecules (`HOH`), Heme group or hetero atom (`HEM`), Inhibitore (`S58`), crystallographic artifacts(`SO4, NAG`) using PDB purser
- Added missing residues, fixed non-standard residues, and added hydrogen at 7.4 pH using 
**PDBFixer**
- PDB file converted to PDBQT using **OpenBable** with Gasteiger mathematical charge calculation method



### 2. Ligand Preparation
- SMILES collected from PubChem
- SMILES converted to MOL using **RDKit**
`Chem.MolFromSmiles(simles)`
- Added Hydrogen atom `Chem.AddHs(mol)`
- Generated 3D coordinates `AllChem.EmbedMolecule, randomSeed = 42`
- Optimized the 3D shape using Merck Molecular Force Field (MMFF) `AllChem.MMFFOptimizeMolecule`
- MOL converted to PDBQT formate with partial charges, and AutoDock atom types using **Meeko**

### 3. Search Box Define
- SDF file of small molecule `S58` downloaded from RCSB Instance Coordinates
- Opened in **PyMOL**, used command `get_position` for coordinates, results `[ 24.263, 21.528, 16.497]`
- Used `get_extent`for coordinate span, results `min: [ 18.483, 18.488, 10.836], max: [ 29.412, 24.676, 20.036]`.
- Search box set to **25×25×25 Å** to provide sufficient conformational sampling space

### 4. Docking 
- Docking ran in **AutoDock Vina** with `exhaustiveness = 10`, `num_modes = 10`. 
- Scoring function: combines four physical forces;Vander Waals, Hydrogen Bonds, Electrostatic, and Hydrophobic

### 5. Visualization
- Docking result loaded in **PyMOL**
- Binding site residues selected within 3.5 Å of ligand (54 atoms)
- Used `distance` command for measuring Hydrogen bond distances

