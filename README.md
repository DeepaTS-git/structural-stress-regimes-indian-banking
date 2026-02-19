# Structural Stress Regimes in Indian Banking (1996–2023)
### A Change-Point Analysis of Asset Quality & Loss Absorption

### Problem Statement

Non-Performing Assets (NPAs) are a key indicator of banking system stability.
Persistent increases in NPAs reduce lending capacity and may signal systemic stress.

This project examines long-term trends in Gross and Net NPAs across major Indian bank groups (1996–2023) and applies statistical change-point detection to identify structural shifts in asset quality regimes.

### Dataset Source

**Source:** Reserve Bank of India (RBI) – Database on Indian Economy (DBIE)

**Dataset:** Gross and Net NPAs of Scheduled Commercial Banks – Bank Group-Wise

**Path:**
Home → Statistics → Financial Sector → Banking – Performance Indicators

**Time Period:** 1996–2023

**Frequency:** Annual

### Data Preparation

RBI datasets are authoritative but structurally complex.
The raw Excel file contains:

- Multiple vertically stacked tables
- Multi-row hierarchical headers
- Footer notes embedded in the sheet
- Blank separator rows
- Uneven time coverage across some bank groups

Data was cleaned and standardized into a unified time-series dataset suitable for comparative and structural analysis.

**Final dataset:**

- 135 observations
- 6 bank categories
- No missing values in final structured data
- All numeric fields properly formatted

### Methodology

System stress is analyzed through:

- Gross NPAs → Indicator of structural credit stress

- Net NPAs → Indicator of provisioning strength and loss absorption

**Change-Point Detection**

Traditional trend analysis shows gradual movement but may not detect statistically significant regime shifts.
To identify structural breaks, this project applies:

- Algorithm: PELT (Pruned Exact Linear Time)
- Cost Model: Radial Basis Function (RBF)
- Penalty Parameter: 3

The penalty was selected as the smallest value that produced stable and interpretable breakpoints without overfitting.

### Tech Stack

- Python
- pandas
- numpy
- matplotlib
- ruptures (change-point detection)

### Structural Break Results
| Bank Group    | Gross NPA Break Point | Net NPA Break Point | Interpretation |
|:--------------|------------:|----------:|:----------------------------|
| Public Sector Banks | 2000 | 2000 | Structural reset in asset quality |
| Private Banks | None | 2005 | Provisioning discipline improved |
| Foreign Banks | 2000 | 2010 | Global-cycle sensitivity |

### Key Findings
**Public Sector Banks**

- Structural break detected in 2000 for both Gross and Net NPAs.
- Indicates a shift in long-term asset quality behavior.
- Later stress episodes appear cyclical rather than structural.

**Private Sector Banks**

- No structural break in Gross NPAs.
- Break detected in Net NPAs in 2005.
- Suggests improvement in provisioning discipline without a structural change in underlying credit regime.

**Foreign Banks**

- Structural break in Gross NPAs around 2000.
- Break in Net NPAs around 2010.
- Indicates changes in asset quality and provisioning behavior over time.

### Key Insights

- Ownership structure influences long-term asset quality behavior.
- Public Sector Banks exhibit higher volatility and identifiable structural regime shifts.
- Private Sector Banks show provisioning improvement without structural credit regime change.
- The 2015–2018 NPA surge does not qualify as a permanent structural regime shift under the selected model specification.
- Change-point detection complements traditional financial ratio analysis by identifying statistically validated regime transitions.

### Limitations

- Annual frequency limits detection of short-term stress regimes.
- Breakpoint detection depends on penalty parameter selection.
- Structural breaks indicate statistical shifts, not causation.
- Interpretation should be combined with economic context.

### How to Run?

1. Clone the repository
2. Install dependencies
```bash
   pip install -r requirements.txt
```
3. Open and run the notebook:
```bash
notebooks/final.ipynb
```
5. The notebook performs:

- Cleaning and restructuring of RBI tables with hierarchical headers
- Trend and volatility analysis across bank groups
- Structural break detection using the PELT algorithm
- Visualization of detected regime shifts
