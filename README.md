# DoubleBetaDecay_Data

A reference dataset repository containing theoretical spectra for double beta decay processes in the closure approximation.

## Overview

This repository provides CSV data files for double beta decay calculations for three isotopes:
- **⁷⁶Ge** (Germanium-76)
- **¹³⁰Te** (Tellurium-130)
- **¹³⁶Xe** (Xenon-136)

Each isotope has data for two decay modes, transitions from ground state to ground state:
- **0nu** (neutrinoless double beta decay)
- **2nu** (two-neutrino double beta decay)

## Repository Structure

```
DoubleBetaDecay_Data/
├── README.md
├── LICENSE
└── data/
    ├── 76Ge_0nu_2betaMinus.csv
    ├── 76Ge_2nu_2betaMinus.csv
    ├── 130Te_0nu_2betaMinus.csv
    ├── 130Te_2nu_2betaMinus.csv
    ├── 136Xe_0nu_2betaMinus.csv
    └── 136Xe_2nu_2betaMinus.csv
```

## Data Format

All CSV files contain 501 data points (indexed 0-500) with consistent formatting:

### Neutrinoless Decay (0nu) Files
Contains 5 columns:
1. **Index** - Row index (0-500)
2. **Energy** - Electron kinetic energy values in MeV (starting from 1e-05).
3. **dG/de1** - Single electron energy spectrum. Normalized to unit integral.
4. **dH/de1** - Single electron energy spectrum. Normalized to unit integral.
5. **alpha** - Angular correlation spectrum.

### Two-Neutrino Decay (2nu) Files
Contains 6 columns:
1. **Index** - Row index (0-500)
2. **Energy** - Electron kinetic energy values in MeV (starting from 1e-05)
3. **dG/de1** - Single electron energy spectrum. Normalized to unit integral.
4. **dG/dT** - Summed electron energy spectrum. Normalized to unit integral.
5. **dH/de1** - Single electron energy spectrum. Normalized to unit integral.
6. **alpha** - Angular correlation spectrum

**Important:** The `dG/dT` column only appears in 2nu files and is positioned between `dG/de1` and `dH/de1`.

## Usage Examples

### Python

```python
import pandas as pd

# Load neutrinoless decay data for Germanium-76
df_0nu = pd.read_csv('data/76Ge_0nu_2betaMinus.csv', index_col=0)

# Load two-neutrino decay data for Tellurium-130
df_2nu = pd.read_csv('data/130Te_2nu_2betaMinus.csv', index_col=0)

# Access specific columns
energy = df_0nu['Energy']
dg_de1 = df_0nu['dG/de1']

# Plot data
import matplotlib.pyplot as plt
plt.plot(df_0nu['Energy'], df_0nu['dG/de1'])
plt.xlabel('Energy (MeV)')
plt.ylabel('dG/de1')
plt.xscale('log')
plt.show()
```


## Citation

If you use this data in your research, please cite accordingly and ensure proper attribution to the original data sources.

## License

See [LICENSE](LICENSE) file for details.

## Contact

For questions, issues, or contributions, please open an issue on the repository.
