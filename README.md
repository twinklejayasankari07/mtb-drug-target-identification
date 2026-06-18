# MTB Drug Target Identification Pipeline

## Overview
A computational pipeline for identifying the potential drug targets in Mycobacterium Tuberculosis (H37RV strain) using comparative genomics, structure prediction and druggability scoring.

## Background
Tuberculosis continues to be a major health challenge in India, with the highest multi-drug resistant (MDR-TB) cases globally. This project identifies proteins unique to MTB that are absent in humans — making them safer and more selective drug targets.

## Methodology
1. **Data collection**
   - Downloaded MTB H37Rv reference proteome (3,980 proteins) from UniProt
   - Downloaded complete human proteome (147,506 proteins) from UniProt
2. **Comparitive genomics (BLAST analysis)**
   - BLASTP was used to compare all MTB proteins against the human proteome
   - Filtered proteins with E-value > 0.001 (non-homologous to humans)
   - Identified 2,162 unique candidate proteins
3. **Structure prediction**
   - Selected top 20 candidates by highest E-value
   - Downloaded AlphaFold-predicted 3D structures
   - Visualized structures using py3Dmol
4. **Druggability scoring**
   - Hydrophobicity score and instability index were calculated
   - All scores were normalized to a 0-1 scale
   - Combined final score was calculated by integrating:
      - E-value: 50%
      - Hydrophobicity: 30%
      - Instability: 20%
   
## Results
Top 5 Drug Target Candidates:

| Rank | Protein ID |                Name                | Score |
|------|------------|------------------------------------|-------|
| 1    | P95218     | Nitrite extrusion protein          | 0.93  |
| 2    | Q11064     | Probable acyltransferase           | 0.91  |
| 3    | P9WM71     | Uncharacterized protein Rv0090     | 0.85  |
| 4    | I6WZ71     | D-3-phosphoglycerate dehydrogenase | 0.82  |
| 5    | P96238     | Transcriptional regulatory protein | 0.82  |

## Tools & Technologies
- Python, Pandas, NumPy
- Biopython
- NCBI BLAST+
- AlphaFold Database
- py3Dmol

## Repository Structure
notebooks/
├── 01_data_loading.ipynb
├── 02_blast_analysis.ipynb
├── 03_structure_prediction.ipynb
└── 04_druggability_scoring.ipynb
results/
├── FINAL_drug_targets.csv
└── structures/ (20 PDB files)

## How to Run
1. Open notebooks in Google Colab
2. Mount Google Drive
3. Run cells sequentially from 01 to 04

## Limitations & Future Work
- Druggability scoring used sequence-based properties as a proxy due to fpocket installation constraints in cloud environments.
- Future work could include pocket-based druggability analysis and molecular docking simulations.

## Author
Twinkle Jayasankari S — B.Tech Bioinformatics, SASTRA DEEMED UNIVERSITY
   
