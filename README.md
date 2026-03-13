# Estimation de Pose et Analyse Cinématique : Application au Tennis

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![MMPose](https://img.shields.io/badge/MMPose-OpenMMLab-red?style=flat)
![Colab](https://img.shields.io/badge/Google_Colab-Compatible-orange?style=flat&logo=google-colab)

Ce projet a été réalisé dans le cadre de notre **Double Licence Mathématiques-Informatique**. Il vise à analyser le geste technique du coup droit au tennis en utilisant des techniques de vision par ordinateur (Pose Estimation) et d'analyse cinématique.

## Auteurs
* **Bastien BABU**
* **Jérémy CLAUX**
* **Pierre PARODI**
* **David QASSEMYAR**

---

## Description du Projet

L'objectif est d'extraire des données biomécaniques précises à partir d'une simple vidéo de tennisman, puis de modéliser le mouvement pour analyser la vitesse et prédire la trajectoire future du bras.

### Fonctionnalités principales :
1.  **Détection de pose (Human Pose Estimation) :** Utilisation du modèle **HRNet** (High-Resolution Net) via la librairie MMPose pour identifier 17 points clés (keypoints) du corps.
2.  **Analyse Cinématique :**
    * Calcul des vitesses et accélérations du poignet.
    * Visualisation des trajectoires en 2D.
    * Lissage des données par moyenne mobile pour réduire le bruit de détection.
3.  **Prédiction :** Tentative de prédiction de la trajectoire future du mouvement via un réseau de neurones récurrents (**LSTM**).

### Choix Techniques :
* **Modèle :** Nous avons privilégié **HRNet** sur CPU pour sa précision spatiale et sa robustesse aux occlusions, après avoir expérimenté avec *RTMPose* (dont l'implémentation GPU s'est avérée instable sur notre environnement).
* **Données :** Traitement image par image pour garantir la stabilité des calculs cinématiques.

---

## Installation et Utilisation

Ce projet a été conçu pour tourner sur **Google Colab** afin de faciliter la gestion des dépendances complexes de `mmcv` et `mmpose`.

### Lancer le projet :
1.  Ouvrez le notebook principal : `notebooks/main_analyse_hrnet.ipynb`.
2.  Cliquez sur le badge "Open in Colab" (si vous hébergez le dépôt sur GitHub).
3.  Exécutez les cellules séquentiellement. Le script gère l'installation des librairies `mmpose`, `mmdet` et `mmcv-lite` automatiquement.

### Structure des fichiers :
* `notebooks/main_analyse_hrnet.ipynb` : Le code complet (installation, inférence, analyse graphique, LSTM).
* `notebooks/experiments/` : Contient nos tentatives d'installation de modèles GPU (RTMPose).
* `report/` : Le rapport complet du projet au format PDF avec les explications détaillées.

---

## Résultats

Nous avons réussi à :
* Générer un squelette fluide du joueur en mouvement.
* Tracer la courbe de vitesse du poignet (« la boucle » du coup droit).
* Identifier les limitations de l'analyse 2D (écrasement des perspectives faussant certains angles).

> Voir le [Rapport complet](report/Rapport_Estimation_Pose.pdf) pour les graphiques détaillés.

---

## Technologies utilisées
* **Python**
* **OpenMMLab** (MMPose, MMCV, MMDet, HRNet)
* **OpenCV** (Traitement vidéo)
* **Matplotlib** (Visualisation de données)
* **TensorFlow / Keras** (Modèle LSTM)

