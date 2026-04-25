# Pediatric Cancer Research Gap Analysis

### Does trial stall rate align with survivor harm?

**Research Question:**  
Do pediatric cancer diseases with higher late-effects burden have higher 
trial stall rates, or does stall rate primarily reflect disease incidence?

**Finding:**  
Diseases with higher non-recurrence mortality show lower trial stall rates 
(rho=-0.697, p=0.025). The incidence correlation from raw stalled trial 
counts does not survive normalization — confirming it was denominator-driven, 
not a signal of research misalignment. The burden index correlation also did 
not survive normalization (rho=-0.406, p=0.244).

The one finding that holds: diseases where survivors are more likely to die 
from treatment consequences than recurrence tend to have lower trial stall 
rates. This is a narrow but reproducible signal in a small dataset.

---

## Data Sources

| Source | Description | Coverage |
|--------|-------------|----------|
| [CDC WONDER](https://wonder.cdc.gov/) | Age-adjusted incidence rates per million | 1999–2022 |
| [CCSS Mortality Tables](https://ccss.stjude.org/) | Non-recurrence cause-of-death % by cancer type | St. Jude Jan 2020 freeze, NDI through 12/31/2017 |
| [ClinicalTrials.gov](https://github.com/DataInfamous/pediatric-cancer-stalled-trials) | 950 terminated/withdrawn/suspended pediatric cancer trials | 1995–present |

---

## Key Results

| Cancer Type | Incidence (per M) | Non-Recurrence Mortality (%) | Stalled Trials | Burden Index |
|-------------|-------------------|------------------------------|----------------|--------------|
| Ewing Sarcoma | 3.0 | 30.8 | 7 | 10.3 |
| Osteosarcoma | 5.1 | 40.1 | 9 | 7.9 |
| Wilms Tumor | 6.2 | 32.0 | 3 | 5.2 |
| Hodgkin Lymphoma | 12.2 | 58.4 | 9 | 4.8 |
| ALL | 33.8 | 28.0 | 89 | 0.8 |
| CNS | 31.3 | 21.8 | 86 | 0.7 |

*Burden Index = non-recurrence mortality % / incidence rate*

**Stall Rate Correlations (stalled / total trials per disease):**

| Comparison | Spearman rho | p-value | Significant |
|------------|--------------|---------|-------------|
| Incidence vs stall rate | +0.164 | 0.651 | No |
| Non-recurrence mortality vs stall rate | -0.697 | 0.025 | Yes |
| Burden index vs stall rate | -0.406 | 0.244 | No |

---

## Visualizations

![Scatter Plots](images/scatter_plots.png)
![Bubble Chart](images/bubble_chart.png)

*Note: Visualizations reflect raw stalled trial counts, not stall rates. 
Updated visualizations pending condition-tag categorization.*

---

## Methods

Three-variable correlation analysis using Spearman rank correlation (n=10 
disease categories). Stalled trials categorized from title keywords; 66% 
of 950 trials could not be categorized and are excluded. Total trial counts 
per disease retrieved from ClinicalTrials.gov API v2 to calculate stall 
rates. Analysis conducted with AI assistance (Claude, Anthropic).

**Limitations:**
- Title-keyword categorization excludes 66% of trials; condition tag API 
  query would improve accuracy and is the primary next step
- Initial raw-count correlations were denominator-driven and do not reflect 
  genuine research misalignment — stall rate is the appropriate metric
- CCSS aggregate tables only; individual-level data requires AOI submission
- n=10 categories is small for correlation analysis; results should be 
  interpreted cautiously
- Temporal mismatch: CCSS through 2017, CDC WONDER through 2022, trials 
  1995–present
- Visualizations reflect raw counts pending updated analysis

---

## Future Work

- Re-run using ClinicalTrials.gov API condition tags rather than title 
  keywords to recover the 66% of uncategorized trials
- Rebuild visualizations using stall rate rather than raw counts
- Assess whether non-recurrence mortality signal strengthens with improved 
  categorization

---

## Related Work

The stalled trial counts used here are derived from 
[pediatric-cancer-stalled-trials](https://github.com/DataInfamous/pediatric-cancer-stalled-trials), 
which characterizes 950 terminated, withdrawn, and suspended pediatric 
cancer trials across 89 countries — including geographic distribution, 
sponsor type, and reason for stopping.

---

## Citation

Wilson, B. (2026). *Pediatric Cancer Research Gap Analysis: CDC WONDER 
Incidence × CCSS Late-Effects Mortality × ClinicalTrials.gov Stalled 
Trials.* GitHub. https://github.com/DataInfamous/pediatric-cancer-research-gaps

**Data Sources:**
- United States Cancer Statistics - Incidence: 1999–2022, WONDER Online 
  Database. CDC/NCI; 2025 release.
- Childhood Cancer Survivor Study (CCSS). St. Jude Children's Research 
  Hospital. Jan 2020 data freeze, NDI through 12/31/2017.
- ClinicalTrials.gov API v2. U.S. National Library of Medicine.

---

*Author: Benjamyn Wilson | [DataInfamous](https://github.com/DataInfamous)*
