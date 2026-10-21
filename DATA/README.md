## Metadata
### Data Summary
This project will use two datasets from the Federal Reserve Bank of St. Louis’s FRED database and the U.S. Energy Information Administration (EIA) to investigate 
whether incorporating crude oil prices improves forecasts of  U.S. gasoline prices. The first dataset consists of weekly U.S. regular gasoline prices measured in 
dollars per gallon. The second dataset contains historical daily West Texas (WTI) crude oil spot prices measured in dollars per barrel. The datasets can be found 
at https://fred.stlouisfed.org/series/GASREGW and https://www.eia.gov/dnav/pet/hist/RWTCD.htm. The gasoline data is weekly while the crude oil data is daily. To 
account for this, crude oil prices will be aggregated to weekly averages. The combined dataset will be used to compare the forecasting accuracy of SARIMA and ARIMAX 
models.
### Provenance
The gasoline price data and crude oil data are both published by the EIA. The gas data is also distributed through FRED by the Federal Reserve Bank of St. Louis. 
The EIA collects the gas prices with a survey of about 900 retail outlets across the U.S., and the reported prices are weighted averages that include applicable 
taxes. The crude oil data represents the daily price of West Texas Intermediate crude oil in Cushing, Oklahoma. Both datasets provide historical pricing data and 
consistent measurements to be used for time-series analysis. The gas data is updated weekly, whereas the crude oil data contains data from daily measurements on 
trading days.
### License
Both datasets are published by the EIA, a U.S. government agency. The data can be used for analysis with proper attribution. For our project, we will not present 
the data as our own original data. Instead, we will cite the original sources and provide links to the datasets. FRED classifies the dataset containing gas prices 
as public-domain data and requests proper citation.
### Data Dictionary
| Variable | Description | Units/Type | Source |
|:---:|:---:|:---:|:---:|
Date | Data associated with each weekly observation | Date; text | FRED/EIA
Gas Price | Average U.S. retail price of regular gasoline, including taxes | $/gallon; numerical | FRED (GASREGW)
Crude Oil Price | Average crude oil spot price after converting daily values to weekly values | $/barrel; numerical | EIA (RWTCD)
### Exploratory Plots
<img width="1387" height="590" alt="image" src="https://github.com/user-attachments/assets/4c22b843-9907-4bf5-b1f9-77e30aece3a8" />

<img width="788" height="590" alt="image" src="https://github.com/user-attachments/assets/e00d7a03-d066-4861-ac3f-aaba41ddb68b" />
