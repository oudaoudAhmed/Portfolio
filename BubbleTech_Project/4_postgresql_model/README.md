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
├── push_db.py                # Lance tous les handlers
├── db.py                     # Connexion + création tables
├── utils.py                  # Fonctions communes
└── forms/
    ├── stagiaire.py
    ├── formateur.py
    ├── benevole.py
    ├── partenaire.py
    └── ...
```

---
## 📸 Exemple d’exécution (terminal)

![Log d’insertion](./insertion.PNG)

---

## 🗂️ Exemple de contenu réel (table `individu`)

![Extrait table individu](./table_individu.PNG)

---

## 🧠 Analyse décisionnelle – Exemples de requêtes SQL

Ces requêtes montrent comment la base peut générer **des indicateurs utiles pour piloter les actions**.

---

### 🔍 Requête 1 : Disponibilités d’un stagiaire

```sql
SELECT i.nom_complet AS "Stagiaire", j.jour AS "Jour", h.tranche_horaire AS "Créneau"
FROM individu i
JOIN role r ON i.id_individu = r.id_individu
JOIN stagiaire st ON r.id_role = st.id_role
JOIN disponibilite d ON r.id_role = d.id_role
JOIN jour j ON d.id_jour = j.id_jour
JOIN horaire h ON d.id_horaire = h.id_horaire
WHERE i.nom_complet = 'OUDAOUDOUHMOU Ahmed';
```

📸 Résultat :

![Résultat requête 1](./requete_disponibilites.PNG)

---

### 📊 Requête 2 : Formations les mieux perçues globalement  
Afficher la moyenne des évaluations par formation (contenu, clarté, pertinence, recommandation).

```sql
SELECT 
    fe.titre AS "Formation",
    ROUND(AVG(ef.qualite_contenu), 2) AS "Contenu",
    ROUND(AVG(ef.clarte_explications), 2) AS "Clarté",
    ROUND(AVG(ef.pertinence_besoins), 2) AS "Pertinence",
    ROUND(AVG(ef.recommandation), 2) AS "Recommandation"
FROM evaluation_formation ef
JOIN formation_evaluee fe ON ef.id_formation_evaluee = fe.id_formation_evaluee
GROUP BY fe.titre
ORDER BY "Recommandation" DESC;
```

📸 Résultat :

![Résultat requête 2](./formations_mieux_perçues_globalement.PNG)

---

### 🏆 Requête 3 : Formation la mieux notée  
Identifier la formation ayant obtenu la meilleure note de recommandation.

```sql
SELECT fe.titre AS titre_formation, 
       ROUND(AVG(ef.recommandation), 2) AS moyenne_recommandation
FROM evaluation_formation ef
JOIN formation_evaluee fe ON ef.id_formation_evaluee = fe.id_formation_evaluee
GROUP BY fe.titre
ORDER BY moyenne_recommandation DESC
LIMIT 1;
```

📸 Résultat :

![Résultat requête 3](./formation_mieux_notée.PNG)

---

## 📌 Conclusion

Cette phase a permis de transformer les données brutes en un **modèle structuré, cohérent et exploitable**, capable de générer des indicateurs stratégiques.  
Grâce à cette base relationnelle, BubbleTech peut aujourd’hui :

- analyser la qualité de ses formations,  
- suivre les profils de ses bénéficiaires,  
- évaluer l’engagement de ses partenaires et bénévoles,  
- et piloter ses décisions sur des bases solides.

🎯 C’est le cœur du système décisionnel mis en œuvre dans ce projet.
