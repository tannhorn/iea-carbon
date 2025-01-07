# iea-carbon
Analysis of IEA carbon emission forecasts. The analysis is done in the `analysis.ipynb` notebook, which you can open and run in Google Colab using the widget below.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/tannhorn/iea-carbon/blob/main/analysis.ipynb)

The underlying data is sourced from [IEA World Energy Outlook reports](https://www.iea.org/reports/world-energy-outlook-2024) and is collated in the `data/data.json` JSON file. The exact reference URL and page in the given document is given for each year, which typically has the format:

```json
  "2013": {
    "link": "https://iea.blob.core.windows.net/assets/a22dedb8-c2c3-448c-b104-051236618b38/WEO2013.pdf",
    "page": {
      "Current Policies": 575,
      "New Policies": 574
    },
    "year": [1990, 2011, 2020, 2025, 2030, 2035],
    "values": {
      "Current Policies": [20948, 31161, 36059, null, 40825, 43111],
      "New Policies": [20948, 31161, 34595, 35722, 36493, 37242]
    }
```

Here,
- "2013" is the key, i.e. the year of the given World Energy Outlook report
- "link" is the URL of the report
- "page" gives the page number from which the data has been taken for selected scenarios (here "Current Policies" and "New Policies")
- "year" gives the years for which historical data (year lower than the year of the report) or predictions (year higher than the year of the report)
- "values" give the corresponding values of CO2 emissions in Mt/year for the selected scenarios. `null` corresponds to a missing value

Note that in the analysis, cubic spline interpolation/extrapolation is used based on the provided data. Furthermore, 
- "Reference" and "Current Policies" correspond to the same scenario
- "New Policies" and "Stated Policies" correspond to the same scenario