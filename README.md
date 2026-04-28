# Pediatric Cancer Research Gap Analysis

### Do clinical trials align with survivor harm?

---

## Executive Summary

This project investigates whether pediatric cancer research activity aligns with survivor harm.

An initial analysis suggested a strong relationship between late-effects burden and trial outcomes. However, when the analysis was expanded using a larger dataset and improved methodology, this relationship disappeared.

> The key finding: apparent alignment between research activity and disease burden can emerge in partial datasets but does not persist at system scale.

---

## Core Insight

This project demonstrates:

```text
Initial signal → disappears under improved methodology
```

* Early result: **ρ = -0.806 (p = 0.005)**
* Full dataset: **ρ = 0.18 (p = 0.67)**

This shift reveals that the original finding was driven by dataset limitations rather than a true system-level relationship.

---

## Visual Analysis

### Figure 1 — Incidence vs Research Activity

![Scatter Plots](images/scatter_plots.png)

* Strong positive relationship between incidence and trial counts
* **ρ = +0.711 (p = 0.021)**

👉 Research scales with how common a disease is

---

### Figure 2 — Burden vs Research Activity

![Bubble Chart](images/bubble_chart.png)

* Strong negative relationship between burden and trial counts
* **ρ = -0.881 (p = 0.001)**

👉 High-burden diseases appear underrepresented in this dataset

---

### Figure 3 — Signal Collapse Under Improved Methodology

![Signal Collapse](images/signal_collapse.png)

| Analysis                          | Result                 |
| --------------------------------- | ---------------------- |
| Partial dataset (keyword mapping) | ρ = -0.806 (p = 0.005) |
| Full dataset (structured mapping) | ρ = 0.18 (p = 0.67)    |

This demonstrates that the initial signal does not hold when the full system is analyzed.

---

## Interpretation

The initial analysis suggested that diseases with higher survivor harm had lower trial failure rates.

However, deeper analysis shows:

* Research activity is primarily driven by **incidence**
* Survivor burden does **not consistently influence research activity**
* Apparent patterns can emerge from **incomplete or biased datasets**

> This highlights how misleading conclusions can arise without full data coverage and proper classification.

---

## Relationship to Source Repository

This project builds on:

**Where Pediatric Cancer Trials Stall**
https://github.com/DataInfamous/pediatric-cancer-stalled-trials

* Source repo: system-level analysis of trial discontinuation
* This repo: evaluates whether those patterns align with disease burden

---

## Methods

* Spearman correlation across disease groups
* ClinicalTrials.gov stalled trial dataset (~950 trials)
* Disease classification via keyword matching (initial analysis)
* Expanded analysis using structured condition mapping (~15k trials)

**Important Note:**
Stalled trial counts are used as a proxy for research activity due to consistent availability, but they do not represent total trial volume.

---

## Limitations

* Initial analysis categorized ~34% of trials
* Keyword-based disease mapping introduces bias
* Total trial counts derived from search queries
* Small sample size (n=10 disease categories)
* Temporal mismatch across datasets
* Observational data cannot establish causation

---

## Final Conclusion

This analysis shows:

```text
Research systems do not appear to be optimized around survivor harm
```

More importantly, it demonstrates:

```text
Methodology determines conclusions
```

---

## Future Work

* Re-run using full API-based condition mapping
* Incorporate total trial counts (not just stalled trials)
* Expand disease subtype resolution
* Integrate funding-level data

---

## Author

Benjamyn Wilson
DataInfamous

