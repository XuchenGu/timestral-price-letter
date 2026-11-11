# Shanxi day-ahead electricity price and covariate dataset

Data of the IEEE letter *Forecasting Electricity Prices With Market-Specific Covariates via Training-Free Foundation Model*, which evaluates the frozen time-series foundation model Timestral-209M against eight trained benchmarks on the day-ahead prices of two Chinese provincial spot markets.

> The Liaoning data used in the letter is confidential and therefore not released. This repository contains the Shanxi market only.

> The code of the experiments will be added to this repository after the letter has been submitted.

## Data

`data/shanxi_15min.csv` holds the day-ahead clearing price and the day-ahead forecasts of the Shanxi spot market.

| column | meaning | unit |
|---|---|---|
| `timestamp` | start of the quarter-hour | |
| `DA_Price` | day-ahead clearing price (target) | CNY/MWh |
| `wind`, `solar`, `renew_total` | day-ahead forecast of wind, solar and total renewable output | MW |
| `tieline` | day-ahead forecast of the tie-line power | MW |
| `load_forecast` | day-ahead load forecast | MW |
| `total_power` | day-ahead forecast of the total power supply | MW |

Resolution 15 minutes (96 points per day), 49,152 rows, 512 complete days from 2025-01-01 00:00 to 2026-05-27 23:45, no missing values. The experiments use the hourly series (24 points per day, the mean of the four quarter-hours of an hour, for the price and the covariates). The six covariates are known for the forecast day; there are no past-only covariates. The days are split chronologically 60/20/20: 306 days for training (2025-01-01 to 2025-11-02), 103 days for validation (to 2026-02-13) and 103 days for testing (2026-02-14 to 2026-05-27).
