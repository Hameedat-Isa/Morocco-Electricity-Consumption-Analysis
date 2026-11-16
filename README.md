# Morocco Electricity Consumption and Environmental Factors Analysis

**AnalystLab Africa | Experience Lab Internship Programme | Week 5 | Data Analytics Track**
BY HAMEEDAT ISA-USMAN

## Project overview

This project explores electricity-consumption readings from **three Moroccan zones** and their relationship with environmental conditions. The dataset comprises **52,416 observations at 10-minute intervals**, from **1 January 2017 at 00:00** through **30 December 2017 at 23:50**. The objective is to describe consumption patterns by zone, hour, day, weekday and month, investigate associations with temperature, humidity and wind speed, and communicate evidence-based recommendations for energy-management monitoring.

The analysis follows the supplied Week 5 assignment and uses **Python, Jupyter Notebook, Pandas, NumPy, Matplotlib, Seaborn and Plotly**.

## Business questions

1. How do the three zones differ in their recorded consumption levels?
2. Which hours, weekdays and months have the highest and lowest average readings?
3. How do consumption patterns change over the observed year?
4. How are temperature, humidity and wind speed associated with recorded consumption?
5. How can descriptive findings support monitoring and better energy-planning decisions?

## Repository structure

The files in the supplied Week 5 project package are organised as follows. Place this `README.md` in the **root of the repository**, alongside `requirements.txt`.

```text
Week 5 – Hameedat Isa-Usman – Data Analytics/
Morocco-Electricity-Consumption-Analysis/
Morocco-Electricity-Consumption-Analysis/
│
├── data/
│   ├── powerconsumption.csv
│   └── powerconsumption_datadictionary.csv
│
├── notebooks/
│   └── Morocco_Electricity_Analysis.ipynb
│
├── outputs/
│   └── (Saved charts like fig1.png, fig2.png, pearson_correlation_heatmap.png, etc.)
│
├── reports/
│   └── Morocco_Electricity_Consumption_Report_Week5.docx
│
└── README.md
```

## Data preparation and quality checks

The notebook:

- loads both original CSV files and inspects the data dictionary;
- checks column names, data types, missing values and duplicate rows;
- **trims whitespace** from column headers and timestamp text;
- converts the `Datetime` column with the explicit format `%m/%d/%Y %H:%M`;
- checks for duplicate timestamps and inconsistent 10-minute intervals;
- converts numerical fields and checks for invalid or negative zone readings;
- flags unusual values using an exploratory **1.5×IQR rule**, without automatically deleting them;
- creates `Year`, `MonthNumber`, `Month`, `Day`, `Hour`, `DayOfWeek` and `Date` fields;
- exports a cleaned dataset and records the quality-check results.

### Verified data-quality summary

| Check | Result |
| --- | ---: |
| Original records | 52,416 |
| Original columns | 9 |
| Cleaned columns with time features | 16 |
| Missing values in source | 0 |
| Full-row duplicates | 0 |
| Duplicate timestamps | 0 |
| Invalid timestamps | 0 |
| Inconsistent consecutive time gaps | 0 |
| Consecutive 10-minute gaps | 52,415 |
| IQR-flagged Zone 1 / Zone 2 / Zone 3 readings | 0 / 7 / 1,191 |

All 52,416 records are retained. IQR flags indicate unusual observations, not established errors.

## Main findings

1. **Zone 1 has the largest average recorded consumption value** (32,344.97), followed by Zone 2 (21,042.51) and Zone 3 (17,835.41).
2. **All three zones show their highest hourly average at approximately 20:00.** Zones 1 and 2 have their lowest average around 06:00, while Zone 3 is lowest around 07:00.
3. **Monthly patterns differ:** Zones 1 and 2 reach their highest monthly mean in August; Zone 3 reaches its highest monthly mean in July.
4. **Temperature has a positive Pearson correlation** with the readings: Zone 1 `r=+0.440`, Zone 2 `r=+0.382`, Zone 3 `r=+0.490`.
5. **Humidity has a negative correlation**: Zone 1 `r=-0.287`, Zone 2 `r=-0.295`, Zone 3 `r=-0.233`.
6. **Wind speed has smaller positive correlations**: Zone 1 `r=+0.167`, Zone 2 `r=+0.146`, Zone 3 `r=+0.279`.

These are descriptive findings. **Correlation does not establish causation.**

## Recommendations

1. **Monitor and plan around evening peaks**, especially the 20:00 high-average period, and examine whether peak profiles persist in newer data.
2. **Use zone-specific monthly monitoring** rather than a single operating profile for all three zones; the zones differ in average level and seasonal timing.
3. **Monitor environmental variables alongside zone readings**, but account for hour of day and season before attributing consumption changes to weather.

## Methodological limitations

- The dataset ends on **30 December 2017**, so it cannot support multi-year comparisons or claims about 31 December.
- Although the supplied data dictionary labels the zone fields in *kilowatt-hours*, the assignment explicitly warns that the physical interpretation of each 10-minute observation has not been established. **Do not sum these readings into annual energy or report a verified total kWh** without source clarification. Comparisons here use means of the recorded values.
- Definitions of `GeneralDiffuseFlows` and `DiffuseFlows` are insufficient for firm physical interpretation. The required environmental analysis focuses on temperature, humidity and wind speed.
- Correlations may reflect time-of-day and seasonal effects as well as other unobserved factors. The results are not causal or predictive claims.

## Project workflow and deliverables

Work followed the Week 5 Data Analytics track sequence: dataset inspection → cleaning and feature engineering → zone/time analysis → environmental association analysis → chart creation → findings, recommendations and documentation. This order makes each chart traceable to validated source data.


## Source and acknowledgement

- AnalystLab Africa, **Experience Lab Internship Programme, Week 5**, *Morocco Electricity Consumption and Environmental Factors Analysis* (supplied assignment brief).
- Supplied data: `powerconsumption.csv` and `powerconsumption_datadictionary.csv`.

**#AnalystLabAfrica**
