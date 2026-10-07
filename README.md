# Dengue surveillance season-window reproducibility package

Public aggregate monthly surveillance and analytical code for the October 2026 revision.
The downloadable ZIP expands to a `dengue-enso/` directory. It contains frozen China
windows, global unit-month data, assigned temperatures, computed windows/trends/power,
review sensitivities, analytical/plotting scripts, geographical inputs, and checksums.
No individual patient records or manuscript/declaration drafts are included.

## Reproduce

Use Python 3.14 and install `requirements.txt`. From the extracted `dengue-enso/`:

```sh
python scripts/global_window_extraction.py --validate
python scripts/revision_analyses.py
python scripts/make_zemin_figures.py
```

Existing primary result CSVs are supplied to reproduce the figures without repeating
downloads or expensive simulations. To recompute analytical layers, run
`global_trend_analysis.py`, `global_detectability.py`, `global_meta_analysis.py`,
`global_intensity_timing.py`, and `global_loo_country.py` in that order after extracting
the global windows. Preserve the frozen `data/processed/windows.csv` anchor.
The `--validate` switch validates and returns without overwriting the frozen China file.

## Provenance and reuse

- OpenDengue V1.3: https://doi.org/10.6084/m9.figshare.24259573
  and https://github.com/OpenDengue/master-repo (aggregate counts; retain original attribution/licence).
- NASA POWER: https://power.larc.nasa.gov/ (assigned-city monthly temperatures).
- ERA5 through Open-Meteo: https://open-meteo.com/ and https://cds.climate.copernicus.eu/
  (China eight-city series; retain provider terms).
- Natural Earth: https://www.naturalearthdata.com/ (public-domain geographical data).
- China full-territory boundaries: Alibaba DataV, https://datav.aliyun.com/portal/school/atlas/area_selector
  (source attribution and provider terms apply; the geographical input is not relabelled as project-owned).
- Original full databases and large remote raw archives are not bundled. The processed
  unit-month and temperature inputs needed by the analyses are supplied.
- Original administrative country codes remain unchanged in source CSVs for reproducibility;
  manuscript displays use countries and territories, including Taiwan, China; Hong Kong SAR, China;
  and Macao, China. Geographic assignment and shared sites do not imply independent units.

## Interpretation

The long-record estimate is concentrated in Thailand and Nicaragua. Reported-case
calendar windows differ from continuous local transmission. MDS80 assumes independent
Gaussian noise and constant future variability. Additional-year medians exclude units
not reaching the reference target within the 60-year horizon. Country-cluster intervals
with five/two clusters are fragile; circular sensitivity and nominal unadjusted tests
must be read with the accompanying result tables. Temperature associations do not
establish causal warming attribution. See `results/revision_*.csv`.

SHA256SUMS lists every archived input/script. An immutable commit link is recorded in
the local project publication record after upload. Third-party inputs retain their own
licences; no new licence for those inputs is implied by this repository.
