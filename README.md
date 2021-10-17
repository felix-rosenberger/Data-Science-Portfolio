# Data Science Portfolio

This repository contains the files and notebooks for the Portfolio task for *COMP6200 Introduction to Data Science* in S2 2021 of my Master's degree *Business Analytics and Management* at Macquarie University in Sydney. It consists of three single portfolios, each handling different data and objectives. All notebooks are run with Python 3.6.

# Portfolio 1: Analysis of Cycling Data
> Portfolio 1 analyses four files containing data about cycling activities that include GPS location data as well as some measurements related to cycling performance like heart rate and power. The objective was to perform data exploration and analysis. The data represents four races. Two are time trials where the rider rides alone on a set course. Two are road races where the rider rides with a peleton. All were held on the same course but the road races include two laps where the time trials include just one.

## Getting started
The following libraries and scripts have been used for this notebook:
```
import pandas as pd
import numpy as np 
from gpxutils import parse_gpx 
import matplotlib.pyplot as plt
import seaborn as sns
```
Note that [gpxutils.py](gpxutils.py) is a script to read in the GPX XML format files that are exported by cycling computers and applications. The sample files were exported from [Strava](https://www.strava.com).<br >

The following files are used within this portfolio:
- [Road Race 2016](files/Calga_RR_2016.gpx)
- [Road Race 2019](files/Calga_RR_2019.gpx)
- [Time Trial 2016](files/Calga_TT_2016.gpx)
- [Time Trial 2019](files/Calga_TT_2019.gpx)

## Scope
- [x] What is the overall distance travelled for each of the rides? What are the average speeds etc.
- [x] Compare the range of speeds for each ride, are time trials faster than road races?
- [x] Compare the speeds achieved in the two time trials (three years apart).
- [x] Calculate the average speeds in three cases (climbing, flat or descending).
- [x] Write code to calculate development in meters for each row in a ride. Plot the result and compare for the four rides.

## Summary
The main part of this notebook is about summarising the data, handle outliers that are due to errors in measurement and to provide insights about each race as well as how the races differ in their characteristics. In this sense it is a classic exploratory data analysis that would need to be done as a starting point of any project.<br >
Task four has been enhanced by providing a visualisation of speed distribution for different slope gradients. This intuitively lets the reader get a sense for how slope gradient impacts speed.<br>
Development distribution for each race is shown in histograms which lets the reader get a feeling which gear the rider used most often during the race since a lower gear usage would result in a lower development.


# Portfolio 2: Analysis of Sport Voucher Data
> Portfolio 2 explores data from the Australian Federal Government Sport Vouchers program for South Australia and Queensland where the government provides vouchers for children to do sports in clubs. The objective was to provide information about voucher usage in different Local Government Areas (LGA) and across different sports. Also, socio-economic data is used to to analyse whether different socio-economic conditions across LGAs impact voucher usage in any way.

## Getting started
The following libraries and packages have been used for this notebook:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import geopandas as gpd
from shapely.geometry import Point, Polygon
```

The following files are used within this portfolio:
- [Socio-economic Data](files/ABS_SEIFA_LGA.csv)
- [Geodata for Map Visualisation](files/LGA_GDA2020.geojson)
- [Sports Vouchers Data for South Australia](files/sportsvouchersclaimed.csv)
- [Sports Vouchers Data for Queensland](files/round1-redeemed_get_started_vouchers.csv)

## Scope
- [x] Description of the distribution of vouchers by LGA and Sport - which regions/sports stand out?
- [x] Sports popularity analysis across LGAs.
- [x] Analysis of voucher usage across LGAs: any over-/underrepresentation in their use of vouchers?
- [x] Relationship analysis between any of the socio-economic measures and voucher use in an LGA?
- [x] Sports popularity analysis and relationship analysis between socio-economic measures and voucher usage in LGAs for Queensland.

## Summary
The first part of the notebook contains the description of the distribution of vouchers by sport and by LGA. Afterwards, the data is analysed with regards to whether some sports are more popular in different parts of the state. The findings are first visualised in a heatmap for the most popular sports, and then on a map where voucher usage across LGAs can be seen through the color gradient on the map of South Australia. It can be concluded that there are a few sports that dominate in popularity across the whole state. Also, voucher usage is heavily dependent on LGAs.<br>
In the third part, it is shown that there is indeed over- and underrepresentation of voucher use in relation to population of LGAs. This finding is first shown in a plot where the threshold is defined by the mean value and, second, a map of South Australia shows that distribution which shows that especially metropolitan areas seem to be underrepresented in their use of vouchers.<br >
The fourth part looks at the relationship between socio-economic measures like educational and occupational levels or economic resources in LGAs and the use of vouchers. It can be found that there is a relationship mostly with economic resources and educational opportunities. One might expect the relationship to be negative, so that disadvantaged areas would use vouchers more than wealthy areas. However, even though the relationship is rather weak, it is the other way around. It is also shown that the middle class uses the vouchers most frequently.
In the last part, the same analysis is conducted for Queensland. Sports popularity is shown and also a comparison to South Australia. The analysis for socio-economic relationship has revealed different results than for South Australia. Namely, the voucher usage is higher for LGAs that have lower socio-economic scores.


# Portfolio 3: Predicting Customer Churn
> Portfolio 3 explores data from a mobile provider in Australia for customer churn. Churn is where a customer leaves the mobile provider. The goal is to build a predictive model to predict churn from available features.

## Getting started
The following libraries and packages have been used for this notebook:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pandas_profiling
from sklearn.preprocessing import StandardScaler, OneHotEncoder, OrdinalEncoder
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score, confusion_matrix, plot_confusion_matrix
from sklearn.inspection import permutation_importance
```

The following files are used within this portfolio:
- [Mobile Customer Churn Data](files/MobileCustomerChurn.csv)

Additionally, a [dictionary](files/MobileChurnDataDictionary.csv) for all feature names is available in the files folder that explains each variable contained in the data.

## Scope
- [x] Build a predictive model for customer churn.

## Summary
This notebook contains an extensive exploratory data analysis. Naive Bayes has been chosen as a classification algorithm for modeling. Different models have been run for different variable transformations. For the most promising versions, feature selections based on permutation importance and multicollinearity analysis has been conducted. The final decision has been made for a model with 7 features only and without variable transformations. <br >
The overall model accuracy achieved is 71.43% while the sensitivity of the model is 84.74%. This means that almost 85% of churners can be predicted correctly by the model.

# License
The code in these portfolios is licensed under the [BSD 3-Clause license](LICENSE).