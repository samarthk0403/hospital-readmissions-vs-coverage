# Hospital Readmissions vs. Insurance Coverage

BA780 Intro to Data Analytics, Boston University (MSBA), Fall 2026. Cohort A, Team 02.

## Business question
Should a State Medicaid agency or hospital association fund coverage expansion to cut 30-day hospital readmissions and the CMS penalties tied to them, or put that money into care-transition programs?

We test whether states with more uninsured residents, and states that did not expand Medicaid, show worse readmission results, across 52 geographies.

## Key findings
- **Uninsured rate is not linked to a state's readmission gap** (r = -0.11, 95% CI [-0.37, +0.17]; r = -0.08 without Puerto Rico).
- **Expansion and non-expansion states have almost identical readmission gaps** (difference -0.01 percentage points, Cohen's d = -0.07, p = 0.40), even though expansion does lower uninsured rates (6.72% vs. 9.96%, d = -1.41).
- **State gaps span only 1.20 percentage points**, while uninsured rates differ 6.2-fold (Massachusetts 2.69% vs. Texas 16.56%).
- **Gaps are consistent within a state** (average r = +0.61 across medical conditions), which is where care-transition programs would be aimed.
- **One association held up:** a larger Medicaid share goes with higher gaps (r = +0.45, Holm p = 0.0014), but Puerto Rico drives much of it (r = +0.25 without it), and Medicaid share may mainly reflect poverty.

## Recommendation
Judge coverage expansion on access and financial protection grounds, not as a readmission program. To reduce readmissions, consider care-transition programs (discharge planning, follow-up calls, medication reconciliation) aimed at states with persistently above-national gaps. We did not test those programs; the recommendation rests on the absence of a coverage effect and on published evidence cited in the notebook.

## Data
| Dataset | Publisher |
|---|---|
| [Unplanned Hospital Visits, Hospital](https://data.cms.gov/provider-data/dataset/632h-zaca) | CMS Provider Data Catalog |
| [Unplanned Hospital Visits, State](https://data.cms.gov/provider-data/dataset/4gkm-5ypv) | CMS Provider Data Catalog |
| [Health Insurance Coverage of the Total Population, 2022-2024](https://www.kff.org/state-health-policy-data/state-indicator/total-population/) | KFF State Health Facts |
| [Status of State Medicaid Expansion Decisions](https://www.kff.org/status-of-state-medicaid-expansion-decisions/) | KFF |
| [Status of State Action on the Medicaid Expansion Decision](https://www.kff.org/affordable-care-act/state-indicator/state-activity-around-expanding-medicaid-under-the-affordable-care-act/) | KFF State Health Facts |

CMS data are U.S. government public data. KFF data are used under KFF's terms of use with attribution.

## Method
14,701 usable CMS hospital-condition records (Jul 2023 to Jun 2025), each compared with the national median for the same condition, summarized by state and joined to KFF coverage (2023-2024 average). Correlations, t-tests with effect sizes, Holm correction for secondary tests, and one exploratory regression. Decision rules were fixed before the final run. Built in Python (pandas, SciPy, statsmodels, matplotlib, seaborn).

## Repo contents
- `A02-Healthcare-Equity-Hospital-Readmissions-and-Insurance-Coverage.ipynb`: full analysis. The notebook loads copies of the five files from shared Google Drive links, so it runs in Colab with no local file paths.

## Limitations
- CMS scores come from Medicare patients, while KFF coverage describes everyone. A null result means "no evidence through this state-level proxy", not "insurance does not matter".
- State-level analysis cannot speak to individual patients. Next step: patient-level data and a fuller model.

## Team
Aqsa Siddique, Samarth Karan, Ting Hui Chu, Dhruv Shah
