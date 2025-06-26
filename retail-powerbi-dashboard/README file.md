# 🛍️ Analyse des ventes et retours – Supermarket Dataset (Kaggle)

Ce projet a pour objectif d'explorer et visualiser les performances commerciales d’un supermarché à l’aide de données ouvertes disponibles sur Kaggle. Il met en œuvre la modélisation en étoile et la création de dashboards interactifs dans Power BI pour faciliter l’analyse.

## 🎯 Objectifs

- Identifier les produits les plus rentables, les segments clients à valeur, et les régions les plus performantes.
- Analyser les marges, le volume des ventes, les retours et les tendances de consommation.
- Créer une structure relationnelle propre (modèle en étoile) pour des analyses efficaces et rapides.

## 🧱 Modélisation relationnelle (Star Schema)

Le modèle de données a été structuré autour d’une table de faits `F_Sales` connectée à plusieurs dimensions :

- `D_Product`
- `D_Customer`
- `D_Date`
- `D_Geographie`
- `D_Ship_mode`
- `D_Regional_Manager`

👉 Voir le schéma relationnel : (model/model.png)

## ⚙️ Préparation des données

- Suppression des doublons
- Création d’une table `D_Date` complète avec année, mois, jour, nom du mois, etc.
- Typage des champs
- Création de mesures DAX : chiffre d’affaires, profit, taux de retour, top N produits, etc.

## 📊 Dashboards Power BI

Le dashboard comprend plusieurs pages et visuels :
- KPIs globaux : ventes, profit, retour
- Ventes par région / segment client / catégorie produit
- Analyse des marges et de la rentabilité
- Filtres interactifs (date, segment, manager, etc.)

📸 Voir les captures dans [`dashboard/captures/`](dashboard/captures)




## 📎 Dataset source

Kaggle – [Super Market Dataset by Aditi Rai](https://www.kaggle.com/datasets/aditirai2607/super-market-dataset)

## 👤 Auteur

Ahmed OUDAOUDOUHMOU  
[LinkedIn](https://www.linkedin.com/in/ahmed-oudaoudouhmou) – [Portfolio](https://ahmedoudaoudouhmou.github.io/Portfolio)


---


## English Version

# 🛍️ Sales & Returns Analysis – Supermarket Dataset (Kaggle)

This project aims to explore and visualize the commercial performance of a supermarket using a publicly available dataset from Kaggle. It applies a star schema data model and interactive dashboards built in Power BI to deliver clear insights.

## 🎯 Project Objectives

- Identify the most profitable products, valuable customer segments, and top-performing regions.
- Analyze profit margins, sales volumes, returns, and consumption trends.
- Build a clean relational model (star schema) to support fast and flexible analysis.

## 🧱 Data Model – Star Schema

The data was structured around a central fact table `F_Sales` connected to several dimensions:

- `D_Product`
- `D_Customer`
- `D_Date`
- `D_Geographie`
- `D_Ship_mode`
- `D_Regional_Manager`

👉 See the schema diagram: [`model/model.png`](model/model.png)

## ⚙️ Data Preparation

- Removed duplicates and cleaned raw records
- Created a full calendar table `D_Date` with year, month, day, weekday, etc.
- Typed and renamed columns for consistency
- Built custom DAX measures: total sales, profit, return rate, top N products, etc.

## 📊 Power BI Dashboards

The Power BI report includes several pages and visual elements:
- Global KPIs: sales, profit, returns
- Breakdown by region, customer segment, and product category
- Profitability and return analysis
- Dynamic filters: by date, region, manager, and more

📸 See screenshots in [`dashboard/captures/`](dashboard/captures)


## 📎 Dataset Source

Kaggle – [Super Market Dataset by Aditi Rai](https://www.kaggle.com/datasets/aditirai2607/super-market-dataset)

## 👤 Author

Ahmed OUDAOUDOUHMOU  
[LinkedIn](https://www.linkedin.com/in/ahmed-oudaoudouhmou) – [Portfolio](https://ahmedoudaoudouhmou.github.io/Portfolio)


