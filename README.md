## Hong Kong Stargazing Analysis Project

### Introduction

Stargazing in Hong Kong is challenged by severe light pollution, making it difficult to observe celestial objects except in rural areas under optimal conditions. This project aims to use data analysis and machine learning skills to find the correlations between stargazing levels and weather conditions and build the foundation for helping users find the best times and locations for stargazing with less manual effort.

### Methodology

- **Data Sources:**

  - Night sky brightness from the [Globe at Night - Sky Brightness Monitoring Network (GaN-MN)](https://globeatnight.org/gan-mn/)
  - Weather data from the [Hong Kong Observatory Open Data](https://www.hko.gov.hk/en/abouthko/opendata_intro.htm)

- **Data Processing:**

  - Aggregated minute-level sky brightness data to daily values to match daily weather data.
  - Applied corrections for city light using [VIIRS satellite data](https://eogdata.mines.edu/products/vnl/) and the natural night sky
    brightness value from the Hong Kong Space Museum Astropark in the GaN-MN dataset.
  - Final dataset: 936 rows, 25 features (e.g., cloud amount, humidity, wind speed, moon phase).

- **Analysis:**
  - Explored correlations and trends among features.
  - Built regression models (Linear Regression, Random Forest) to predict daily night sky brightness.
  - Evaluated models using Mean Squared Error (MSE), R-squared, and K-fold cross-validation.
  - Assessed feature importance to identify key influencing factors.

### Results

- **Model Performance:**
  - Random Forest outperformed Linear Regression (lower MSE, higher R²).
- **Key Findings:**
  - Most important negative factors: cloud amount, moon phase, wind speed, sunshine hours, relative humidity.
  - Best stargazing: clear skies, no moon, calm winds, short sunshine hours in the day, low humidity.
- **Limitations:**
  - Some uncertainty remains due to city light and model simplicity.

### Future Work

Develop a real-time tool to synthesize weather data and output a stargazing Bortle scale for Hong Kong.

## Supplementary

1. Link to [SEEM2460 Project Proposal](https://docs.google.com/document/d/14zvYhnD2CBXRDK7w4SIBz02xTEZQ-CqUO9WUBEokABE/edit?usp=sharing)
2. Link to [SEEM2460 Project Report](https://docs.google.com/document/d/1342FDZmJr44Bkj5SwCuIYfURDuOp-Uki4xiX12l7Kas/edit?usp=sharing)
3. Links to Pre-processed Raw Data:
   - Sky Brightness Data: [GaN-MN Data](https://globeatnight.org/gan-mn/)
   - Weather Data: [Hong Kong Observatory Open Data](https://www.hko.gov.hk/en/abouthko/opendata_intro.htm)
4. Link to [Processed Data](https://drive.google.com/drive/folders/19-j077JSlG8R-ns6nsTmUky4P4rrGH9S?usp=sharing):
   - `filtered_data.zip`: Include `daily_nsb.csv`, `combined_sun`, `combined_moon`, and `nsb_weather_merged`
   - `sky_brightness.zip`: Include every month's sky brightness data from January 2022 to October 2024
   - `weather.zip`: Include different kinds of weather data
5. The dataset contains features from 1-1-2022 to 31-10-2024
6. `nsb_weather_merged` Dataset features:
<table border="1">
  <tr>
    <td align="center">Max Night Sky Brightness (MPSAS)</td>
    <td align="center">Min Night Sky Brightness (Non-zero) (MPSAS)</td>
    <td align="center">Mean Night Sky Brightness (Excluded zero) (MPSAS)</td>
    <td align="center">Daily Mean Hong Kong Heat Index</td>
    <td align="center">Daily Mean Wet Bulb Temperature (°C)</td>
  </tr>
  <tr>
    <td align="center">Daily Mean Dew Point Temperature (°C)</td>
    <td align="center">Daily Mean Amount of Cloud</td>
    <td align="center">Daily Mean Pressure (hPa)</td>
    <td align="center">Daily Total Evaporation (mm)</td>
    <td align="center">Daily Total Rainfall (mm)</td>
  </tr>
  <tr>
    <td align="center">Daily Mean Relative Humidity (%)</td>
    <td align="center">Daily Maximum Temperature (°C)</td>
    <td align="center">Daily Minimum Temperature (°C)</td>
    <td align="center">Daily Mean Temperature (°C)</td>
    <td align="center">Daily Global Solar Radiation (MJ/m2)</td>
  </tr>
  <tr>
    <td align="center">Daily Total Bright Sunshine (hours)</td>
    <td align="center">Daily Mean Wind Speed (m/s)</td>
    <td align="center">Sun Rise</td>
    <td align="center">Sun Transit</td>
    <td align="center">Sun Set</td>
  </tr>
  <tr>
    <td align="center">Moon Rise</td>
    <td align="center">Moon Transit</td>
    <td align="center">Moon Set</td>
    <td></td>
    <td></td>
  </tr>
</table>
