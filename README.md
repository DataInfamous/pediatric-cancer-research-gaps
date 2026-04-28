# Pediatric Cancer Research Gap Analysis

### Does trial stall rate align with survivor harm?

---

## Executive Summary

This analysis examines whether pediatric cancer research activity aligns with survivor harm.

Initial results suggest a strong inverse relationship between late-effects burden and trial stall rates. However, deeper inspection shows that trial activity is primarily driven by disease incidence rather than long-term survivor outcomes.

High-burden, low-incidence cancers appear systematically underrepresented in clinical research activity.

---

## Overview

This analysis explores whether clinical trial stall rates in pediatric oncology align with disease burden, specifically late-effects mortality among survivors.

The goal is to test whether research outcomes reflect underlying clinical need, or whether observed patterns are driven by disease incidence and dataset structure.

This work represents an **early-stage, hypothesis-generating analysis** using a partially categorized dataset of stalled trials.

---

## Research Question

Do pediatric cancer diseases with higher late-effects burden show higher trial stall rates, or does stall rate primarily reflect disease incidence?

---

## Preliminary Finding

An initial analysis identified a strong negative correlation between non-recurrence mortality and trial stall rates:

* **ρ = -0.806**
* **p = 0.005**

Additional findings:

* Incidence vs stall rate: **ρ = +0.273, p = 0.446** (not significant)
* Burden index vs stall rate: **ρ = -0.624, p = 0.054** (borderline)

After normalization, the mortality signal remained while the incidence signal disappeared, indicating denominator-driven effects in raw counts.

---

## Interpretation (Refined)

While the initial interpretation suggested alignment between research persistence and disease severity, further inspection indicates a different structure:

> Research activity is primarily driven by disease incidence, not by survivor harm.

High-incidence diseases (e.g., ALL, CNS) dominate trial counts, while high-burden, low-incidence diseases (e.g., Ewing sarcoma, osteosarcoma) receive comparatively limited research activity.

---

## Visual Analysis

### Figure 1 — Incidence vs Stalled Trials and Burden vs Stalled Trials

![Scatter Plots](images/scatter_plots.png)

* **Left:** Stalled trials increase with incidence (**ρ = +0.711, p = 0.021**)
* **Right:** Stalled trials decrease with increasing burden (**ρ = -0.881, p = 0.001**)

These results indicate that research activity scales with how common a disease is rather than with long-term survivor harm.

---

### Figure 2 — Research Gap Visualization

![Bubble Chart](images/bubble_chart.png)

Bubble size represents stalled trial count.

* X-axis: Late-effects burden index
* Y-axis: Incidence rate

Key pattern:

* **Top-left (ALL, CNS):** High incidence, low burden → large research footprint
* **Bottom-right (Ewing, Osteosarcoma):** High burden, low incidence → limited research activity

> High-burden diseases are underrepresented relative to their clinical impact.

---

## Critical Context

This finding was derived from a **limited and partially categorized dataset**:

* ~950 stalled trials
* ~34% successfully categorized using title keywords
* Remaining ~66% excluded from disease-level analysis

This reflects patterns within **classifiable trials**, not the full system.

---

## Data Sources

| Source                | Description                                    | Coverage                 |
| --------------------- | ---------------------------------------------- | ------------------------ |
| CDC WONDER            | Age-adjusted incidence rates per million       | 1999–2022                |
| CCSS Mortality Tables | Non-recurrence cause-of-death % by cancer type | St. Jude Jan 2020 freeze |
| ClinicalTrials.gov    | ~950 stalled pediatric cancer trials           | 1995–present             |

---

## Key Results

| Cancer Type   | Incidence | Non-Recurrence Mortality | Total Trials | Stalled Trials | Stall Rate | Burden Index |
| ------------- | --------- | ------------------------ | ------------ | -------------- | ---------- | ------------ |
| Ewing         | 3.0       | 30.8                     | 158          | 7              | 4.4%       | 10.3         |
| Osteosarcoma  | 5.1       | 40.1                     | 204          | 9              | 4.4%       | 7.9          |
| Wilms         | 6.2       | 32.0                     | 101          | 3              | 3.0%       | 5.2          |
| Hodgkin       | 12.2      | 58.4                     | 343          | 9              | 2.6%       | 4.8          |
| AML           | 8.1       | 35.8                     | 607          | 26             | 4.3%       | 4.4          |
| NHL           | 11.9      | 43.5                     | 322          | 13             | 4.0%       | 3.7          |
| Neuroblastoma | 8.5       | 26.4                     | 279          | 29             | 10.4%      | 3.1          |
| STS           | 12.0      | 34.0                     | 178          | 14             | 7.9%       | 2.8          |
| ALL           | 33.8      | 28.0                     | 1260         | 89             | 7.1%       | 0.8          |
| CNS           | 31.3      | 21.8                     | 777          | 86             | 11.1%      | 0.7          |

---

## Correlation Results

| Comparison                 | Spearman rho | p-value | Significant |
| -------------------------- | ------------ | ------- | ----------- |
| Incidence vs stall rate    | +0.273       | 0.446   | No          |
| Mortality vs stall rate    | -0.806       | 0.005   | Yes         |
| Burden index vs stall rate | -0.624       | 0.054   | Borderline  |

---

## Methods

* Spearman correlation across **n = 10 disease groups**
* Stalled trials identified via ClinicalTrials.gov
* Disease classification via **title keyword matching**
* Total trial counts retrieved via search queries

**Note:**
Stalled trial counts are used as a proxy for research activity due to consistent availability across disease categories.

---

## Limitations

* ~66% of trials excluded due to classification limitations
* Keyword-based disease mapping introduces bias
* Total trial counts not derived from structured condition tags
* Small sample size (n=10)
* Temporal mismatch across datasets
* Visualizations based on stalled counts, not full trial dataset

---

## Relationship to Updated Analysis

A later full-pipeline analysis using:

* ~15,000 trials
* structured condition mapping
* consistent denominators
* temporal controls

found:

* **ρ = 0.18, p = 0.67**

This indicates that the strong negative correlation observed here does **not persist at system scale**.

---

## Final Interpretation

This analysis identifies a **potential signal**, but later work suggests:

> Apparent alignment between research activity and disease burden may emerge in partial datasets but does not hold when the full clinical trial system is analyzed.

---

## Future Work

* Re-run using ClinicalTrials.gov API condition tags
* Recover excluded trials
* Recalculate using full dataset
* Expand disease subtype mapping
* Validate burden relationship at scale

---

## Related Work

**Where Pediatric Cancer Trials Stall**
https://github.com/DataInfamous/pediatric-cancer-stalled-trials

---

## Author

Benjamyn Wilson
DataInfamous

