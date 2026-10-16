# Évaluation UML — Conception d'un système de gestion des incidents informatiques

**Niveau :** Master 1  
**Type de travail :** individuel  
**Durée :** une journée  
**Technologies :** outil de modélisation UML au choix  
**Livrable principal :** dossier de conception UML accompagné de justifications écrites
**Email:** mathiasgilles136@gmail.com
---

## 1. Contexte

Une entreprise de taille moyenne souhaite mettre en place un système de gestion des incidents informatiques afin d'améliorer le suivi des problèmes rencontrés par ses employés.

Les incidents peuvent concerner différents domaines :

- Pannes réseau.
- Applications inaccessibles.
- Problèmes matériels.
- Comptes utilisateurs bloqués.
- Problèmes d'accès aux ressources informatiques.

Actuellement, les employés signalent les problèmes par courriel ou par téléphone. Le service informatique rencontre plusieurs difficultés : perte d'informations, absence de suivi centralisé, affectations mal coordonnées et manque de visibilité sur les délais de résolution.

L'entreprise souhaite donc disposer d'une application permettant de centraliser les déclarations, d'organiser le travail des techniciens, de suivre l'évolution des incidents et de conserver un historique des opérations.

Vous êtes chargés de réaliser la **conception UML de ce système**, depuis l'analyse des besoins jusqu'à la proposition d'une architecture logicielle.

Aucun développement n'est demandé.

## 2. Objectifs de l'évaluation

À travers cette étude de cas, vous devez démontrer votre capacité à :

- Analyser un besoin métier et identifier les acteurs d'un système.
- Modéliser les fonctionnalités à l'aide d'un diagramme de cas d'utilisation.
- Construire un diagramme de classes cohérent avec les règles métier.
- Décrire des interactions à l'aide de diagrammes de séquence.
- Modéliser un processus métier à l'aide d'un diagramme d'activités.
- Proposer une architecture logicielle à l'aide d'un diagramme de composants.
- Maintenir la cohérence entre les différents diagrammes.
- Justifier vos choix de modélisation et identifier les éventuelles ambiguïtés du besoin.

## 3. Description fonctionnelle du système

### 3.1. Gestion des utilisateurs

Chaque employé dispose d'un compte lui permettant de déclarer des incidents et de consulter les incidents qu'il a signalés.

Le service informatique dispose de comptes spécifiques permettant de gérer les incidents et de suivre leur traitement.

Les utilisateurs du système peuvent avoir différents rôles :

- **Employé :** déclare un incident et consulte son suivi.
- **Technicien :** consulte les incidents qui lui sont affectés et met à jour leur état.
- **Responsable informatique :** supervise les incidents, affecte les techniciens et consulte les indicateurs de suivi.
- **Administrateur :** gère les comptes, les rôles et le référentiel des compétences techniques.

Un utilisateur peut posséder plusieurs rôles si l'entreprise le permet.

### 3.2. Déclaration d'un incident

Un employé peut déclarer un incident en renseignant les informations suivantes :

- Un titre.
- Une description.
- Une catégorie.
- Un niveau d'urgence.
- Une date de déclaration.

Chaque incident reçoit un identifiant unique et est associé à l'employé qui l'a déclaré.

Les catégories disponibles sont :

- Réseau.
- Matériel.
- Logiciel.
- Compte utilisateur.
- Autre.

Les niveaux d'urgence sont :

- Faible.
- Normale.
- Élevée.
- Critique.

Un incident nouvellement créé possède le statut `NOUVEAU`.

### 3.3. Affectation des incidents

Le responsable informatique consulte les incidents en attente et peut affecter un incident à un technicien.

Chaque incident peut être affecté à un seul technicien à la fois.

Un technicien possède un ensemble de compétences techniques. Chaque incident nécessite une ou plusieurs compétences pour être traité.

Le système doit vérifier que le technicien sélectionné possède toutes les compétences requises par l'incident.

Si les conditions sont réunies, l'affectation est enregistrée et le statut de l'incident devient `ASSIGNE`.

Dans le cas contraire, l'affectation est refusée et un message explicatif est présenté au responsable informatique.

### 3.4. Traitement des incidents

Le technicien peut consulter les incidents qui lui sont affectés et commencer leur traitement.

Lorsqu'il commence à travailler sur un incident, son statut devient `EN_COURS`.

À la fin de son intervention, il renseigne une description de la solution apportée. L'incident peut alors passer au statut `RESOLU`.

Le responsable informatique peut ensuite vérifier la résolution et clôturer l'incident.

### 3.5. Historique des incidents

Le système conserve un historique des changements de statut.

Chaque entrée d'historique contient :

- La date et l'heure du changement.
- Le statut précédent.
- Le nouveau statut.
- L'utilisateur à l'origine du changement.
- Un commentaire facultatif.

L'historique permet de reconstituer les principales étapes du traitement d'un incident.

### 3.6. Consultation et supervision

Le responsable informatique peut consulter les incidents selon plusieurs critères :

- Statut.
- Catégorie.
- Niveau d'urgence.
- Technicien affecté.
- Date de déclaration.

Il peut également consulter des indicateurs de suivi, notamment le nombre d'incidents ouverts, résolus ou en retard.

Le système doit permettre de distinguer les incidents encore en cours de traitement des incidents terminés.

## 4. Règles métier

Les règles suivantes doivent être prises en compte dans les diagrammes.

**RM1.** Chaque incident possède un identifiant unique.

**RM2.** Chaque incident est déclaré par un utilisateur.

**RM3.** Un incident peut être affecté à zéro ou un technicien à un instant donné.

**RM4.** Un technicien ne peut être affecté à un incident que s'il possède toutes les compétences requises.

**RM5.** Un incident clos ne peut plus être modifié dans le cadre du traitement normal.

**RM6.** Un incident ne peut passer au statut `RESOLU` que si une description de la solution est renseignée.

**RM7.** Chaque changement de statut doit être enregistré dans l'historique.

**RM8.** Un incident affecté ne peut être pris en charge que par le technicien auquel il est affecté, sauf intervention exceptionnelle du responsable informatique.

**RM9.** Un incident ne peut être clôturé que s'il est résolu.

**RM10.** Un technicien peut traiter plusieurs incidents simultanément.

**RM11.** Les incidents critiques doivent être identifiables et prioritaires dans les consultations du service informatique.

**RM12.** Toute transition de statut doit respecter le cycle de vie défini par la conception.

Si une règle ne précise pas suffisamment le comportement attendu, vous devez formuler une hypothèse, la justifier et l'appliquer de manière cohérente dans l'ensemble des diagrammes.

---

# 5. Travail demandé

## Partie A — Analyse du besoin et diagramme de cas d'utilisation

**Objectif :** identifier les acteurs, leurs responsabilités et les fonctionnalités du système.

### A.1. Identification des acteurs

Identifiez les acteurs principaux et secondaires du système.

Pour chaque acteur, précisez brièvement son rôle et ses interactions avec l'application.

Vous devrez notamment étudier les rôles suivants :

- Employé.
- Technicien.
- Responsable informatique.
- Administrateur.

Vous pouvez identifier d'autres acteurs si vous justifiez leur utilité.

### A.2. Identification des cas d'utilisation

Réalisez le diagramme global des cas d'utilisation.

Le diagramme doit représenter au minimum les fonctionnalités suivantes :

- Déclarer un incident.
- Consulter ses incidents.
- Consulter les incidents à traiter.
- Affecter un incident à un technicien.
- Réaffecter un incident.
- Commencer le traitement d'un incident.
- Enregistrer une solution.
- Résoudre un incident.
- Clôturer un incident.
- Consulter l'historique d'un incident.
- Filtrer les incidents.
- Consulter les indicateurs de suivi.
- Gérer les utilisateurs et leurs rôles.
- Gérer les compétences des techniciens.

### A.3. Relations entre les cas d'utilisation

Identifiez les relations pertinentes entre les cas d'utilisation.

Vous devrez notamment déterminer si certaines fonctionnalités nécessitent obligatoirement d'autres traitements ou si certains comportements sont conditionnels.

Utilisez les relations UML `<<include>>` et `<<extend>>` uniquement lorsque leur sémantique est justifiée.

### A.4. Description textuelle d'un cas d'utilisation

Rédigez une description détaillée du cas d'utilisation **« Affecter un incident à un technicien »**.

Votre description doit contenir :

- Le nom du cas d'utilisation.
- L'acteur principal.
- Les préconditions.
- Le scénario nominal.
- Les scénarios alternatifs.
- Les postconditions.
- Les règles métier concernées.

Prévoyez notamment les situations suivantes :

- L'incident n'existe pas.
- Le technicien n'existe pas.
- Le technicien ne possède pas toutes les compétences requises.
- L'incident est déjà clos.
- L'affectation est acceptée.

**Livrables de la partie A :**

1. Un diagramme global de cas d'utilisation.
2. Une description textuelle détaillée du cas d'utilisation « Affecter un incident à un technicien ».

---

## Partie B — Diagramme de classes

**Objectif :** modéliser la structure statique du système et traduire les règles métier en éléments UML.

### B.1. Identification des classes

Construisez un diagramme de classes métier représentant les principales entités du système.

Vous devrez notamment étudier les classes suivantes :

- `Utilisateur`
- `Incident`
- `Technicien`
- `Competence`
- `HistoriqueStatut`

Vous pouvez ajouter d'autres classes si elles sont nécessaires à votre conception.

Par exemple, vous pouvez distinguer les rôles des utilisateurs, les catégories d'incidents ou les opérations d'affectation si cela améliore la modélisation.

### B.2. Attributs et opérations

Pour chaque classe, précisez :

- Les attributs pertinents.
- Les types des attributs.
- La visibilité des attributs et opérations lorsque cela est pertinent.

Les attributs doivent être suffisamment précis pour représenter les informations nécessaires au fonctionnement du système.

### B.3. Associations et multiplicités

Représentez les associations entre les classes.

Votre diagramme devra notamment permettre de représenter :

- Le lien entre un incident et son déclarant.
- Le lien entre un incident et son technicien affecté.
- Les compétences détenues par les techniciens.
- Les compétences requises par les incidents.
- L'historique associé à un incident.
- L'utilisateur à l'origine d'un changement de statut.

### B.4. Énumérations et contraintes

Utilisez des énumérations UML lorsque cela est pertinent, notamment pour :

- Les statuts des incidents.
- Les niveaux d'urgence.
- Les catégories d'incidents.

### B.5. Gestion du cycle de vie

Le diagramme de classes doit être cohérent avec les règles de changement de statut et de conservation de l'historique.

Vous devez expliquer comment votre modèle permet de représenter :

- L'affectation d'un incident.
- La conservation de l'historique.
- L'enregistrement de la solution.
- La clôture d'un incident.

**Livrable de la partie B :**

Un diagramme de classes métier complet, accompagné d'une justification concise des principales associations, multiplicités et contraintes.

---

## Partie C — Diagrammes de séquence

**Objectif :** représenter les interactions entre les acteurs et les objets du système pour des scénarios métier significatifs.

Vous devez réaliser **deux diagrammes de séquence**.

### C.1. Diagramme de séquence 1 : affectation d'un incident

Modélisez le scénario suivant :

Le responsable informatique sélectionne un incident et demande son affectation à un technicien.

Le système recherche l'incident et le technicien, vérifie que l'incident peut être affecté et contrôle les compétences du technicien.

Si les conditions sont réunies :

1. Le technicien est affecté à l'incident.
2. Le statut de l'incident devient `ASSIGNE`.
3. L'historique est mis à jour.
4. Le responsable reçoit une confirmation.

Dans le cas contraire, l'opération est refusée et un message explicatif est retourné.

Votre diagramme doit faire apparaître :

- L'acteur initiateur.
- L'interface ou le point d'entrée du système.
- Le service métier chargé de l'affectation.
- Les objets ou composants chargés de rechercher les données.
- Les vérifications métier.
- Les modifications apportées à l'incident.
- L'enregistrement de l'historique.
- Les retours vers l'acteur.

Utilisez des fragments combinés UML, notamment `alt`, pour représenter les différentes issues possibles.

### C.2. Diagramme de séquence 2 : résolution et clôture d'un incident

Modélisez le scénario suivant :

Un technicien commence le traitement d'un incident qui lui a été affecté.

Il réalise son intervention, renseigne la description de la solution puis demande la résolution de l'incident.

Le système vérifie que le technicien est autorisé à effectuer l'opération et que la description de la solution est renseignée.

Si les conditions sont réunies :

1. Le statut passe à `RESOLU`.
2. L'historique est mis à jour.
3. Le système confirme la résolution.

Le responsable informatique consulte ensuite l'incident et peut le clôturer.

Votre diagramme doit représenter les interactions, les validations, les changements de statut et les mises à jour de l'historique.

Prévoyez également un scénario alternatif dans lequel la résolution est refusée parce que la description de la solution est absente.

**Livrables de la partie C :**

1. Un diagramme de séquence pour l'affectation d'un incident.
2. Un diagramme de séquence pour la résolution et la clôture d'un incident.

---

## Partie D — Diagramme de composants et architecture logicielle

**Objectif :** proposer une architecture logicielle cohérente avec les fonctionnalités et les modèles précédents.

L'entreprise souhaite une application dont les responsabilités sont séparées afin de faciliter sa maintenance et son évolution.

Vous devez proposer une architecture comprenant au minimum les éléments suivants :

- Une interface utilisateur.
- Un composant de gestion des incidents.
- Un composant de gestion des affectations.
- Un composant de gestion des utilisateurs et des techniciens.
- Un composant de gestion de l'historique.
- Un composant d'accès aux données.
- Un système de stockage des données.

Vous pouvez regrouper certains composants ou en ajouter d'autres si vous justifiez vos choix.

### D.1. Réalisation du diagramme

Le diagramme doit représenter :

- Les composants logiciels.
- Le rôle de chaque composant.
- Les interfaces fournies et requises, lorsque cela est pertinent.
- Les dépendances entre les composants.
- Les interactions entre les composants métier et le stockage.

### D.2. Justification de l'architecture

Rédigez une justification concise de votre architecture.

Expliquez notamment :

- Pourquoi vous avez séparé les composants.
- Quel composant est responsable des règles d'affectation.
- Comment les données sont consultées et modifiées.
- Comment l'historique est enregistré.
- Comment votre architecture pourrait évoluer si une interface web ou une API était ajoutée.


**Livrable de la partie D :**

Un diagramme de composants accompagné d'une justification écrite de l'architecture proposée.

---

# 6. Livrables attendus

À la fin de la journée, vous devez fournir un dossier de conception comprenant :

| Référence | Livrable | Format attendu |
|---|---|---|
| A1 | Diagramme de cas d'utilisation | Image ou PDF |
| A2 | Description textuelle du cas d'utilisation « Affecter un incident » | PDF ou Markdown |
| B | Diagramme de classes métier | Image ou PDF |
| C1 | Diagramme de séquence : affectation | Image ou PDF |
| C2 | Diagramme de séquence : résolution et clôture | Image ou PDF |
| D | Diagramme de composants | Image ou PDF |

Tous les diagrammes doivent être lisibles, correctement légendés et réalisés à l'aide d'une notation UML standard.

Les outils de modélisation sont libres. Vous pouvez utiliser un logiciel de modélisation UML, un éditeur compatible avec PlantUML ou tout autre outil adapté.

Aucun code applicatif n'est demandé.

## 7. Organisation indicative du travail

La durée totale de l'évaluation est d'une journée.

| Phase | Travail | Durée indicative |
|---|---|---:|
| 1 | Analyse du besoin et identification des acteurs | 45 min |
| 2 | Diagramme de cas d'utilisation et description textuelle | 1 h |
| 3 | Diagramme de classes | 1 h 45 |
| 4 | Diagrammes de séquence | 1 h 30 |
| 6 | Diagramme de composants | 1 h |
| **Total** | | **6 h** |

Cette répartition est indicative. Vous pouvez organiser votre travail différemment, à condition de remettre tous les livrables demandés.

---

# 8. Barème d'évaluation

La note finale est calculée sur **20 points**.

| Partie | Critères d'évaluation | Points |
|---|---|---:|
| A | Identification des acteurs, pertinence des cas d'utilisation et description textuelle | 5 |
| B | Qualité du diagramme de classes, associations, multiplicités et contraintes | 5 |
| C | Pertinence des diagrammes de séquence, interactions et scénarios alternatifs | 5 |
| D | Qualité du diagramme de composants et justification de l'architecture | 4 |
| | Lisibilité et qualité générale du dossier | 1 |
| **Total** | | **20** |

## 9. Critères généraux d'évaluation

L'évaluation portera notamment sur :

- La compréhension du besoin métier.
- La précision et la pertinence de la modélisation UML.
- Le respect de la notation UML.
- La cohérence entre les différents diagrammes.
- La bonne représentation des règles métier et des scénarios alternatifs.
- La pertinence des associations et des multiplicités.
- La qualité des choix d'architecture.
- La capacité à justifier les décisions de conception.
- La lisibilité et la structuration du dossier.
- La capacité à identifier et à traiter les ambiguïtés du besoin.

Une attention particulière sera portée à la cohérence entre les diagrammes. Un diagramme isolément correct ne suffit pas si ses éléments contredisent ceux des autres diagrammes.

## 10. Contraintes et recommandations

- Le travail est individuel.
- Aucun développement informatique n'est demandé.
- Les outils de modélisation sont libres.
- Les diagrammes doivent utiliser une notation UML standard.
- Les hypothèses retenues doivent être explicitées.
- Les règles métier doivent être représentées de manière cohérente.
- Les diagrammes doivent être lisibles et suffisamment détaillés pour permettre à un autre concepteur de comprendre le système.
- Toute décision de modélisation importante doit pouvoir être justifiée.

**L'objectif final est de démontrer votre capacité à analyser un besoin complexe, à le représenter avec plusieurs diagrammes UML complémentaires et à produire une conception logicielle cohérente, justifiée et exploitable.**
