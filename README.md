# Pediatric Cancer Research Gap Analysis

### Does trial stall rate align with survivor harm?

---

## Overview

This analysis explores whether clinical trial stall rates in pediatric oncology align with disease burden, specifically late-effects mortality among survivors.

The goal is to test whether research outcomes reflect underlying clinical need, or whether observed patterns are driven by other factors such as disease incidence or dataset structure.

This work represents an **early-stage, hypothesis-generating analysis** using a partially categorized dataset of stalled trials.

---

## Research Question

Do pediatric cancer diseases with higher late-effects burden show higher trial stall rates, or does stall rate primarily reflect disease incidence?

---

## Preliminary Finding

An initial analysis identified a strong negative correlation between non-recurrence mortality and trial stall rates:

* **ρ = -0.806**
* **p = 0.005**

This suggests that diseases with higher survivor harm (i.e., higher non-recurrence mortality) were associated with **lower** stall rates.

Additional findings:

* Incidence vs stall rate: **ρ = +0.273, p = 0.446** (not significant)
* Burden index vs stall rate: **ρ = -0.624, p = 0.054** (borderline)

After normalizing by total trial counts, the mortality signal remained while the incidence signal disappeared, indicating that raw counts were influenced by denominator effects.

---

## Interpretation (Preliminary)

This result suggested a counterintuitive pattern:

> Diseases where survivors are more likely to die from treatment-related causes do not show proportionally higher rates of trial failure.

At face value, this could imply partial alignment between research persistence and disease severity.

---

## Critical Context

This finding was derived from a **limited and partially categorized dataset**:

* ~950 stalled trials
* Only ~34% could be mapped to disease categories using title keywords
* Total trial counts were retrieved separately via search queries

As a result, this analysis reflects patterns within a **subset of trials that could be easily classified**, rather than the full clinical trial system.

---

## Data Sources

| Source                | Description                                                 | Coverage                                         |
| --------------------- | ----------------------------------------------------------- | ------------------------------------------------ |
| CDC WONDER            | Age-adjusted incidence rates per million                    | 1999–2022                                        |
| CCSS Mortality Tables | Non-recurrence cause-of-death % by cancer type              | St. Jude Jan 2020 freeze, NDI through 12/31/2017 |
| ClinicalTrials.gov    | ~950 terminated/withdrawn/suspended pediatric cancer trials | 1995–present                                     |

---

## Key Results

| Cancer Type      | Incidence (per M) | Non-Recurrence Mortality (%) | Total Trials | Stalled Trials | Stall Rate | Burden Index |
| ---------------- | ----------------- | ---------------------------- | ------------ | -------------- | ---------- | ------------ |
| Ewing Sarcoma    | 3.0               | 30.8                         | 158          | 7              | 4.4%       | 10.3         |
| Osteosarcoma     | 5.1               | 40.1                         | 204          | 9              | 4.4%       | 7.9          |
| Wilms Tumor      | 6.2               | 32.0                         | 101          | 3              | 3.0%       | 5.2          |
| Hodgkin Lymphoma | 12.2              | 58.4                         | 343          | 9              | 2.6%       | 4.8          |
| AML              | 8.1               | 35.8                         | 607          | 26             | 4.3%       | 4.4          |
| NHL              | 11.9              | 43.5                         | 322          | 13             | 4.0%       | 3.7          |
| Neuroblastoma    | 8.5               | 26.4                         | 279          | 29             | 10.4%      | 3.1          |
| STS              | 12.0              | 34.0                         | 178          | 14             | 7.9%       | 2.8          |
| ALL              | 33.8              | 28.0                         | 1260         | 89             | 7.1%       | 0.8          |
| CNS              | 31.3              | 21.8                         | 777          | 86             | 11.1%      | 0.7          |

*Burden Index = non-recurrence mortality % / incidence rate*

---

## Correlation Results

| Comparison                             | Spearman rho | p-value | Significant |
| -------------------------------------- | ------------ | ------- | ----------- |
| Incidence vs stall rate                | +0.273       | 0.446   | No          |
| Non-recurrence mortality vs stall rate | -0.806       | 0.005   | Yes         |
| Burden index vs stall rate             | -0.624       | 0.054   | Borderline  |

---

## Methods

* Spearman rank correlation across **n = 10 disease categories**
* Stalled trials identified via ClinicalTrials.gov
* Disease classification based on **title keyword matching**
* Total trial counts retrieved via ClinicalTrials.gov search queries
* Stall rate calculated as:

```text
stall_rate = stalled_trials / total_trials
```

---

## Limitations

* Only ~34% of trials could be categorized using title keywords
* Remaining ~66% excluded from disease-level analysis
* Disease classification may be inconsistent or incomplete
* Total trial counts derived from search queries, not structured condition tags
* Small sample size (n=10 disease categories)
* Temporal mismatch across datasets (CCSS, CDC, trials)
* Visualizations based on raw counts rather than normalized rates

---

## Relationship to Updated Analysis

A subsequent full-pipeline analysis using:

* ~15,000 total trials
* structured condition mapping (API-based)
* consistent denominators
* temporal controls

found:

* **ρ = 0.18, p = 0.67**

This indicates that the strong negative correlation observed here does **not persist** when the full dataset is analyzed with improved methodology.

---

## Interpretation

This analysis successfully identified a **potential signal**, but later work suggests that:

> The observed relationship between disease burden and stall rates may reflect dataset limitations rather than a true system-level pattern.

---

## Future Work

* Re-run analysis using ClinicalTrials.gov API condition tags
* Recover uncategorized trials (~66%)
* Recalculate stall rates using full dataset
* Rebuild visualizations using normalized rates
* Expand disease subtype mapping
* Re-evaluate burden relationship with improved data coverage

---

## Related Work

This analysis builds on and feeds into:

**Where Pediatric Cancer Trials Stall**
https://github.com/DataInfamous/pediatric-cancer-stalled-trials

A full-system analysis examining structural drivers of trial discontinuation.

---

## Author

Benjamyn Wilson
DataInfamous
