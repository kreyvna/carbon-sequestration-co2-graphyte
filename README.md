# Carbon Sequestration Analysis from Mauna Loa CO₂ Data

This project analyzes atmospheric CO₂ trends using NOAA’s Mauna Loa Observatory dataset. It simulates how environmental sensor data can be used to validate carbon sequestration effectiveness — a critical step in ensuring carbon removal solutions are measurable and permanent.

## Project Goals

- Clean and preprocess NOAA CO₂ sensor data
- Visualize long-term and seasonal atmospheric CO₂ trends
- Apply linear regression to model historical accumulation
- Detect anomalies that could represent faulty readings or unusual events
- Identify periods of interpolated or non-standard data
- Highlight sensor integrity concerns such as source changes (e.g. Maunakea station)
- Demonstrate how data supports the permanence and traceability of CO₂ removal

## Project Structure
<pre>
carbon-sequestration-co2-graphyte/
├── data/
│   ├── raw/                     # Original NOAA data file
│   └── processed/               # Cleaned dataset with flags
├── visuals/                     # Saved charts from notebook
├── notebooks/
│   └── sequestration_analysis.ipynb
├── README.md
└── requirements.txt
 </pre>

## Data Details

The original dataset was downloaded from NOAA's Global Monitoring Laboratory:

> https://gml.noaa.gov/ccgg/trends/data.html  
> Source: NOAA Global Monitoring Laboratory (Mauna Loa CO₂ Monthly Mean Data)

### Columns used:
| Column           | Description |
|------------------|-------------|
| `year`           | Calendar year |
| `month`          | Month of year |
| `decimal_date`   | Year + month as decimal (e.g., 2020.5 = June 2020) |
| `average`        | Raw monthly average CO₂ concentration (ppm) |
| `deseasonalized` | Smoothed CO₂ trend line (seasonal effects removed) |
| `ndays`          | Days of valid measurements per month |
| `sdev`, `unc`    | Standard deviation and uncertainty (negative = interpolated) |

## Flags Created During Analysis

- `is_interpolated`: Months filled in via interpolation (uncertainty < 0)
- `is_scripps`: Data from 1958–1974, originally collected by Scripps Institution of Oceanography
- `is_maunakea`: Data from Dec 2022–July 2023, collected at a temporary Maunakea station

## Key Findings

- Atmospheric CO₂ is rising at ~1.65 ppm per year.
- Seasonal oscillations reflect natural carbon cycles (e.g., vegetation respiration).
- Statistical outliers were detected via z-score filtering.
- ~24% of data points were flagged as interpolated.
- ~7 months were flagged as originating from the temporary Maunakea station.

## Tools Used

- Python (pandas, seaborn, matplotlib, scikit-learn)
- Jupyter Notebook

## Attribution

Data provided by:
- **NOAA Global Monitoring Laboratory** – [NOAA GML CO₂ Trends](https://gml.noaa.gov/ccgg/trends/)
- **Scripps Institution of Oceanography** – CO₂ records from 1958–1974

These data are made freely available by NOAA and Scripps in support of climate research. For formal citation:  
> NOAA GML. “Mauna Loa CO₂ Monthly Mean Data.” https://gml.noaa.gov/ccgg/trends/

## Author

Kevin Reyna  
2025 Climate Tech Portfolio
