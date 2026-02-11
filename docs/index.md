
# Summary
Accurate day-ahead forecasts of solar energy availability are essential for grid operations, energy trading, and renewable integration, particularly in regions with strong cloud-driven variability. In this project, I developed a **day-ahead solar irradiance forecasting pipeline** using hourly data from the National Solar Radiation Database (NSRDB) for Metropolitan Manila, Philippines, and evaluated its performance against a meaningful persistence baseline.

The forecasting task was formulated as a **24-hour-ahead prediction problem**, where Global Horizontal Irradiance (GHI) at time *t+24* is predicted using only information available at time *t*. This formulation avoids the inflated performance commonly observed in hour-ahead forecasting due to short-term persistence and deterministic solar geometry. Predictors included calendar variables, meteorological conditions, clear-sky reference irradiance, and historical persistence at the daily scale.

Model performance was evaluated using a chronological 80/20 train–test split to preserve temporal causality. A persistence baseline assuming that tomorrow’s irradiance equals today’s irradiance at the same hour yielded an RMSE of **271.5 W/m²**, highlighting the inherent difficulty of day-ahead solar prediction in a tropical environment. A linear regression model reduced the RMSE to **218.1 W/m²**, corresponding to a **~20% improvement** over the baseline. The best performance was achieved by a Random Forest model, which attained an RMSE of **177.2 W/m²**, representing a **~35% reduction in error** relative to persistence.

Feature importance analysis indicates that clear-sky irradiance and diurnal/seasonal timing dominate predictability, reflecting the strong deterministic control of solar geometry. Meteorological variables contribute secondary nonlinear corrections associated with cloud modulation. Despite these improvements, substantial residual errors remain, emphasizing the intrinsic unpredictability of cloud evolution at day-ahead horizons.

To assess operational relevance, irradiance forecasts were converted into photovoltaic (PV) power and daily energy yield using a simplified fixed-efficiency PV model. This conversion demonstrates that even moderate improvements in irradiance forecast skill translate into meaningful differences in estimated daily energy production, while also illustrating the limits imposed by atmospheric variability.

Overall, this project demonstrates a **physically consistent, leakage-free, and operationally realistic approach to day-ahead solar forecasting**, providing a transparent benchmark for evaluating machine-learning models in renewable energy applications.

---
## Full Notebook

👉 [Open the full analysis notebook](solar_notebook.html)
---

## Figures

### Day-Ahead GHI Forecast (Random Forest)
![Day-ahead GHI forecast](figures/ghi_day_ahead_forecast.png)

### Random Forest Feature Importance
![RF feature importance](figures/rf_feature_importance_day_ahead.png)

### Day-Ahead PV Power Forecast
![PV power forecast](figures/pv_power_day_ahead.png)

### Daily PV Energy Error (Day-Ahead)
![Daily PV energy error](figures/pv_daily_energy_error.png)
---
