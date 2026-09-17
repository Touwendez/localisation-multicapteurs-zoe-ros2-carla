# Localisation multicapteurs pour véhicule autonome

## ROS 2, CARLA et évaluation EKF sur plateforme Renault Zoé robotisée

Ce projet porte sur l'étude, l'intégration et l'évaluation de méthodes de localisation pour véhicule autonome sous ROS 2 et CARLA.

Le travail associe un état de l'art des approches GNSS/INS, LiDAR-SLAM et Visual-Inertial Odometry, l'intégration de capteurs sur une Renault Zoé robotisée et son jumeau numérique, ainsi qu'une évaluation expérimentale de plusieurs configurations EKF.

## Technologies

- ROS 2
- CARLA
- Python
- Linux
- Jupyter Notebook
- NumPy, pandas, Matplotlib
- Filtre de Kalman étendu (EKF)
- RViz

## Expérience EKF disponible

Le notebook `test_ekf.ipynb` compare trois configurations sur le même rejeu CARLA :

1. odométrie seule ;
2. IMU seule ;
3. fusion odométrie + IMU.

La sortie `/odometry/filtered` est comparée à la référence `/carla/hero/odometry`.

### Résultats du notebook

| Configuration | RMSE 2D |
|---|---:|
| Odométrie seule | 0,0000 m |
| IMU seule | 214,3412 m |
| Odométrie + IMU | 7,4464 m |

Ces valeurs doivent être interprétées comme une démonstration du protocole d'évaluation. L'odométrie CARLA sert également de référence, ce qui explique l'erreur nulle du cas odométrie seule. Le cas IMU seule illustre la dérive inertielle sans correction externe.

## Plateforme et capteurs étudiés

Le projet couvre une chaîne de localisation intégrant ou étudiant :

- GNSS ;
- INS / IMU ;
- LiDAR ;
- caméra ;
- odométrie véhicule.

Le dépôt décrit notamment une caméra Intel RealSense D435i, une centrale inertielle SBG Ellipse-E et un LiDAR Hesai Pandar XT-32 pour la plateforme réelle.

## Démonstration

https://github.com/user-attachments/assets/da7d7c57-9a8b-4318-9f9b-78eda55cb568

<p align="center">
  <img width="900" alt="Démonstration ROS 2 CARLA RViz" src="https://github.com/user-attachments/assets/95580bf7-3f11-4388-a766-4d02e38dd873" />
</p>

## Point important

Le LiDAR et la caméra font partie de l'étude globale et de l'intégration multicapteurs, mais le notebook EKF public ne compare actuellement que odométrie, IMU et odométrie + IMU. Le README évite donc d'affirmer qu'une fusion LiDAR ou caméra est démontrée dans cette expérience.

## Contenu du dépôt

- `ProjetsSMART25-26_ToSyMA_EZ_sujet3-4.pdf` : cahier des charges du projet ;
- `test_ekf.ipynb` : analyse comparative EKF ;
- `docs/methodology.md` : méthodologie ;
- `docs/results.md` : résultats ;
- `docs/limitations.md` : limites et périmètre.

## Auteur

**Touwende OUEDRAOGO**  
Master 2 SMaRT, Université de Lille
