# 📊 Projet BubbleTech – Contexte et Objectifs

Dans le cadre de mon stage de fin d’études en Business Data Analysis, j’ai réalisé un projet chez **BubbleTech**, une ASBL bruxelloise active dans la formation, le bénévolat et l’inclusion numérique. Face à la croissance de ses activités (formations, stages, bénévolat, partenariats), BubbleTech avait besoin d’un **système d’information centralisé** pour mieux structurer, analyser et exploiter ses données internes.

---

## 🎯 Objectif général

L’objectif principal de ce projet était de concevoir un **système d’information décisionnel (SID)** pour accompagner la croissance de BubbleTech.  
L'organisation faisait face à des difficultés de structuration des données, de centralisation des informations, et de reporting. Le système mis en place devait permettre :

- de **digitaliser** les processus de collecte (inscriptions, partenariats, stages, etc.) via des formulaires uniformisés ;
- de **centraliser** les données dans une base relationnelle claire et exploitable ;
- de **produire des indicateurs clés** (KPIs) pour chaque activité, facilitant ainsi le pilotage et la prise de décision ;
- de **visualiser** les performances globales de l’ASBL via des dashboards interactifs.

Ce projet répondait à un double enjeu : structurer les données pour fiabiliser les processus, tout en rendant l’information accessible, compréhensible et actionnable.

---

## 🧩 Enjeux identifiés

L’état initial de la gestion de l'information chez BubbleTech révélait plusieurs limites importantes, notamment :

- **Données dispersées et non centralisées** : la majorité des informations étaient stockées dans des fichiers Excel non structurés, difficilement partageables et rarement mis à jour.

- **Dépendance organisationnelle** : une grande partie de la connaissance des processus et des données reposait sur une seule personne, rendant l'organisation vulnérable.

- **Manque d'indicateurs et de vision globale** : l'absence de KPIs standardisés empêchait toute analyse d'impact fiable, et les décisions se prenaient souvent sur la base d'intuition.

- **Processus manuels et chronophages** : sans automatisation, les tâches répétitives (collecte, nettoyage, reporting) mobilisaient du temps précieux.

- **Croissance rapide non accompagnée** : face à l’augmentation du volume et de la diversité des activités (formations, bénévolat, stages, partenariats), l’absence d’un système d'information structuré menaçait la pérennité opérationnelle.

L’enjeu du projet était donc d’accompagner la professionnalisation de BubbleTech par un système robuste, évolutif et orienté décision.

---

## 🛠️ Solution apportée

Le projet a été structuré en quatre grandes phases selon une approche agile :

### 1. Conception des outils de collecte
Des formulaires Google Forms ont été conçus et validés avec l’équipe de BubbleTech pour couvrir toutes les dimensions stratégiques : stagiaires, bénévoles, employés, formateurs, partenaires, bénéficiaires, satisfaction, feedback post-formation.  
Chaque formulaire a été structuré autour d’indicateurs clés identifiés suite à des entretiens. En tout, **8 formulaires** ont été mis en place.

### 2. Développement d’un pipeline automatisé
Un script Python a été développé pour automatiser l’intégralité du traitement des fichiers Google Sheets :
- standardisation des noms de colonnes selon un mapping centralisé ;
- nettoyage des numéros de téléphone, accents, doublons, textes mal orthographiés ;
- gestion de formats invalides ou inexploitables.
Le pipeline générait un fichier propre, prêt à être inséré en base.

### 3. Intégration en base de données
Les données ont d’abord transité par **Cassandra (NoSQL)** pour stockage brut, avant d’être insérées dans une **base PostgreSQL** modélisée autour de l’entité `individu`.  
Le schéma relationnel assurait l’intégrité des données et permettait de gérer des entités multiples : rôles, préférences, partenariats, ressources, etc.

### 4. Visualisation dans Power BI
Des dashboards ont été développés pour chaque volet (formation, bénévolat, partenariat…), connectés directement aux vues SQL générées.  
Parmi les **43 KPIs** définis initialement, une sélection pertinente a été intégrée visuellement : répartition géographique, satisfaction, nombre de formations, insertion professionnelle, engagement bénévole, etc.

---

## 🧠 Compétences mobilisées

### 🔄 Traitement des données
- **Python** (Pandas, Regex, PySpellChecker) pour l’ETL complet
- Nettoyage automatique de données textuelles, numériques et catégorielles
- Gestion des anomalies (doublons, incohérences, formats)

### 🧱 Modélisation et base de données
- Modèle relationnel en étoile (PostgreSQL)
- Normalisation des entités : stagiaires, partenaires, employés, etc.
- Passage temporaire par **Cassandra** (NoSQL) pour des raisons de flexibilité

### 📊 Visualisation et reporting
- **Power BI** : modélisation, mesures DAX, slicers, filtres interactifs
- KPIs répartis en 8 grandes thématiques
- Tableaux de bord filtrables par rôle ou activité

### 🗂️ Documentation et gestion projet
- **GitHub** : versioning, structuration du code et des scripts
- **ClickUp** : organisation en sprints, gestion des tâches et feedbacks
- Rédaction de documentation technique (modèle de données, code, procédures)

### 👥 Analyse métier et collaboration
- Recueil des besoins via entretiens avec les parties prenantes
- Structuration des formulaires selon des indicateurs métiers
- Tests utilisateurs et ajustements post-déploiement

---

> Ce projet m’a permis d’exercer des compétences transversales alliant data engineering, modélisation, automatisation et visualisation métier, dans un contexte réel et complexe.
