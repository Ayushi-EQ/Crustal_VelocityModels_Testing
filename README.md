# Evaluation of 3D Crustal Seismic Velocity Models for Physics-Based Ground-Motion Simulation in New Zealand

This repository contains the intensity measures, residuals, and electronic supplements accompanying the paper:
**Evaluation of 3D crustal seismic velocity models for physics-based ground-motion simulation in New Zealand**  
Ayushi Tiwari, Brendon Bradley, Felipe Kuncar, and Dan Bassett  
*Earthquake Spectra* - manuscript submitted for publication.

The six crustal tomography models evaluated in the paper (EP10, EP20, EP25, B25, W25, and C22) are implemented in NZVM version 2.10.

# Repository Overview

The repository includes:

- Electronic Supplement B in CSV format

- Observed intensity measures (IMs)

- Simulated IMs from NZVM 2.10 for each of the six tomography models

- Residuals from Linear Mixed-Effects regression (MERA) for each of the six tomography models

## Repository structure

```text
Crustal_VelocityModels_Testing/
|
|-- Electronic_Supplements/
|   |-- Event_Information.csv
|   |-- Station_Information.csv
|
|-- IMs/
|   |-- Events.csv
|   |-- Stations.csv
|   |-- Observed_IMs.csv
|   |-- Simulated_IMs_EP10.csv
|   |-- Simulated_IMs_EP20.csv
|   |-- Simulated_IMs_EP25.csv
|   |-- Simulated_IMs_B25.csv
|   |-- Simulated_IMs_W25.csv
|   |-- Simulated_IMs_C22.csv
|
|-- Residuals/
|   |-- EP10/
|   |-- EP20/
|   |-- EP25/
|   |-- B25/
|   |-- W25/
|   |-- C22/
|
|-- LICENSE
|-- README.md
```

# Folder descriptions

## 1. Electronic_Supplements/

Contains Electronic Supplement B of the paper in CSV format.

- `Event_Information.csv`: Table B.1, the 28 events used in the analyses, with location, MW, depth, focal mechanism (strike, dip, rake), and the number of recording stations.
- `Station_Information.csv`: Table B.2, the 137 stations used, with location, basin and geomorphology classification, Vs30, T0, and the number of recorded events.

## 2. IMs/

Contains the observed and simulated intensity measures (IMs) used in the analyses. Each IM file has one row per ground motion, keyed by `gm_id`, `event_id`, and `stat_id`, followed by pSA and EAS across a range of periods and frequencies.

- `Observed_IMs.csv`: IMs for the 1510 observed ground motions.
- `Simulated_IMs_<model>.csv`: simulated IMs for each of the six tomography models.
- `Events.csv` and `Stations.csv`: metadata mapping `event_id` to the event name and `stat_id` to the station code.

## 3. Residuals/

Residuals from the Linear Mixed-Effects regression (MERA), computed separately for each tomography model. The six subfolders contain the same set of files:

- `bias_std_df.csv`: bias and standard-deviation components for all 84 IMs. The columns are the bias term (`bias`) and its standard error (`bias_std_err`), the between-event standard deviation (`tau`), the between-site (site-to-site) standard deviation (`phi_S2S`), the remaining within-event residual standard deviation (`phi_w`), and the total standard deviation (`sigma`, the root-sum-square of `tau`, `phi_S2S`, and `phi_w`).
- `event_res_df.csv`: between-event residuals.
- `event_cond_std_df.csv`: uncertainty in the point estimate of the between-event residuals (conditional standard deviation).
- `site_res_df.csv`: site-to-site residuals.
- `site_cond_std_df.csv`: uncertainty in the point estimate of the site-to-site residuals (conditional standard deviation).
- `rem_res_df.csv`: remaining within-event, within-site residuals for each ground motion.
- `fit_df.csv`: fitted values from the regression for each ground motion.
- `eas_support_per_frequency.csv`: number of records, events, and stations used at each EAS frequency.
- `run_summary.csv`: settings and number of records, events, and stations before the frequency-dependent selection criteria are applied.

## Citation

If you use this repository, please cite the accompanying paper:

```bibtex
@article{tiwari2026crustalmodels,
  title = {Evaluation of 3D crustal seismic velocity models for physics-based ground-motion simulation in New Zealand},
  author = {Tiwari, Ayushi and Bradley, Brendon and Kuncar, Felipe and Bassett, Dan},
  journal = {Earthquake Spectra},
  year = {2026},
  note = {Manuscript submitted for publication}
}
```

## License

This repository is released under the MIT License. See `LICENSE` for details.