Analyse de données de tracking en football
Objectif
Ce projet vise à exploiter des données de tracking haute fréquence pour réaliser une analyse individuelle approfondie des performances d’un joueur sur un match donné. L’enjeu est d’extraire des indicateurs quantifiables et visuellement interprétables à partir de positions spatio-temporelles, en intégrant à la fois des métriques physiques, de présence territoriale, et d’implication dans le jeu.

Données
Fichier de tracking brut : coordonnées (x, y) des joueurs et du ballon à chaque instant

Échantillonnage temporel suffisant pour calculer vitesses et accélérations

Données structurées avec une colonne temps et une paire de colonnes x/y par entité

Prétraitement :

Extraction et réorganisation des coordonnées par entité

Normalisation spatiale sur terrain standard FIFA (105x68m)

Méthodologie
Métriques calculées
Pour chaque joueur :

Distance totale parcourue

Vitesse moyenne / maximale

Nombre et distance des sprints (> 7 m/s)

Distance à haute intensité (> 5.5 m/s)

Accélération maximale

Position moyenne

Surface couverte (via ConvexHull)

Implication (proximité au ballon par frame)

Efficience (implication / distance)

Toutes les métriques sont calculées à partir des dérivées premières (vitesse) et secondes (accélération) des positions.

Visualisations
Heatmaps 2D classiques (histogramme) et heatmaps lissées (KDE)

Contours de densité pour comparer les zones d’activité entre joueurs

Résumés chiffrés sous forme de tableau synthétique

Outils
Python (Colab)

pandas, numpy, scipy, matplotlib

ConvexHull (surface couverte)

gaussian_kde (densité spatiale)

mplsoccer pour la représentation du terrain

Exemple de résultats
Sur un joueur donné (Player17) :

10.3 km parcourus

Vitesse max : 31.2 km/h

235 sprints détectés

Accélération max : 7.16 m/s²

Position moyenne dans le couloir gauche

Zone d’influence cohérente avec un rôle de relayeur ou milieu latéral pressing

Implication élevée (contacts fréquents avec le ballon)

Bon ratio efficience/volume de course

Ce profil est typique d’un milieu “box-to-box” à haute intensité, utile dans les phases de transition et le pressing à la perte.

Cas d’usage
Analyse post-match ou post-séquence

Suivi longitudinal des efforts et de l’implication

Comparaison intra/inter-joueurs sur critères objectifs

Outil de profiling de performance complémentaire aux stats événementielles
