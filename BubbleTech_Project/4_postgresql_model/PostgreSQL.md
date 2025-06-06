# 🧩 Phase 4 – Intégration relationnelle dans PostgreSQL

Après le nettoyage et le stockage intermédiaire dans Cassandra, les données sont structurées et intégrées dans une base de données relationnelle **PostgreSQL**.  
Cette base constitue le **socle du système d’information décisionnel** mis en place pour BubbleTech.

---

## 🎯 Pourquoi PostgreSQL ?

- Système de gestion de base relationnelle robuste et open source
- Prise en charge des **vues**, **jointures**, **contraintes d’intégrité**
- Compatible avec les outils de BI comme Power BI
- Idéal pour construire un modèle structuré, normalisé et évolutif

---

## 🧱 Structure du modèle relationnel

Le modèle repose sur une **table centrale `individu`**, dans laquelle sont enregistrées toutes les personnes (stagiaires, bénévoles, formateurs, partenaires, employés...).

Chaque individu peut avoir un ou plusieurs **rôles**, qui sont définis dans une table `role`, avec un `type_role` associé.

Autour de cette table centrale, des tables spécifiques permettent de stocker les données propres à chaque rôle ou interaction.

---

### 📋 Tables principales

| Table               | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `individu`         | Données personnelles et de contact (nom, email, téléphone, âge...)         |
| `role`             | Lien entre un individu et son(ses) rôle(s) (stagiaire, bénévole...)        |
| `formation`        | Informations sur les formations suivies                                     |
| `disponibilite`    | Jours et horaires disponibles (pour les stagiaires, bénévoles...)          |
| `organisation`     | Données sur les structures partenaires (partenariat, entreprise, etc.)     |
| `satisfaction`     | Évaluations post-formation (notées et textuelles)                          |
| `experience`       | Feedback qualitatif après le passage chez BubbleTech                       |
| `formateur`, `employe`, etc. | Tables métiers liées aux rôles spécifiques                          |

---

### 🔗 Relations principales

| Relation                                      | Description                                                                 |
|----------------------------------------------|-----------------------------------------------------------------------------|
| `individu` 🔁 `role`                         | Un individu peut avoir un ou plusieurs rôles (stagiaire, bénévole, etc.)   |
| `role` 🔁 tables spécifiques (`stagiaire`, `formateur`, etc.) | Chaque rôle est lié à une table métier qui enregistre ses spécificités     |
| `individu` 🔁 `disponibilite`, `langue`, `preference` | Tables de liaison pour des attributs partagés par rôle                     |
| `individu` 🔁 `organisation` via `partenaire` ou `employe` | Une personne peut être liée à une organisation en tant que partenaire ou employé |
| `individu` 🔁 `satisfaction`, `experience`    | Un individu ayant participé à une formation peut laisser une évaluation ou un retour |
| `formation_evaluee` 🔁 `formation` + `individu` | Suivi de la participation d’un individu à une formation précise            |

---

## 🗂️ Arborescence des scripts Python d’insertion (handlers)

Chaque type de formulaire est traité par un **handler Python dédié**, responsable de l’insertion des données dans les bonnes tables relationnelles.

```bash
sql_ressources/
├── push_db.py            # Point d’entrée (exécute tous les handlers)
├── db.py                     # Connexion et création de tables
├── utils.py                  # Fonctions communes (nettoyage, duplication, etc.)
└── forms/
    ├── stagiaire.py          # Handler pour les stagiaires
    ├── formateur.py
    ├── benevole.py
    ├── employe.py
    ├── satisfaction.py
    ├── partenaire.py
    └── ...

```
---
## 📌 Conclusion

Cette phase marque la **transition entre les données nettoyées et leur structuration formelle** dans un modèle relationnel robuste.  
Grâce à ce design centré sur `individu` et ses rôles, l'organisation de BubbleTech est modélisée de façon souple et évolutive.

Les données sont désormais **fiables, cohérentes et interconnectées**, prêtes à alimenter les outils de reporting et d’analyse.  
Ce socle relationnel est ce qui permet à Power BI de restituer une vue métier fidèle, segmentée et exploitable à tout moment.
