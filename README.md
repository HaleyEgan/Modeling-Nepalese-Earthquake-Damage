# Modeling Earthquake Building Damage - Nepal

### Introduction
In 2015 there was a 7.8 magnitude earthquake near Gorkha, Nepal. The damage devastated the community. About 9,000 people were killed, millions of people lost their homes, and there was about $10 billion in damage. The Nepalese government is still working to rebuild the affected area. During the years of recovery, the National Planning Commission, Kathmandu Living Labs, and the Central Bureau of Statistics have collected one of the largest post-disaster datasets ever. This data contains valuable information on earthquake structural damage and socio-economic impacts. 

This project was inspired by the Richter’s Predictor: Modeling Earthquake Damage data challenge hosted by DrivenData.org. The project harnesses the dataset on the 2015 Nepalese earthquake to model and predict the level of damage buildings suffered as a result of the earthquake. The insights gained from these predictions can be applied to future earthquakes, and ideally in preventing this level of devastation and fatalities from occurring again. 

![earthquakepicture](https://github.com/HaleyEgan/Modeling-Nepalese-Earthquake-Damage/blob/main/150427-nepal-quake-jhc-1326.jpg)

### Data
The data comes from the 2015 Nepal Earthquake Open Data Portal (https://eq2015.npc.gov.np/#/https://eq2015.npc.gov.np/#/). The data contains 38 features, including structural information like number of floors, age of building, and type of foundation, as well as ownership status, building use, and number of families who lived there, etc. Eight of the 38 features are categorical, resulting in mixed data types, which is addressed in the Data Cleaning & Preparation section. 

Each building has a unique id, and has a corresponding damage grade (1 = low damage, 2 = medium damage, 3 = complete destruction). This is a large dataset, with nearly 260,601 individual buildings (rows) documented. The features are used to predict the damage level of each building on the test data set. 

### Analysis
Bayesian Data Analysis techniques are used to model and predict this data set. Why? Linear Discriminant Analysis (LDA), Quadratic Discriminant Analysis (QDA), and Logistic Regression are the models used in this report to predict building damage levels. The data is processed and modeled in Python, using packages such as pymc, pandas, numpy, scipy and sklearn. 

#### Priors
The two sets of priors were used for each model. The first set of priors are gathered from initial observations of building damage through photos, videos, and articles of the 2015 earthquake. Based on this prior knowledge, it was initially observed that very few buildings experienced no or little damage (damage grade 1). Most buildings experienced some level of damage (damage grade 2), and many (more than a few, but less than ‘most’) buildings experienced complete destruction (damage grade 3). Based on this prior knowledge, the damage grades were given the following prior value: damage grade 1 = 5%, damage grade 2 = 70%, damage grade 3 = 25%.   

The second set of priors are used as a comparison to the first priors, and are calculated from the observed proportion of building damage per level. While this method is not based on ‘prior knowledge’, it can help in the understanding of how well the initial priors performed. For damage grade 1, the observed proportion (buildings per grade/total buildings) for the training dataset is 0.0965, about 9.7%. For damage grade 2, the observed proportion for the training set is 0.5695, or about 57%. For damage grade 3, the observed proportion for the training set is 0.3339, or about 33.4%. 
