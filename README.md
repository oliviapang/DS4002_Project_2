# DS4002_Project_2
## Table of Contents
1. Software and Platform  
2. Documentation Map  
3. Instructions for Reproduction  

## Software and Platform
Softwares used: Google Colab and Python 3.10.12  
Add-ons: pandas 2.2.2, numpy 1.26.4, matplotlib 3.7.1, seaborn 0.13.1, statsmodels 0.14.2, scikit-learn 1.5.2  
Platform: Windows  

## Documentation Map
```mermaid
graph TD
    %% Styling Definitions
    classDef purple fill:#DCD6F7,stroke:#4B3F72,stroke-width:1.5px,color:#000;
    classDef blue fill:#D4EBF8,stroke:#1F4E79,stroke-width:1.5px,color:#000;
    classDef green fill:#E2F0D9,stroke:#385723,stroke-width:1.5px,color:#000;

    %% Root
    Root["DS4002_Project_2<br/>Repository"]:::purple

    %% Top-Level Direct Folders and Files
    Root --> DATA["DATA"]:::blue
    Root --> OUTPUT["OUTPUT"]:::blue
    Root --> SCRIPTS["SCRIPTS"]:::blue
    Root --> LICENSE["LICENSE.md"]:::blue
    Root --> README["README.md"]:::blue

    %% DATA Column (Vertical stack)
    DATA --> D1["GASREGW.csv"]:::green
    D1 --> D2["README.md"]:::green
    D2 --> D3["cleaned_differenced_data.csv"]:::green
    D3 --> D4["monthly_oil_gas_prices.csv"]:::green
    D4 --> D5["oil_data.xls"]:::green

    %% OUTPUT Column (Vertical stack)
    OUTPUT --> O1["absolute_errors_boxplot (1).png"]:::green
    O1 --> O2["absolute_errors_over_time (1).png"]:::green
    O2 --> O3["bias_and_residuals_comparison (1).png"]:::green
    O3 --> O4["evaluation_metrics.csv"]:::green
    O4 --> O5["forecasts_comparison.csv"]:::green
    O5 --> O6["multi_horizon_comparison.csv"]:::green
    O6 --> O7["multi_horizon_forecasts (1).png"]:::green
    O7 --> O8["oil_gas_scatter.png"]:::green
    O8 --> O9["price_trends_timeseries.png"]:::green
    O9 --> O10["walk_forward_forecasts (2).png"]:::green

    %% SCRIPTS Column (Vertical stack)
    SCRIPTS --> S1["1_Cleaning_and_EDA.ipynb"]:::green
    S1 --> S2["2_Build_Model.ipynb"]:::green
    S2 --> S3["3_Evaluating_Model.ipynb"]:::green
```
## Instructions for Reproduction
1. Download gasoline price data from FRED (`GASREGW.csv`) and crude oil price data from EIA (`oil_data.xls`). Save both files in the DATA folder. *Note: Steps 2–5 can be accomplished by running `1_Cleaning_and_EDA.ipynb` in Google Colab.*
2. Import the required libraries and load both datasets into pandas DataFrames.
3. Clean the datasets by converting dates and prices into appropriate formats and removing observations with missing or invalid values.
4. Convert both datasets into monthly averages, merge them by date, and apply logarithmic transformations to gasoline and crude oil prices.
5. Perform exploratory data analysis, including price trends and correlation. Export the processed dataset as `monthly_oil_gas_prices.csv`. *Note: Steps 6–11 can be accomplished by running `2_Build_Model.ipynb` in Google Colab.*
6. Import the processed dataset, shift logged crude oil prices back one month (t-1), and perform ADF and KPSS tests to check stationarity.
7. Calculate first differences of logged prices and fit initial SARIMA and SARIMAX models to the differenced data.
8. Split the logged price data chronologically into training (before 2020) and testing (2020 onward) datasets without shuffling.
9. Build and fit SARIMA and SARIMAX forecasting models with order (1,1,1) and seasonal order (1,1,1,12). SARIMA uses historical gasoline prices, while SARIMAX includes lagged crude oil prices.
10. Perform one-month-ahead walk-forward validation by repeatedly forecasting with updated historical observations without refitting. Include a naive forecast using the previous month's gasoline price.
11. Convert predictions back to dollars per gallon and export `forecasts_comparison.csv`, `evaluation_metrics.csv`, and `oil_coefficient.csv` to OUTPUT. Export `cleaned_differenced_data.csv` to DATA. *Note: Steps 12–15 can be accomplished by running `3_Evaluating_Model.ipynb` in Google Colab.*
12. Import actual gasoline prices and forecast results from the naive, SARIMA, and SARIMAX models.
13. Calculate RMSE, MAE, and MAPE to compare forecasting accuracy across all three models.
14. Examine the crude oil coefficient and its p-value from the initial SARIMAX model to assess statistical significance.
15. Plot actual versus predicted gasoline prices and compare model performance using forecast errors, RMSE, and residual visualizations. Determine whether SARIMAX improves forecasting accuracy compared with SARIMA.

## References
[1] Federal Reserve Bank of St. Louis, "U.S. Regular All Formulations Retail Gasoline Prices (GASREGW)," FRED. Available: https://fred.stlouisfed.org/series/GASREGW  
[2] U.S. Energy Information Administration, "Cushing, OK WTI Spot Price FOB (RWTCD)." Available: https://www.eia.gov/dnav/pet/hist/RWTCD.htm  
[3] S. P. A. Brown and M. K. Yücel, "Gasoline and crude oil prices: Why the asymmetry?," Economic and Financial Review, Federal Reserve Bank of Dallas, pp. 23–29, 2000.  
[4] R. J. Hyndman and G. Athanasopoulos, Forecasting: Principles and Practice, 3rd ed., OTexts, 2021. https://otexts.com/fpp3/  
