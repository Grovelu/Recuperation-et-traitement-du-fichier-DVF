# Fonction de téléchargement et de traitement des fichiers DVF

Cette fonction permet de télécharger et de traiter les fichiers DVF pour les années spécifiées, en filtrant les données en fonction de certaines conditions. La fonction effectue les étapes suivantes pour chaque année :

1. Téléchargement du fichier DVF compressé au format CSV depuis le site web data.gouv.fr.
2. Suppression des lignes qui n'ont pas la valeur "Vente" dans la colonne "nature_mutation".
3. Suppression des lignes ayant des valeurs nulles dans la colonne "surface_reelle_bati".
4. Suppression des lignes ayant des valeurs nulles dans la colonne "valeur_fonciere".
5. Suppression des lignes qui n'ont pas la valeur "Maison" ou "Appartement" dans la colonne "type_local".
6. Suppression des lignes ayant des valeurs nulles dans les colonne 'longitude' et 'latitude'

Enfin, les données filtrées pour chaque année sont concaténées dans un seul fichier CSV appelé "full_dvf.csv".

## Utilisation

Pour utiliser cette fonction, vous devez d'abord importer les bibliothèques nécessaires et définir la liste des années à télécharger :

```python
import pandas as pd
import requests
import time
import gzip
import io

years = [2017, 2018, 2019, 2020, 2021, 2022]
