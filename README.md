# Évaluation de modules de localisation pour véhicule autonome (ROS 2 / CARLA)

## Contexte
Projet d’évaluation et d’intégration de briques de localisation multi-capteurs sur une Renault Zoé robotisée et son jumeau numérique CARLA/ROS. :contentReference[oaicite:2]{index=2}

## Objectifs
- État de l’art : GNSS/INS, LiDAR-SLAM, Visual-Inertial Odometry (VIO), approches IA.
- Installation, calibration et intégration de modules de localisation sous ROS 2 (réel + simulation CARLA).
- Fusion multi-capteurs et analyse de l’apport de chaque capteur.
- Évaluation : précision de pose, latence, continuité/robustesse.

## Stack / Outils
- ROS 2, Python, Linux
- CARLA (simulation)
- (Optionnel selon setup) Autoware + dépôts open-source :contentReference[oaicite:3]{index=3}

## Capteurs (plateforme réelle)
- Caméra Intel RealSense D435i
- Récepteur GNSS
- Centrale inertielle SBG Ellipse-E
- LiDAR Hesai Pandar XT-32
- Encodeurs de roues, vitesse, angle de direction :contentReference[oaicite:4]{index=4}

## Méthodologie (résumé)
1. Revue bibliographique + choix des modules.
2. Installation / calibration / intégration ROS 2.
3. Déploiement sur jumeau numérique CARLA + (si applicable) tests réel.
4. Mesures & comparaison : pose, latence, continuité.
5. Analyse : impact de chaque capteur sur la précision.



➡️ **Énoncé / cahier des charges (PDF)** : [ProjetsSMART25-26_ToSyMA_EZ_sujet3-4.pdf](ProjetsSMART25-26_ToSyMA_EZ_sujet3-4.pdf)

## Résultats
Tableaux/graphes (précision, latence, continuité) et comparaisons de méthodes.  
Notebook EKF (démo fusion) : [test_ekf.ipynb](test_ekf.ipynb)


## Auteurs
- Touwende OUEDRAOGO

## Références
- Sujet du projet / plateforme ToSyMA – Université de Lille :contentReference[oaicite:5]{index=5}

## Démo vidéo (CARLA → ROS 2 → RViz)

Une vidéo de démonstration ici :

Elle présente :
- Une **simulation CARLA enregistrée puis rejouée** via **ROS 2**, visualisée dans **RViz** (véhicule se déplaçant sur le scénario).
- Un exemple simple de **fusion de capteurs** et une **comparaison** entre :
  1) **Odométrie seule**  
  2) **Odométrie + IMU + LiDAR**
- L’affichage du *
*nuage de points LiDAR** dans RViz, ainsi que l’évolution de la trajectoire/pose estimée.

https://github.com/user-attachments/assets/da7d7c57-9a8b-4318-9f9b-78eda55cb568

Img : 
<img width="1311" height="641" alt="Screenshot from 2025-12-04 21-14-44" src="https://github.com/user-attachments/assets/95580bf7-3f11-4388-a766-4d02e38dd873" />

