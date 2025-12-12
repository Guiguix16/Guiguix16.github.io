---
title: "Kaggle – Predicting Loan Payback"
date: 2025-12-10 10:00:00 +0100
categories: [Projets personnels]
tags: [Machine learning, Python, Power BI]
image: /assets/accueil_tdb.png
description: "Pipeline ML complet et tableau de bord interactif Power BI pour la prédiction de défaut de paiement dans le challenge Kaggle Predicting Loan Payback."
---

# Kaggle – Predicting Loan Payback  
*Playground Series*

Ce projet personnel m’a permis de travailler un cas d’étude complet en data, en adoptant une démarche volontairement orientée machine learning en premier lieu, avant de restituer les résultats sous forme de tableau de bord Power BI.

J’ai d’abord abordé le problème sous l’angle de la prédiction du défaut de paiement, afin d’identifier les variables réellement discriminantes et comprendre les mécanismes de risque.
Ce travail de modélisation m’a ensuite servi de socle analytique pour construire un tableau de bord Power BI cohérent, structuré et orienté lecture métier.

Cette approche m’a permis de renforcer mes compétences sur :

- la construction d’un pipeline ML robuste en Python,

- l’interprétation des résultats de modèles,

- et surtout la restitution visuelle de résultats complexes dans Power BI.
  
### Positionnement 

Ce projet a d’abord été abordé comme un challenge de machine learning Kaggle, avec pour objectif principal d’obtenir un modèle performant sur la prédiction du défaut de paiement.

Une fois le modèle entraîné, évalué et le score obtenu sur la plateforme, j’ai choisi de revenir sur les données et les résultats afin de les analyser plus finement et de les restituer sous forme de tableau de bord Power BI.

Le tableau de bord n’a donc pas servi à piloter la modélisation, mais à :

- analyser a posteriori les comportements de risque,

- mieux comprendre pourquoi le modèle performe,

- structurer et rendre lisibles des résultats initialement techniques,

- transformer un score Kaggle en lecture analytique exploitable.

Cette démarche m’a permis de travailler à la fois :

- la modélisation machine learning dans un cadre compétitif,

- et la restitution de résultats complexes dans Power BI, en allant au-delà du simple score.
  
---

- **Données Kaggle** :  [Lien du Challenge](https://www.kaggle.com/competitions/playground-series-s5e11)
  
---

#  Overview – Dataset Summary & Global Metrics

![Dashboard Overview](/assets/Overview_tdb.png)

### Points clés du dataset  
- **593 994 prêts** analysés  
- **20.12 %** de défauts → forte **class imbalance**  
- Score de crédit moyen : **681**  
- Revenus et montants de prêt très **asymétriques**  
- Importance notable du **Debt-to-Income (DTI)** dans les défauts

### Insights initiaux

- Les emprunteurs avec **DTI élevé** présentent un risque nettement supérieur.  
- Les défauts varient selon le **purpose** du prêt (éducation, médical, business…).  
- Les niveaux d’éducation et d’emploi influencent la probabilité de défaut.  

---

# Risk Analysis – Structure & Drivers of Default

![Dashboard Risk](/assets/risk_tdb.png)

## Risk Assessment Approach

Avant modélisation, plusieurs dimensions critiques ont été analysées :

- **Affordability & Debt-to-Income**  
- **Crédit Score Sensitivity**  
- **Income Stability**  
- **Loan Amount Skewness**  
- **Class imbalance (20 % defaults)**  

## Key Challenges Identified

- Déséquilibre massif des classes  
- Distributions très asymétriques (income, DTI…)  
- Relations **non linéaires**  
- Forte hétérogénéité entre profils emprunteurs  

## Behavioral Insights

- Sauts de risque brusques dès DTI > 40 %  
- La majorité des emprunteurs sont “low-risk”  
- Forte interaction entre montants, revenus et score de crédit  
- Clusters naturels de profils risqués  

Ces observations guident la construction du pipeline ML (normalisation, encoding, choix du modèle).

---

# Machine Learning – Model Training & Predictions



## Pipeline ML développé

### 1. **Préprocessing**
- Encodage des variables catégorielles  
- Normalisation des variables financières  
- Gestion du class imbalance (oversampling ou class_weight)  
- Split train / test stratifié  

### 2. **Modèles testés**
Selon la nature non linéaire des données :

- LightGBM  
- Random Forest  
- Logistic Regression (baseline)

### 3. **Feature Importance (LGBM)**  
Les principales variables prédictives observées :

1. **Debt-to-Income (DTI)**  
2. **Credit Score**  
3. **Interest Rate**  
4. **Loan Amount**  
5. **Annual Income**

### 4. **Objectif d’évaluation**
- Accuracy  
- F1-score (important pour la classe minoritaire)  
- AUC-ROC  

Suite aux résultats, LightGBM a été retenu comme modèle final (meilleur compromis entre performance et robustesse face au dataset déséquilibré).

---

# Conclusions & Insights

- Le **DTI** est de loin le meilleur prédicteur de défaut.  
- Les distributions asymétriques nécessitent un **prétraitement avancé**.  
- Les modèles linéaires sont insuffisants → les modèles **tree-based** performants.  
- Le choix du seuil décisionnel peut drastiquement changer les performances.  
- Le default risk n'est pas uniforme → segmentation naturelle par profil.

Avec le meilleur modèle, j'ai obtenu un **private score de 0,92** à ce challenge, ce qui m'a placé dans le haut du classement.

---




