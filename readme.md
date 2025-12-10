# 🚀 Projet Data Science : Détection du Cancer du Sein  
Analyse & Pipeline Machine Learning complet

![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![Python](https://img.shields.io/badge/Python-3.10-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![ML](https://img.shields.io/badge/Model-RandomForest-green)

---

## 📑 SOMMAIRE

1. [Contexte Général](#1-contexte-général)  
2. [Objectifs du Projet](#2-objectifs-du-projet)  
3. [Dataset & Structure](#3-dataset--structure)  
4. [Pipeline Machine Learning](#4-pipeline-machine-learning)  
5. [Schéma Général du Pipeline](#5-schéma-général-du-pipeline)  
6. [Analyse Théorique Synthétique](#6-analyse-théorique-synthétique)  
7. [Résultats & Interprétation](#7-résultats--interprétation)  
8. [Limites & Améliorations](#8-limites--améliorations)  
9. [Installation & Exécution](#9-installation--exécution)  
10. [Arborescence du Projet](#10-arborescence-du-projet)  
11. [Requirements](#11-requirements)  
12. [Licence](#12-licence)

---

# 1. Contexte Général

Ce projet s'inscrit dans un cadre médical où l’IA est utilisée comme **outil d’aide au diagnostic**.  
L'objectif est de prédire si une tumeur est :

- **0 – Maligne (cancer)**
- **1 – Bénigne**

Les conséquences d’une mauvaise classification imposent un focus métier clair :

> 🎯 **Objectif principal : minimiser les Faux Négatifs (FN).**

---

# 2. Objectifs du Projet

### 🎯 Objectif global  
Construire un modèle fiable capable de classer correctement les tumeurs.

### 🔍 Objectifs détaillés :
- Nettoyer et préparer un dataset contenant des valeurs manquantes.
- Réaliser une EDA complète.
- Appliquer un pipeline ML standardisé.
- Utiliser un **Random Forest** pour la classification.
- Évaluer les performances selon des métriques pertinentes.
- Identifier les limites et proposer des pistes d’amélioration.

---

# 3. Dataset & Structure

Dataset utilisé :  
📌 **Breast Cancer Wisconsin Dataset** (Sklearn)

### 🧬 Description :
- **30 variables** représentant des caractéristiques cellulaires.
- Toutes quantitatives.
- Les images ne sont pas utilisées, seulement leurs descripteurs mathématiques.

### 🛠 Simulation de données manquantes :
Afin de se rapprocher d’un cas réel, **5 % des données ont été volontairement corrompues avec des NaN**.

---

# 4. Pipeline Machine Learning

Étapes complètes du pipeline :

### ✔ Acquisition
Chargement du dataset depuis sklearn.

### ✔ Nettoyage
- Utilisation d’un `SimpleImputer(strategy="mean")`
- Remplacement des valeurs manquantes par la moyenne.

⚠ **Attention : Data Leakage**
> L’imputation devrait être effectuée APRÈS le split train/test, pas avant.

### ✔ Analyse exploratoire (EDA)
- Statistiques descriptives
- Analyse de la distribution
- Corrélation entre variables (radius, perimeter, area très corrélées)

### ✔ Split Train/Test
```python
train_test_split(test_size=0.2, random_state=42)
                 ┌────────────────────────────────┐
                 │      Acquisition Dataset       │
                 └────────────────────────────────┘
                               │
                               ▼
                 ┌────────────────────────────────┐
                 │  Simulation données manquantes │
                 └────────────────────────────────┘
                               │
                               ▼
                 ┌────────────────────────────────┐
                 │      Nettoyage & Imputation    │
                 └────────────────────────────────┘
                               │
                      (Data Leakage Warning)
                               │
                               ▼
                 ┌────────────────────────────────┐
                 │         Analyse EDA            │
                 └────────────────────────────────┘
                               │
                               ▼
                 ┌────────────────────────────────┐
                 │     Train / Test Split         │
                 └────────────────────────────────┘
                               │
                               ▼
                 ┌────────────────────────────────┐
                 │     Modèle Random Forest       │
                 └────────────────────────────────┘
                               │
                               ▼
                 ┌────────────────────────────────┐
                 │  Évaluation + Matrice Confusion│
                 └────────────────────────────────┘
