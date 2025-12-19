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

## Organisation du repo
- `docs/` : rapport, notes, schémas
- `src/` : scripts ROS 2 (launch, nodes, config)
- `configs/` : paramètres capteurs / fusion / mapping
- `eval/` : scripts d’évaluation (métriques, plots)
- `data/` : (vide) instructions pour données (ne pas commit de données lourdes)

## Résultats
> À compléter : tableaux/graphes (précision, latence, continuité), comparaisons de méthodes.

## Auteurs
- Ton nom (+ coéquipier si besoin)

## Références
- Sujet du projet / plateforme ToSyMA – Université de Lille :contentReference[oaicite:5]{index=5}
