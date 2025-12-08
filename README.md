# TL;DR
Deze repository bevat een complete pipeline om ruwe spel- of sessielogs om te zetten naar gebruikersprofielen en clusters:
normalisation_database.ipynb verwerkt ruwe logs tot sessiedata.
grouped.csv bevat per gebruiker geaggregeerde statistieken.
proof_of_concept.ipynb voert clustering uit (Gaussian Mixture Models) en visualiseert gebruikersprofielen.
Gebruik de notebooks in bovenstaande volgorde om een volledig overzicht te krijgen van het gedrag van spelers en hen automatisch in clusters in te delen.

## Overzicht van de pipeline
De datastroom verloopt als volgt:
```
test_data.txt → normalisation_database.ipynb → grouped.csv → proof_of_concept.ipynb
```
**Doel**: ruwe data verwerken naar sessies, sessies aggregeren naar gebruikersniveau en vervolgens gebruikers clusteren op basis van gedrag.

## 2.Bestanden
**test_data.txt**
Bevat een overzicht van het verwachte aantal sessies per gebruiker.
Wordt gebruikt om de output uit de normalisatiestap te controleren.
**normalisation_database.ipynb**
Zet ruwe logs om naar gestructureerde sessiedata.
Belangrijk:
- Mappen van acties naar categorieën
- Bepalen van fouten, correcte acties en tijdsbesteding
- Opbouwen van sessies per gebruiker
- Exporteren van sessiedata naar CSV
**grouped.csv**
Bevat per gebruiker een geaggregeerde set kenmerken, waaronder:
- Aantal sessies
- Ratio voltooide sessies
- Mediane tijd per actie
- Foutenratio’s
- Categoriegebonden tijd- en foutmaten
- Efficiëntiematen
Deze dienen als input voor de clustering.

**proof_of_concept.ipynb**
Voert de clusteringanalyse uit:
- Inladen en opschonen van features
- Schalen met StandardScaler
- Vergelijken van modellen via BIC en Silhouette
- Trainen van een Gaussian Mixture Model
- Visualisatie met PCA
- Indelen van nieuwe gebruikers met `predict` en `predict_proba`

## 3. Installatie en vereisten
Benodigde libraries:
```
pip install pandas numpy scikit-learn matplotlib seaborn
```
Run de notebooks in bijvoorbeeld:
- Jupyter Notebook
- JupyterLab
- Visual Studio Code (met Python-extensie)
## 4. Pipeline uitvoeren
**Stap 1: Normaliseren**
Open en run:
```
normalisation_database.ipynb
```
Hiermee wordt de sessiedata gegenereerd.
**Stap 2: Groeperen**
Groepeer per gebruiker op basis van de sessiedata en genereer:
```
grouped.csv
``` 
**Stap 3: Clustering**
Open:
```
proof_of_concept.ipynb
```
Run alle cellen en bekijk:
- Modelselectie
- Clusterstructuur
- Visualisaties
- Resultaten voor nieuwe gebruikers


