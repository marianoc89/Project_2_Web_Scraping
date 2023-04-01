# Project 2 - Web Scraping - Idealista Website 
---
---

<p align="center">
    <img width="500" src="https://it-s.com/wp-content/webp-express/webp-images/uploads/2020/01/featured-image.jpg.webp" alt="Scrape">
</p>

---
---

The goal of this project is to scrape one of the biggest Realstate websites in Spain, to obtain information about the current market situaition for the appartments or houses currently being sold in "El Clot" neighbourhood. 
To obtain the data from the web, I have used Selenium, Requests and BeautifulSoup and by implementing data wrangling, cleaning, and manipulation with Pandas I have been able to make some data analysis which then gave me the possibility of making visualizations with different Python libraries such as Matplotlib, Seaborn and PlotlyExpress.

---
---
##  Table of Content:
   #### 1. Organization of the repo/project
   #### 2. Hypothesis of this project
   #### 3. Data
   #### 4. Visualizations
   #### 5. Conclusions
   #### 6. Links and Resources

***
### 1. Organization of the repo/project
***
```python
/data
    ayuntamiento_scrape{date_of_scrape}.csv
    Idealista_scrape{date_of_scrape}.csv
/images
    fig.jpg
    fig_3_barrios_yoy.jpg
    fig_3_barrios_yoy_sep.jpg
    fig_clot_price_evo_yoy.jpg
    fig_clot_price_scrape.jpg
    fig_el_clot_price_vs_euribor_evo.jpg
    fig_euribor_evo.jpg
/notebooks
    Idealista_Clot_Price_Scrape.ipynb
/src
    scrape.py
    visualization.py
.gitignore
README.md
```
***
### 2. Hypothesis of this project
***
#### Hypothesis --> Understand which is the current realstate market situation of the neighbourhood where I live ("El Clot")

   ##### a) What is the current price for M2?
   ##### b) Is there a pricing trend? Why?
   ##### c) Do we see a pattern in the price for previous years? Is there any reason for that?
   ##### d) Is there any relation between the price increas/decrease and the Euribor interest rate?


***
### 3. Data
***
In order to obtain all the data needed for this project, I had to scrape Idealista's website to get current market price and also historical data for Euribor interest rates and finally, Ayuntamiento de Barcelona's website to get historical data for neighborhoods pricing in Barcelona.
For that, I have created the scrape.py file that will take all the data needed from each website and create the DataFrame needed to perform analysis and visualizations.
I have created 2 fucntions that will compare current price against historical price data:
1. Clot_Price_Alert: This column will inform if the M2 price is considered: Low, Over, Good or Not The best Price. For that, it will compare current price agains the historical minimum, maximum and mean from "El Clot".
2. YoY_Price_Alert: This column will inform if the M2 price follows the same categorization as before but compared agains the minimum, maximum and mean for all the neightboors in Barcelona from previous year (2022).

***
### 4. Visualizations
***
1. Understanding what is the view of current market pricing:

![Alt text](images/fig_clot_price_scrape.jpg)

- Only 26% of all the sale adds have a "Good Price", meaning that the price per M2 is between the minimum and the mean. A 25% has not the best price but could potentially be negociated and 49% are currently over priced.

2. Understanding if there is a relation between the price and the fact that they have or not lift:

![Alt text](images/fig.png)


- Most of the adds that are currently in "Good Price" are because they don't have lift, while the ones with "Over Price" they mainly have lift.

3. Understanding the price evolution year over year for this neightboorhood and the correlation of the Euribor interest rate throughout the years:

![Alt text](images/fig_clot_price_evo_yoy.jpg)

![Alt text](images/fig_el_clot_price_vs_euribor_evo.jpg)

![Alt text](images/fig_euribor_evo.jpg)

- The year 2014 and 2019 are considered inflection points were the M2 price has changed the behaviour.
The current mean price for El Clot is €3,260.90 for the M2 price between 2013-2022 (10 years).
In regards to the Euribor rate evolution, we can clearly see that after the housing crisis suffered in 2008, the rate has been decreasing year over year, even reaching negative rates from 2015 until 2021, which is considered the minimum and is currently (2023) at maximum rates.

4. Is there a pattern on the behaviour of this neighborhood with other neighborhoods (Ciutat Meridiana and Diagonal Mar)?

![Alt text](images/fig_3_barrios_yoy_sep.jpg)

![Alt text](images/fig_3_barrios_yoy.jpg)

- Ciutat Meridiana is currently the neighborhood with the lowest price M2 and Diagonal Mar with the maximums. Despite the prices and the cost per M2, we can clearly see that the pattern and the price fluctuation follows a similarity with a clear diference on Diagonal Mar for which the price has not stop increasing and keeps going up overitme.

***
### 5. Conclusions
***
Based on the hypothesis of this project and after analyzing the data and visualizing the results, we can conclude the following:
- The current market price is a bit over priced and the good prices (M2) could mainly be found for appartments with no lift.
- There are some opportunities which would require some negotiations to achieve a better pricing to close a "good price".
- We can clearly see that from 2014 onwards the M2 price has increased drastically year over year reaching a maximum in 2019. The reason for this could be related to the launched of the project "Canòpia Urbana" in 2014, informed "Ayuntamiento de Barcelona" which had several stages, starting in 2015 and having a first conclusion in 2019 and final will be in 2024. On the other side, we can clarely see that the low interest rates in Euribor has also helped to increase the investent on this neighborhood, helping with the price increase YoY during those years. As soon as the interest rate touched it's minimum and started to escalate to the current maximums, the price evolution has stopped increasing.
***
### 6. Links and Resources
***
- Data sources: 
1. Idealista (El Clot): https://www.idealista.com/venta-viviendas/barcelona/sant-marti/el-clot/
2. Ayuntamiento de Barcelona: https://ajuntament.barcelona.cat/estadistica/angles/Estadistiques_per_temes/Habitatge_i_mercat_immobiliari/Mercat_immobiliari/Preu_oferta_habitatge_segona_ma/evo/t2mab.htm
3. Historical Euribor: https://www.idealista.com/news/euribor/historico-diario/
4. Ayuntamiento de Barcelona (Project Canòpia Urbana info.): https://ajuntament.barcelona.cat/glories/es/fases/
- Library used:
    - https://numpy.org/doc/1.18/
    - https://pandas.pydata.org/
    - https://docs.python.org/3/library/functions.html
    - https://plotly.com/python/
    - https://matplotlib.org/
    - https://seaborn.pydata.org/
    - https://pandas.pydata.org/docs/