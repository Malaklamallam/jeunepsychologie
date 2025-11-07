# Accès aux soins psychologiques pour les jeunes en Seine-Saint-Denis (93)

## Introduction
Ce projet vise à explorer l’accès aux soins psychologiques et psychiatriques pour les jeunes (12-25 ans) en Seine-Saint-Denis (93).  
La santé mentale des jeunes constitue un enjeu majeur sur ce territoire caractérisé par une forte densité de population, des inégalités sociales marquées, et un déficit historique d’infrastructures de soins.  
Notre objectif est de construire un écosystème statistique et visuel permettant de comprendre :
- l’offre de soins (structures disponibles),
- la consommation de soins (indicateurs indirects via médicaments),
- les déséquilibres territoriaux dans le département.



## Sources de données (Data brutes)

| Source | Type de données | Description | Année | Lien |

PTSM-93 (Projet Territorial de Santé Mentale – Seine-Saint-Denis)
Données structurelles
Offre de soins psychiatriques, répartition des structures (CMP, hôpitaux, dispositifs jeunes)
2024
[sante.gouv.fr - PTSM-93](https://sante.gouv.fr/IMG/pdf/projet_territorial_sante_mentale_93.pdf)


Observatoire Départemental des Données Sociales (ODDS93)
Données de consommation | Taux de consommation de médicaments psychotropes (antidépresseurs, anxiolytiques) chez les jeunes 12-24 ans
2022
[ODDS93 – Santé mentale des jeunes](https://ressources.seinesaintdenis.fr/IMG/pdf/1664273_santementalejeunesrosny_050525-3.pdf)


Capitalisation Santé / ARS Île-de-France
Données qualitatives
Présentation de la Plateforme Jeunesse & Santé Mentale (PJSM) 93
2024
[Capitalisation Santé – PJSM 93](https://www.capitalisationsante.fr/capitalisations/plateforme-jeunesse-sante-mentale-pjsm-nord-ouest-de-la-seine-saint-denis-93/)



## Data tables

### 1️ Offre de soins pour les jeunes (`offre_soins_jeunes_93.csv`)
| Commune | Année | Structure_Type | Tranche_Age | Nombre_Structure | Source |
| Nord-Ouest 93    | 2024 | PJSM | 12-25 | 1 | Capitalisation Santé |
| Aulnay-sous-Bois | 2024 | CMP enfants et adolescents | 0-18 | 22 | GHT GPNE |
| Saint-Denis      | 2024 | CMP enfants et adolescents | 0-18 | 18 | PTSM-93 |
| Montreuil        | 2024 | CMP jeunes et hôpital de jour | 12-25 | 16 | PTSM-93 |
| Bobigny          | 2024 | CMP enfants et adolescents | 0-18 | 15 | PTSM-93 |
| Total 93         | 2024 | Structures de soins psychologiques et psychiatriques | 0-25 | 72 | ARS Île-de-France |


### 2️ Consommation médicamenteuse chez les jeunes (`consommation_medicamenteuse_jeunes_93.csv`)
| Commune | Année | Classe_Médicaments | Taux_pour_1000 | Tranche_Age |
| Seine-Saint-Denis | 2022 | Antidépresseurs | 22 | 12-24 |
| Seine-Saint-Denis | 2022 | Anxiolytiques   | 10 | 12-24 |
| Aulnay-sous-Bois  | 2022 | Antidépresseurs | 25 | 12-24 |
| Montreuil         | 2022 | Antidépresseurs | 27 | 12-24 |
| Saint-Denis       | 2022 | Antidépresseurs | 24 | 12-24 |
| Bobigny           | 2022 | Antidépresseurs | 18 | 12-24 |



## Structures visuelles et représentations

### Objectifs des visualisations
1. Comparer l’offre de soins entre communes (ex: nombre de structures pour jeunes).
2. Identifier les disparités dans la consommation médicamenteuse(ex: taux d’antidépresseurs).
3. Mettre en évidence la corrélation possible entre densité d’offre et consommation.




### Choix des représentations (inspiré de D3.js)
| Type de représentation | Question à laquelle elle répond | Exemple D3 |

Carte choroplèthe des communes du 93 (valeurs = taux pour 1 000 jeunes)  
Où les jeunes ont-ils le plus recours aux médicaments psychotropes ? [Choropleth Map](https://observablehq.com/@d3/choropleth) 

Diagramme en barres comparant le nombre de structures
Quelles communes offrent le plus de structures? 
[Bar Chart](https://observablehq.com/@d3/bar-chart) 

Graphique combiné (scatter) entre nombre de structures et taux de médicaments
Existe-t-il une corrélation entre offre et consommation?
[Scatter Plot](https://observablehq.com/@d3/scatterplot)



## Interactions avec l’environnement

- des filtres : possibilité de filtrer par commune, type de médicament ou tranche d’âge.  
- hover : affichage des valeurs exactes et sources.  
- Slider temporel si ajout d’autres années plus tard.  
- Lien entre graphiques : cliquer sur une commune sur la carte met à jour le graphique de structures.
(Outils: D3.js, ObservableHQ, tableau de bord avec HTML/CSS/JS.)  



## Écosystème de connaissances
- Données quantitatives et qualitatives sur l’offre et la demande de soins.  
- Données géographiques (communes du 93).  
- Données institutionnelles (PTSM, ARS, Observatoire).  
- Visualisations interactives.  
- Acteurs institutionnels (jeunes, professionnels, structures, ARS, département).



