![logo_fire](https://raw.githubusercontent.com/Simao-Lopes/Fire-Project/main/Presentation/Background/1817788.jpg)


Fires in Portugal 
======


## The problem

In Portugal, every year we have a problem with fires. Most of the time it's due either to poor resource allocation, or insufficient resources. I try to understand if it's possible to create a model to predict with acceptable accuracy the burnt area. In the process of cleaning and studying the dataset, I found many interesting things that are explained in the presentation. Feel free to use everything on this repository for your projects.

I will develop this continuously and feed it with new data.

### Folders list

1. Models, this folder contains the resgression results and is defined as a target to save computed models. They are not included because of github size restrictions.

2. NEW_DATA, this folder contains the raw fires data.

3. Presentatio, conclusions of the fire analysis in powerpoint presentation, all graphs inside their respective folder.

4. Research, all usefull research papers that I had to research.


### Python files

1. 01 -Main dataset manipulation.ipynb - This jupyter notebook cleans our data to the best possible and valid shape so we can treat them on tableau or other app, after the proccess everything is saved to a csv and a MYSQL database for further use.
2. 02 - Modeling Data.ipynb - In this notebook I import just the relevant columns from MySQL database, treat, scale and make models. It's recommended to make individual models for each district, during my process of analysis I used the top 5 CO2 ofenders to test and scoring the models. **To change districts just change the where clause on the sql query.**

'''select lat, lon,duration, area_total, alert_date,relative_humidity,wind_intensity,precipitation, ffmc, 
        dc,isi,dmc,avg_altitude,avg_inclination,rvdendity,cosn5variety 
        from 
        fires_clean 
        where district in ('Viana do Castelo', 'Viseu', 'Bragança', 'Guarda', 'Vila Real')'''




##### Tableau public: [Link](https://public.tableau.com/app/profile/sim.o6187/viz/NewFire-Project/Bush)

Disclaimer: Academic project only, not for media use. Use the data freely.
