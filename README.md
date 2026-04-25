# Pediatric Cancer Research Gap Analysis

### Does trial stall rate align with survivor harm?

**Research Question:**  
Do pediatric cancer diseases with higher late-effects burden have higher 
trial stall rates, or does stall rate primarily reflect disease incidence?

**Finding:**  
Diseases with higher non-recurrence mortality show lower trial stall rates 
(rho=-0.806, p=0.005). This finding held and strengthened after normalizing 
stalled trial counts by total trials per disease. The incidence correlation 
did not survive normalization (rho=+0.273, p=0.446), confirming the raw 
count signal was denominator-driven. The burden index correlation was 
borderline (rho=-0.624, p=0.054).

The finding that holds: diseases where survivors are more likely to die 
from treatment consequences than recurrence tend to have lower trial stall 
rates. This is a narrow but reproducible signal — diseases carrying the 
highest late-effects mortality burden are not seeing proportionally more 
trial activity fail.

---

## Data Sources

| Source | Description | Coverage |
|--------|-------------|----------|
| [CDC WONDER](https://wonder.cdc.gov/) | Age-adjusted incidence rates per million | 1999–2022 |
| [CCSS Mortality Tables](https://ccss.stjude.org/) | Non-recurrence cause-of-death % by cancer type | St. Jude Jan 2020 freeze, NDI through 12/31/2017 |
| [ClinicalTrials.gov](https://github.com/DataInfamous/pediatric-cancer-stalled-trials) | 950 terminated/withdrawn/suspended pediatric cancer trials | 1995–present |

---

## Key Results

| Cancer Type | Incidence (per M) | Non-Recurrence Mortality (%) | Total Trials | Stalled Trials | Stall Rate | Burden Index |
|-------------|-------------------|------------------------------|--------------|----------------|------------|--------------|
| Ewing Sarcoma | 3.0 | 30.8 | 158 | 7 | 4.4% | 10.3 |
| Osteosarcoma | 5.1 | 40.1 | 204 | 9 | 4.4% | 7.9 |
| Wilms Tumor | 6.2 | 32.0 | 101 | 3 | 3.0% | 5.2 |
| Hodgkin Lymphoma | 12.2 | 58.4 | 343 | 9 | 2.6% | 4.8 |
| AML | 8.1 | 35.8 | 607 | 26 | 4.3% | 4.4 |
| NHL | 11.9 | 43.5 | 322 | 13 | 4.0% | 3.7 |
| Neuroblastoma | 8.5 | 26.4 | 279 | 29 | 10.4% | 3.1 |
| STS | 12.0 | 34.0 | 178 | 14 | 7.9% | 2.8 |
| ALL | 33.8 | 28.0 | 1260 | 89 | 7.1% | 0.8 |
| CNS | 31.3 | 21.8 | 777 | 86 | 11.1% | 0.7 |

*Burden Index = non-recurrence mortality % / incidence rate*

**Stall Rate Correlations:**

| Comparison | Spearman rho | p-value | Significant |
|------------|--------------|---------|-------------|
| Incidence vs stall rate | +0.273 | 0.446 | No |
| Non-recurrence mortality vs stall rate | -0.806 | 0.005 | Yes |
| Burden index vs stall rate | -0.624 | 0.054 | Borderline |

---

## Visualizations

![Scatter Plots](images/scatter_plots.png)
![Bubble Chart](images/bubble_chart.png)

*Note: Visualizations reflect raw stalled trial counts. Updated 
visualizations using stall rate pending condition-tag categorization.*

---

## Methods

Three-variable correlation analysis using Spearman rank correlation (n=10 
disease categories). Stalled trials categorized from title keywords; 66% 
of 950 trials could not be categorized and are excluded. Total trial counts 
per disease retrieved from ClinicalTrials.gov search (April 2026) to 
calculate stall rates. Analysis conducted with AI assistance (Claude, 
Anthropic).

**Limitations:**
- Title-keyword categorization excludes 66% of trials; condition tag API 
  query would improve accuracy and is the primary next step
- Total trial counts retrieved via ClinicalTrials.gov search terms, not 
  condition tags — counts may include trials outside pediatric oncology 
  scope
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
- Assess burden index correlation at p=0.054 with larger categorized sample

---

## Related Work

The stalled trial counts​​​​​​​​​​​​​​​​
