# 🧩 Phase 4 – Intégration relationnelle dans PostgreSQL

Cette phase consiste à insérer les données nettoyées dans une base PostgreSQL structurée, normalisée et évolutive.  
Elle constitue le **socle du système décisionnel** de BubbleTech, connectée ensuite à Power BI pour la restitution.

---

## 🎯 Pourquoi PostgreSQL ?

- Moteur SQL robuste et open source  
- Intégrité relationnelle et contraintes de cohérence  
- Support des requêtes analytiques avancées  
- Connectivité avec les outils BI (Power BI, Metabase, etc.)

---

## 🧱 Modèle relationnel

Le modèle est structuré autour de la table centrale `individu`, liée à des rôles (`stagiaire`, `formateur`, `bénévole`, etc.) et à différentes entités d'interaction (satisfaction, organisation, disponibilité...).

---

### 📌 Volet 1 – Modèle relationnel : Individus & Rôles

![Modèle relationnel – Individus](./individu_role.png)

---

### 📌 Volet 2 – Modèle relationnel : Inscriptions & Formations

![Modèle relationnel – Formations](./inscription_formation.png)

---

### 📌 Volet 3 – Modèle relationnel : Partenariats

![Modèle relationnel – Partenariats](./partenaire.png)

---

## 🧑‍💻 Organisation des scripts d’insertion Python

```bash
sql_ressources/
├── push_sqlite.py            # Lance tous les handlers
├── db.py                     # Connexion + création tables
├── utils.py                  # Fonctions communes
└── forms/
    ├── stagiaire.py
    ├── formateur.py
    ├── benevole.py
    ├── partenaire.py
    └── ...

