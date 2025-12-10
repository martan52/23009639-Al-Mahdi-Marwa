# 📘 Compte Rendu du Projet  
## Analyse des Métiers de l’Ingénierie & Pipeline Data Science

---

## 📑 Sommaire
1. [Introduction](#introduction)  
2. [Objectif du Projet](#objectif-du-projet)  
3. [Description des Données](#description-des-données)  
4. [Pipeline Méthodologique](#pipeline-méthodologique)  
   - 4.1 [Acquisition & Simulation](#41-acquisition--simulation)  
   - 4.2 [Nettoyage des données](#42-nettoyage-des-données)  
   - 4.3 [Analyse exploratoire (EDA)](#43-analyse-exploratoire-eda)  
   - 4.4 [Séparation des données](#44-séparation-des-données)  
   - 4.5 [Modélisation (Random Forest)](#45-modélisation-random-forest)  
   - 4.6 [Évaluation du modèle](#46-évaluation-du-modèle)  
5. [Analyse Théorique : Random Forest](#analyse-théorique--random-forest)  
6. [Conclusion Générale](#conclusion-générale)

---

## 1. Introduction

Ce projet s'inscrit dans une démarche d’analyse métier appliquée au domaine de la data science et de l’ingénierie.  
Il vise à comprendre et implémenter les différentes étapes d’un pipeline complet de Machine Learning, depuis la préparation des données jusqu’à l’évaluation du modèle.

Le projet s'appuie sur un notebook Python et une analyse approfondie expliquant chaque étape de manière pédagogique et professionnelle.

---

## 2. Objectif du Projet

L’objectif principal est de construire un modèle de prédiction capable de **distinguer les tumeurs bénignes et malignes** dans un contexte médical sensible.

Les objectifs spécifiques sont :
- Développer un assistant IA pour le diagnostic.
- Prioriser la sécurité du patient en minimisant les **faux négatifs**.
- Appliquer un pipeline complet : nettoyage → exploration → modélisation → évaluation.

---

## 3. Description des Données

Le dataset utilisé est le **Breast Cancer Wisconsin Dataset**, contenant des mesures microscopiques de cellules.

- **30 features** quantitatives  
- **1 variable cible :**
  - `0` : Malin  
  - `1` : Bénin  
- Simulation de données manquantes : **5 % de NaN ajoutés** pour se rapprocher d’un cas industriel réel.

---

## 4. Pipeline Méthodologique

### 4.1 Acquisition & Simulation

Les données sont importées via `sklearn.datasets`.  
Une corruption volontaire de 5 % des valeurs a été effectuée pour simuler des données réelles contenant du bruit.

---

### 4.2 Nettoyage des données

L’imputation est réalisée via :

```python
SimpleImputer(strategy='mean')

