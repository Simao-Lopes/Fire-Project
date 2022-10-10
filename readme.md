![logo_fire](https://raw.githubusercontent.com/Simao-Lopes/Fire-Project/main/Presentation/Background/1817788.jpg)


Fires in Portugal 
======


## The problem

In Portugal, every year we have a problem with fires. Most of the time it's due either to poor resource allocation, or insufficient resources. I try to understand if it's possible to create a model to predict with acceptable accuracy the burnt area. In the process of cleaning and studying the dataset, I found many interesting things that are explained in the presentation. Feel free to use everything on this repository for your projects.

I will develop this continuously and feed it with new data.

## Analysis conclusions

**Tableau public: [Link](https://public.tableau.com/app/profile/sim.o6187/viz/NewFire-Project/Bush)**

During my analysis I found that an assessment by burnt area was a possible metric but probably not the best, so I calcculated the CO2 emissions by district and used it as a metric to define the worst offender districts considering CO2 emissions. During hypotesis I learned that the re-ignition rates on this 5 districts is way higher than Portugal's re-ignition mean, but the average fire count is actually lower in the top 5.

![co2_plot](https://raw.githubusercontent.com/Simao-Lopes/Fire-Project/main/Presentation/Graphs/Co2%20ratios.PNG)

## Modeling data

I was able to build fairly usable models with random forest tree regressor and extended tree regressor. For a better analysis each district should have his own model because the GPS coordinates are used in the model and it's not recomended to mix them, increasing model building time. I also included pickling capabilities so a model after computation can be unpacked and reused really fast, a unpacking function is also included.

**Original data in RED, model results in GREEN**

![model_plot](https://raw.githubusercontent.com/Simao-Lopes/Fire-Project/main/Presentation/Graphs/transferir.png)

### Folders list

1. Models, this folder contains the resgression results and is defined as a target to save computed models. They are not included because of github size restrictions.

2. NEW_DATA, this folder contains the raw fires data.

3. Presentatio, conclusions of the fire analysis in powerpoint presentation, all graphs inside their respective folder.

4. Research, all usefull research papers that I had to research.


### Python files

1. 01 -Main dataset manipulation.ipynb - This jupyter notebook cleans our data to the best possible and valid shape so we can treat them on tableau or other app, after the proccess everything is saved to a csv and a MYSQL database for further use.
2. 02 - Modeling Data.ipynb - In this notebook I import just the relevant columns from MySQL database, treat, scale and make models. It's recommended to make individual models for each district, during my process of analysis I used the top 5 CO2 ofenders to test and scoring the models. **To change districts just change the where clause on the sql query.**

```sql

'''query = select lat, lon,duration, area_total, alert_date,relative_humidity,wind_intensity,precipitation, ffmc, 
        dc,isi,dmc,avg_altitude,avg_inclination,rvdendity,cosn5variety 
        from 
        fires_clean 
        where district in ('Viana do Castelo', 'Viseu', 'Bragança', 'Guarda', 'Vila Real')'''
```
3. 03 - Hypothesis Formulation.ipynb - This notebook has my main question hypothesis calculations and mean duration safe ranges for Portugal and top 5 CO2 offender districts.


## Credits

1. Nuzulul Khairu Nissa, The Experiment of Forest Fires Prediction using Deep Learning -https://medium.com/mlearning-ai/the-experiment-of-forest-fires-prediction-using-deep-learning-d537e8c8e3a2
2. Fire Weather Index (FWI) System - https://www.nwcg.gov/publications/pms437/cffdrs/fire-weather-index-system
3. Jorge Miguel Gomes, A repository for ICNF data - https://github.com/vostpt/ICNF_DATA
4. Paulo Cortez & Anibal Morais, A Data Mining Approach to Predict Forest Fires using Meteorological Data 
5. Joana da Fonseca Valente, Modelação do fogo florestal e os seus impactes na qualidade do ar.



**Disclaimer:** Academic project only, not for media use. Use the data freely.
