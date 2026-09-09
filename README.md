[Read the full report](report/Breast_Cancer_Clinical_Trials_Australia_New_Zealand_Report.pdf) · [Open the reproducible notebook](analysis/Breast_Cancer_Clinical_Trials_Aus_NZ_Analysis.ipynb)
# Breast Cancer Clinical Trials in Australia and New Zealand

A reproducible, cross-sectional analysis of currently recruiting interventional breast cancer trials with confirmed recruiting locations in Australia or New Zealand.

**Prepared by:** Zohreh Riahi  
**Data retrieved:** 6 September 2026  
**Primary source:** [ClinicalTrials.gov API v2](https://clinicaltrials.gov/data-api/api)

## Project overview

This project uses the public ClinicalTrials.gov REST API v2 to identify and compare actively recruiting interventional breast cancer trials in Australia and New Zealand. The workflow retrieves JSON study records, validates country locations, separates trial-level and site-level data, and summarises geographic distribution, trial phase, lead sponsor class, intervention types and population-adjusted recruitment activity.

The analysis is a dated registry snapshot. It describes registered trial activity, not treatment effectiveness, patient enrolment or guaranteed access.

## Key findings

- 88 unique interventional trials had at least one confirmed recruiting site in Australia or New Zealand.
- Australia participated in 87 trials and New Zealand in 8; 7 trials recruited in both countries.
- Australia recorded 363 recruiting study-location records, compared with 14 in New Zealand.
- Population-adjusted activity remained higher in Australia: 3.15 trials and 13.15 site records per million residents, versus 1.50 trials and 2.63 site records per million in New Zealand.
- Phase 3 trials represented 62.5% of New Zealand's smaller portfolio and 26.4% of Australia's portfolio.
- Industry was the lead sponsor for 89.7% of Australian trials and 87.5% of New Zealand trials.
- Recruitment was geographically concentrated: New South Wales and Victoria accounted for 65.6% of Australian site records, while Auckland Region accounted for 57.1% of New Zealand site records.

## Study selection

| Stage | Studies retained | Excluded at stage |
|---|---:|---:|
| Initial API search | 500 | 0 |
| Confirmed Australia or New Zealand location | 499 | 1 |
| Recruiting or not yet recruiting | 113 | 386 |
| Regional site recruiting or upcoming | 97 | 16 |
| Interventional only | 91 | 6 |
| Currently recruiting regional site | 88 | 3 |

## Repository contents

- `BC Clinical.ipynb` - reproducible Python notebook for API extraction, data preparation, validation, analysis and visualisation
- `FINAL-Breast_Cancer_Clinical_Trials_Australia_New_Zealand_Report.pdf` - 16-page public report
- `Interactive_Map_Breast_Cancer_Recruiting_Trials_Australia_New_Zealand_2026-09-06.html` - interactive city-level map
- `data/` - trial-level and site-level CSV datasets
- `tables/` - exported analytical summary tables
- `figures/` - report-ready charts and map image

## Methods summary

The analysis was completed in Python using `requests`, `pandas`, `matplotlib` and `folium`.

1. Retrieve studies from ClinicalTrials.gov API v2 using the condition `Breast Cancer` and locations `Australia OR New Zealand`.
2. Validate country names against registered study locations.
3. Retain interventional studies with an overall status of `Recruiting` and at least one regional site whose site-level status is `Recruiting`.
4. Separate unique trial records from study-location records to avoid mixing study counts with site counts.
5. Standardise geographic labels, trial phases, sponsor classes and intervention names.
6. Produce country, state or region, phase, sponsor and intervention summaries.
7. Calculate descriptive rates per million residents using official population estimates for 30 June 2025.

## Interactive map

Open the [interactive city-level trial map](https://zohreh61riahi-a11y.github.io/breast-cancer-clinical-trials-australia-new-zealand/Interactive_Map_Breast_Cancer_Recruiting_Trials_Australia_New_Zealand_2026-09-06.html) to explore registered recruiting locations, facility labels and linked ClinicalTrials.gov records.

The map covers 97 city labels: 90 in Australia and 7 in New Zealand. Coordinates are intended for geographic visualisation rather than clinical navigation.

## Data files

The main exported datasets are:

- `Breast_Cancer_Currently_Recruiting_Trials_Aus_NZ_2026-09-06.csv` - 88 unique trials
- `Breast_Cancer_Currently_Recruiting_Sites_Aus_NZ_2026-09-06.csv` - 377 recruiting study-location records
- `Breast_Cancer_Open_Interventional_Trials_Aus_NZ.csv` - 91 open interventional trials
- `Breast_Cancer_Open_Trial_Sites_Aus_NZ.csv` - 395 study-location records

## Important limitations

- Recruitment status and site listings may change after the retrieval date.
- ClinicalTrials.gov is not the only registry used in Australia and New Zealand; trials registered exclusively elsewhere may be absent.
- Some multi-tumour studies may include breast cancer as only one eligible cancer type.
- A site record is one study-location record and is not necessarily a unique hospital.
- Country-linked trial counts overlap when the same trial recruits in both countries.
- Population-adjusted rates are descriptive and are not adjusted for breast cancer incidence, eligible patient numbers, travel distance or actual enrolment.

## Population sources

- [Australian Bureau of Statistics - National, state and territory population, June 2025](https://www.abs.gov.au/statistics/people/population/national-state-and-territory-population/jun-2025)
- [Stats NZ - National population estimates at 30 June 2025](https://www.stats.govt.nz/information-releases/national-population-estimates-at-30-june-2025/)

## Reuse and attribution

Independent analysis, data preparation, tables and interpretation by Zohreh Riahi. ClinicalTrials.gov registry records remain subject to the source's terms and may change after the retrieval date.

Suggested attribution:

> Riahi, Z. (2026). Breast Cancer Clinical Trials in Australia and New Zealand: A cross-sectional analysis of currently recruiting trials using ClinicalTrials.gov API v2. Data retrieved 6 September 2026.
