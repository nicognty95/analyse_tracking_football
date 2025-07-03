# Analyse de données de tracking en football

## Objectif  
Exploiter des données de tracking haute fréquence pour analyser en profondeur la performance individuelle d’un joueur sur un match donné, en extrayant des indicateurs quantifiables et visuellement interprétables à partir de positions spatio-temporelles.

## 📂 Données  
- **Fichier de tracking brut** : coordonnées (x, y) des joueurs et du ballon à chaque instant  
- **Échantillonnage temporel** : suffisant pour calculer vitesses et accélérations  
- **Structure** : colonne temps + paire de colonnes x/y par entité  

## Prétraitement  
1. Extraction et réorganisation des coordonnées par entité  
2. Normalisation spatiale sur terrain standard FIFA (105 × 68 m)  

## Méthodologie  
Calcul des métriques suivantes pour chaque joueur, à partir des dérivées premières (vitesse) et secondes (accélération) des positions :  
- **Distance totale parcourue**  
- **Vitesse moyenne & maximale**  
- **Nombre et distance des sprints** (> 7 m/s)  
- **Distance à haute intensité** (> 5,5 m/s)  
- **Accélération maximale**  
- **Position moyenne**  
- **Surface couverte** (via `ConvexHull`)  
- **Implication** (proximité au ballon par frame)  
- **Efficience** (implication / distance)  

## Visualisations  
- **Heatmaps 2D** (histogramme) & **heatmaps lissées** (KDE)  
- **Contours de densité** pour comparer zones d’activité  
- **Tableau synthétique** récapitulatif des métriques  

## Outils  
- **Python** (Colab)  
- **pandas**, **numpy**, **scipy**, **matplotlib**  
- **ConvexHull** (surface couverte)  
- **gaussian_kde** (densité spatiale)  
- **mplsoccer** (représentation du terrain)  

## Exemple de résultats (Player17)  
- Distance parcourue : 10,3 km  
- Vitesse max : 31,2 km/h  
- Sprints détectés : 235  
- Accélération max : 7,16 m/s²  
- Position moyenne : couloir gauche  
- Zone d’influence : rôle relayeur / milieu latéral pressing  
- Implication : contacts fréquents avec le ballon  
- Bon ratio efficience / volume de course  

**Profil-type** : milieu “box-to-box” à haute intensité, essentiel en transitions et pressing à la perte.

## Cas d’usage  
- Analyse post-match ou post-séquence  
- Suivi longitudinal des efforts et de l’implication  
- Comparaison intra/inter-joueurs sur critères objectifs  
- Outil de profiling de performance complémentaire aux stats événementielles

![Carte des tirs]([https://raw.githubusercontent.com/tonrepo/football-datascience/main/images/shot_map.png](https://mail.google.com/mail/u/0?ui=2&ik=b9c7ebe638&attid=0.1&permmsgid=msg-a:r-1316748580671123508&th=197bcf72f19e1a0e&view=fimg&fur=ip&permmsgid=msg-a:r-1316748580671123508&sz=s0-l75-ft&attbid=ANGjdJ9329dym-207TJFiTh1sudlDOISpaHlmpwyF6XSvvuEsEdYV1ogHkmWen2NqZ9wIxAOTffe-Qd7JF5Ccq0-sxG43PQUZp9Epc6TvkgP44Tq-WSgRckhWy7x25A&disp=emb&realattid=ii_mci0c1ky0&zw))

