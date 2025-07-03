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

![Heatmap des réceptions](assets/heatmap.png)
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



