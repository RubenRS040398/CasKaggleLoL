# Pràctica Kaggle APC UAB 2022-23
### Nom: Rubén Ramos Segarra
### DATASET: (LoL) League of Legends Ranked Games
### URL: [kaggle](https://www.kaggle.com/datasets/datasnaek/league-of-legends?resource=download)
## Resum
El dataset utilitza dades extretes de més de 50.000 partides de LoL, acompanyades d'uns fitxers JSON que conté informació dels noms dels campions i inhibidors (aquesta prové d'una pàgina web de tercers).
Tenim 51.490 dades amb 61 atributs. La majoria dels atributs són numèrics, mentre que la resta són categòrics (winner, firstBlood, firstTower, firstInhibitor, firstBaron, firstDragon, firstRiftHerald, t1_riftHeraldKills, t2_riftHeraldKills).
### Objectius del dataset
No s'especifica la finalitat d'aquest, pero matissa que pot tenir diverses utilitats. En aquest cas s'ha decidit predir sobre quin es l'equip guanyador (l'atribut objectiu es winner).
## Experiments
Durant aquesta pràctica hem realitzat diferents experiments.
### Preprocessat
S'han realitzat les següents proves
* Mostreig de dades (massa dades, duplicades, poques...).
* Conversió de dades (dades numèriques, categòriques, ordinals).
* Neteja de dades (dades errònies, perdudes, outliers...).
* Normalització/Estandardització de dades.
### Model
Sobre un mateix model seleccionat a través d'uns criteris (més informació al Notebook), s'ha aplicat SVM lineal amb diversos mètodes. Aquests han estat els resultats.
| Model | Hiperparàmetres | Accuracy | Precision | Recall | Temps |
| ----- | --------------- | -------- | --------- | ------ | ----- |
| Sense Cross-Validation | Per defecte | 0.97 | 0.96 | 0.97 | 0:00:22 |
| Amb Cross-Validation (PCA: `n_components=2`) | Per defecte | 0.91 | 0.93 | 0.90 | 0:00:07 |
| Amb Cross-Validation (PCA: `n_components=3`) | Per defecte | 0.91 | 0.93 | 0.90 | 0:00:07 |
| Amb Cross-Validation (PCA: `n_components=4`) | Per defecte | 0.93 | 0.95 | 0.91 | 0:00:06 |
| Amb Cross-Validation (PCA: `n_components=5`) | Per defecte | 0.93 | 0.95 | 0.91 | 0:00:06 |
| Amb Cross-Validation (PCA: `n_components=6`) | Per defecte | 0.93 | 0.95 | 0.91 | 0:00:06 |
| Amb Cross-Validation (PCA: `n_components=7`) | Per defecte | 0.93 | 0.94 | 0.91 | 0:00:06 |
| Amb Cross-Validation (PCA: `n_components=8`) | Per defecte | 0.93 | 0.94 | 0.91 | 0:00:07 |
| Amb Cross-Validation (PCA: `n_components=9`) | Per defecte | 0.93 | 0.94 | 0.91 | 0:00:07 |
| Amb Cross-Validation (PCA: `n_components=10`) | Per defecte | 0.93 | 0.94 | 0.91 | 0:00:07 |
| Amb Cross-Validation (Grid Search) | `param_grid = {'C': [0.1, 1, 10], 'kernel': ['linear']}` | 0.96 | 0.96 | 0.97 | 0:03:49 |
## Conclusions
El millor model que s'ha aconseguit ha estat el primer, on s'ha obtingut un 97% d'accuracy, un 96% de precision i un 97% de recall (més informació al Notebook).
## Idees per treballar en un futur
Crec que seria interesant indagar més en explorar altres mètodes sobre el mateix model, sobretot en Grid Search CV ja que realitza una exploració a fons sobre diversos hiperparàmetres (s'havia intentat amb kernel radial però donat que l'execuciò trigava molt s'ha decantat per lineal).