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

👉 Voir le schéma relationnel : [`model/star_schema.png`](model/star_schema.png)

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

## 📁 Structure du projet

