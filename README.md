[README.md](https://github.com/user-attachments/files/27098795/README.md)
# Youth Unemployment & Economic Structure: A Global Analysis (1991–2022)

**ACC102 Mini Assignment — Track 2: GitHub Data Analysis Project**
Xi'an Jiaotong-Liverpool University · 2nd Semester 2024–25

---

## 1. Problem & User

**Analytical problem:** Youth unemployment consistently runs far above total unemployment across the world, yet the gap varies enormously by region and economic structure. This project asks: *How has global youth unemployment evolved since 1991, which regions and countries are most affected, and how does economic structure (sector dominance, GDP size) relate to the youth employment gap?*

**Target audience:** Economics and policy students, early-career researchers, and anyone who wants a clear, data-driven picture of the global youth employment challenge.

---

## 2. Data

| Dataset | Source | Access date | Key variables |
|---------|--------|-------------|---------------|
| `youth_unemployment_global.csv` | World Bank / ILO (via Kaggle) | April 2025 | Country, Year, YouthUnemployment (%) |
| `Employment_Unemployment_GDP_data.csv` | World Bank Open Data (via Kaggle) | April 2025 | Country, Year, GDP (USD), Unemployment Rate (%), Employment sector shares (Agriculture / Industry / Services) |

Both files are included in this repository. Coverage spans **1991–2022** across up to **100+ countries** after merging and cleaning.

---

## 3. Methods (Python Workflow)

All analysis is in `notebook.ipynb`. The main steps are:

1. **Data loading** — read both CSVs with `pandas`
2. **Cleaning** — drop rows with missing `YouthUnemployment`; filter to 1991–2022
3. **Merging** — inner join on `Country` + `Year`
4. **Feature engineering**
   - `GDP_bn` — GDP in billions USD
   - `GDP_log` — log₁₀ of GDP (for scatter analysis)
   - `Youth_Gap` — youth minus total unemployment rate
   - `Dom_Sector` — dominant employment sector (Agriculture / Industry / Services)
   - `Region` — hand-mapped region labels (7 regions)
5. **Visualisation** (4 figures, saved to `figures/`)
   - Fig 1: Global trend line — youth vs total unemployment, 1991–2022
   - Fig 2: Regional boxplot of youth unemployment in 2022
   - Fig 3: Scatter — log GDP vs youth unemployment (2022, coloured by region)
   - Fig 4: Bar — median youth-adult unemployment gap by dominant sector
6. **Key findings** — printed summary statistics

**Libraries:** `pandas`, `matplotlib`, `seaborn`, `numpy`

---

## 4. Key Findings

- Global average youth unemployment **peaked at 18.8% in 2020** (COVID-19 shock) and stood at **16.2% in 2022**.
- Youth unemployment is consistently **roughly 2× the total rate** — the multiplier effect is persistent across all regions and decades.
- **Highest region (2022): Middle East & Africa (20.9%)** — driven by structural underemployment and demographic pressure.
- **Lowest region (2022): Asia-Pacific (8.5%)** — reflecting stronger labour absorption in manufacturing and services.
- **Top 5 highest youth unemployment countries (2022):** South Africa (61.1%), Jordan (42.0%), Tunisia (37.8%), North Macedonia (32.6%), Iraq (32.1%).
- **GDP correlation with youth unemployment: r = −0.26** — a modest negative relationship; wealthier economies tend to have lower youth unemployment, but the link is far from deterministic.
- **Youth-adult gap by sector:** Services-dominant economies show a larger gap (8.2 pp median) than agriculture-dominant ones (3.4 pp), likely because informal agricultural work absorbs young workers without formal employment.

---

## 5. How to Run

```bash
# Clone the repository
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

# Install dependencies
pip install pandas matplotlib seaborn numpy jupyter

# Launch the notebook
jupyter notebook notebook.ipynb
```

Both CSV data files are included in the root folder. No additional setup is needed.

**Requirements** (also in `requirements.txt`):
```
pandas
matplotlib
seaborn
numpy
jupyter
```

---

## 6. Repository Structure

```
.
├── README.md
├── notebook.ipynb          ← Main analysis notebook
├── requirements.txt
├── youth_unemployment_global.csv
├── Employment_Unemployment_GDP_data.csv
└── figures/
    ├── fig1_global_trend.png
    ├── fig2_regional_boxplot.png
    ├── fig3_gdp_scatter.png
    └── fig4_sector_gap.png
```

---

## 7. Limitations & Next Steps

- The region mapping is manual and approximate; some countries are labelled "Other" due to missing coverage.
- The GDP–unemployment correlation is cross-sectional and does not imply causation.
- Data completeness varies by country; some smaller economies have gaps in the time series.
- Future work could apply panel regression or clustering to identify country archetypes, or extend the dataset to 2023–2024 using the latest ILO releases.

---

## 8. Demo Video

*https://video.xjtlu.edu.cn/Mediasite/Play/26ffd064282647d6afde3188d4e00dd51d*

---

*ACC102 · Track 2 · GitHub Data Analysis Project · XJTLU IBSS*
