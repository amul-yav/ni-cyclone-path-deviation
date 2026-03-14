
# North Indian Ocean Cyclone Path Deviation Analysis

Statistical analysis of 330 cyclones (1982-2025).  
Key Finding: Warm SST anomalies correlate with 18% greater path deviations (Spearman ρ=0.15, p=0.02)

## Research Summary

Novel Contribution: Developed trajectory deviation metric measuring angle change between early (0-24h) and late (48-72h) cyclone motion vectors:

θ = cos⁻¹((v₁·v₂)/(|v₁||v₂|))

text

Primary Result: Cyclones over warm SST (>+0.5°C) exhibit 47.2° mean deviation vs 39.9° over cool SST.

## Complete Analysis Pipeline

data/ → code/01_load_filter.ipynb → code/02_deviation_metrics.ipynb → code/03_sst_analysis.ipynb

text

## Key Statistics (n=330 cyclones)
| Metric | Value |
|--------|-------|
| Mean deviation | 40.8° (SD=32.4°) |
| Median deviation | 35.2° |
| Maximum deviation | 180° (U-turns) |
| SST correlation | ρ=0.15 (p=0.02) |
| Warm SST deviation | 47.2° (n=142) |
| Cool SST deviation | 39.9° (n=32) |

## Data Sources
- ibtracs.NI.list.v04r01.csv - NOAA IBTrACS v4r01 (391 cyclones, 12,847 fixes)
- ni_imd_clean.csv - IMD agency tracks (Arabian Sea + Bay of Bengal)
- final_results.csv - Deviation + SST analysis results
- cyclone_deviations.csv - Track angle calculations
- final_cyclone_analysis.csv - Complete dataset

## ⚠️ Full Dataset Download
Complete IBTrACS data (>10MB): 
[NOAA IBTrACS v4r01](https://www.ncei.noaa.gov/data/international-best-track-archive-for-climate-stewardship-ibtracs/v04r01/access/csv-by-year/)

Notebooks auto-download full data on first run.

## Code Structure
code/
├── 01_load_filter.ipynb # IBTrACS parsing + NIO filtering (391 → 330 cyclones)
├── 02_deviation_metrics.ipynb # θ calculation (early vs late vectors)
└── 03_sst_analysis.ipynb # Spearman ρ=0.15 + SST stratification

text

## Paper
[NIO_CyclonePaths.pdf](NIO_CyclonePaths.pdf)  
7 citations | 3 figures | LaTeX formatted

## Method Validation
Data: IBTrACS v4r01 + NOAA OI.v2 SST (0.25° daily)  
Statistical test: Spearman rank correlation (non-parametric)  
Sample: 330 cyclones with complete 72h tracks  
Temporal range: 1982-2025 (43 years)

## Tech Stack
Language: Python 3.10  
Libraries: pandas, numpy, scipy.stats, matplotlib, cartopy  
Data: IBTrACS v4r01 (NOAA/NCEI), NOAA OI.v2 SST  
Document: LaTeX (Overleaf)

## Citation
Amulya V (2026). A Statistical Study of Tropical Cyclone Path Deviations in the North Indian Ocean. GitHub: ni-cyclone-path-deviation.

## Reproducibility
1. Open code/01_load_filter.ipynb
2. Run all cells sequentially (uses data/ibtracs.NI.list.v04r01.csv)
3. Analysis fully reproduces ρ=0.15 result
