---
title: "Kaggle – Predicting Loan Payback"
date: 2025-12-09 10:00:00 +0100
categories: [machine-learning, kaggle]
tags: [classification, risk-analysis, powerbi, python]
image: /assets/accueil_tdb.png
description: "Pipeline ML complet et tableau de bord interactif Power BI pour la prédiction de défaut de paiement dans le challenge Kaggle Predicting Loan Payback."
---

# Kaggle – Predicting Loan Payback  
*Playground Series – Season 5 Episode 11*

Ce projet vise à prédire la probabilité qu’un emprunteur ne rembourse pas son prêt, dans le cadre du challenge Kaggle **Predicting Loan Payback**.  
Le travail combine :

- un **pipeline de machine learning** en Python,   
- un **rapport Power BI** comprenant une analyse du Challenge.

L’objectif est de comprendre les comportements de risque, gérer les déséquilibres de classes et évaluer plusieurs modèles pour améliorer la qualité des prédictions.

---

- **Données Kaggle** :  [Lien du Challenge](https://www.kaggle.com/competitions/playground-series-s5e11)
  
---

# 🟦 Overview – Dataset Summary & Global Metrics

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

## 🔎 Key Challenges Identified

- Déséquilibre massif des classes  
- Distributions très asymétriques (income, DTI…)  
- Relations **non linéaires**  
- Forte hétérogénéité entre profils emprunteurs  

## 📘 Behavioral Insights

- Sauts de risque brusques dès DTI > 40 %  
- La majorité des emprunteurs sont “low-risk”  
- Forte interaction entre montants, revenus et score de crédit  
- Clusters naturels de profils risqués  

Ces observations guident la construction du pipeline ML (normalisation, encoding, choix du modèle).

---

# Machine Learning – Model Training & Predictions

![Dashboard Modeling](/assets/img/kaggle/kaggle_model.png)

## ⚙️ Pipeline ML développé

### 1. **Préprocessing**
- Encodage des variables catégorielles  
- Normalisation des variables financières  
- Gestion du class imbalance (oversampling ou class_weight)  
- Split train / test stratifié  

### 2. **Modèles testés**
Selon la nature non linéaire des données :

- **LightGBM**  
- Random Forest  
- Logistic Regression (baseline)

### 3. **Feature Importance (LGBM)**  
Les principales variables prédictives observées :

1. **Debt-to-Income (DTI)**  
2. **Credit Score**  
3. **Interest Rate**  
4. **Loan Amount**  
5. Annual Income  

### 4. **Objectif d’évaluation**
- Accuracy  
- F1-score (important pour la classe minoritaire)  
- AUC-ROC  

Selon tes résultats, LightGBM a été retenu comme modèle final (meilleur compromis entre performance et robustesse face au dataset déséquilibré).

---

# Conclusions & Insights

- Le **DTI** est de loin le meilleur prédicteur de défaut.  
- Les distributions asymétriques nécessitent un **prétraitement avancé**.  
- Les modèles linéaires sont insuffisants → les modèles **tree-based** performants.  
- Le choix du seuil décisionnel peut drastiquement changer les performances.  
- Le default risk n'est pas uniforme → segmentation naturelle par profil.

---



# Conclusion générale

Ce projet combine une **analyse exploratoire**, une **étude de risque** et une **modélisation machine learning** centrée sur la prédiction de défaut.  
Les dashboards Power BI fournissent une vision synthétique du dataset, tandis que le pipeline Python permet d’expérimenter des modèles performants et adaptés aux données réelles.

---

