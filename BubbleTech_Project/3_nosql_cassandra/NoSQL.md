# 🗃️ Phase 3 – Stockage intermédiaire NoSQL avec Cassandra

Dans cette phase, les fichiers nettoyés sont temporairement stockés dans une base de données **NoSQL (Cassandra)** avant leur insertion dans la base relationnelle finale (PostgreSQL).

Ce stockage intermédiaire permet d’organiser, sécuriser et préparer les données tout en **maintenant une grande flexibilité**.

---

## 🎯 Pourquoi Cassandra ?

- ✅ **Pas de schéma strict requis** : idéal pour gérer différents types de fichiers/formulaires
- ✅ **Performance élevée** pour le stockage de fichiers structurés sans transformation immédiate
- ✅ **Séparation logique par formulaire** via l’utilisation de *keyspaces*
- ✅ Permet de **garder une trace des fichiers nettoyés**, indépendamment du modèle relationnel final

---

## 🧱 Structure réelle des keyspaces utilisés

Les fichiers nettoyés sont classés dans **4 keyspaces**, chacun correspondant à un ensemble logique de formulaires ou à un usage spécifique :

### 🔸 `autres_services/`
Contient les fichiers liés à :
- **bénévoles**
- **employés**
- **stagiaires**
- **partenaires**

### 🔸 `formation/`
Contient :
- les inscriptions aux **formations**
- les retours de **satisfaction**
- les données des **formateurs**

### 🔸 `firstContact/`
Formulaire unique non modélisé utilisé pour comprendre les besoins de toute personne qui contacte BubbleTech via ses réseaux sociaux (ex : veut-il un stage, une formation, etc.).  
📌 Ces données sont **uniquement stockées dans Cassandra** à ce stade.

### 🔸 `retour_experience/`
Contient :
- le **formulaire de retour sur contribution**
- le **suivi des participants** après leur passage chez BubbleTech

---

## 📁 L’arborescence des Kayspaces :

```bash
data/
└── keyspaces/
    ├── formation/
    │   ├── cleaned_satisfaction.xlsx
    │   └── cleaned_formateur.xlsx
    ├── autres_services/
    │   └── cleaned_stagiaire.xlsx
    ├── retour_experience/
    │   └── cleaned_suivi_des_participants.xlsx
    └── firstContact/
        └── cleaned_first_contact.xlsx


```
---
## 🧠 Ce que cette phase apporte

Cette étape assure un **stockage structuré, flexible et temporairement autonome** avant l’intégration dans la base relationnelle.  
Cassandra agit comme une **zone tampon professionnelle** :

- permettant d’**organiser les fichiers par logique fonctionnelle** (via les keyspaces),
- facilitant les allers-retours sur les fichiers sans impacter la base finale,
- **sécurisant les données nettoyées** avant modélisation,
- **adaptée aux données semi-structurées** et aux formulaires non modélisés.

> Ce choix renforce la robustesse et l'évolutivité du pipeline tout en respectant les contraintes métier de BubbleTech.
