# L-g-Chimio — version 2

**Gestion intégrée d'une chimiothèque et d'une extractothèque de recherche, avec cheminformatique et bioactivité.**

L-g-Chimio est une application web complète de gestion des collections de produits issus de la synthèse ou d'extraits naturels d'un laboratoire de recherche. Là où ces collections sont habituellement dispersées entre tableurs, cahiers de laboratoire, inventaires de congélateurs et fichiers de résultats biologiques, L-g-Chimio les réunit dans un système unique, cohérent et interrogeable : une même fiche relie la **structure chimique**, le **stock physique**, la **provenance** et les **données d'activité** d'un composé ou d'un extrait.

L'application couvre l'ensemble du cycle de vie d'un échantillon. Côté synthèse, elle gère les **produits chimiques** : enregistrement, structures 2D, descripteurs et regroupements structuraux. Côté produits naturels, elle suit les **extraits et leurs fractions**, du spécimen d'origine (taxonomie, conformité Nagoya / CITES) jusqu'au fractionnement bioguidé. Et parce que la chimie ne prend tout son sens qu'à travers ce qu'elle produit biologiquement, elle intègre nativement les **résultats biologiques** par cible — classés selon des barèmes issus de la littérature — et établit le lien jusqu'à l'**analyse structure-activité**.

Au cœur du dispositif, un moteur cheminformatique (**RDKit**) traite les structures comme de véritables objets chimiques — rendu 2D, descripteurs, squelettes, similarité — et non comme de simples images. Autour, tout est pensé pour l'usage quotidien au laboratoire : **stockage physique** (piluliers, plaques, tares), **traçabilité conforme ISO 9001**, **gestion multi-équipes** avec contrôle d'accès, et une **interface disponible en 10 langues**. Ce dépôt est le **canal public de distribution des versions** (journal des modifications et métadonnées de version) ; le code source de l'application est géré séparément.

---

## En bref

- 🧪 **Chimiothèque** — catalogue de molécules avec structures 2D, descripteurs et regroupements structuraux.
- 🌿 **Extractothèque** — extraits et fractions de produits naturels, avec taxonomie, conformité réglementaire et fractionnement.
- 🔬 **Bioactivité** — résultats biologiques par cible, classés selon des seuils issus de la littérature, et **fractionnement bioguidé**.
- 📦 **Stock & traçabilité** — mouvements, étiquettes/QR, plaques, journalisation conforme ISO 9001.
- 🌍 **10 langues** — interface entièrement internationalisée.
- 🔐 **Sécurité** — développée selon les bonnes pratiques OWASP, contrôle d'accès par équipe.

---

## Fonctionnalités

### Chimiothèque (produits de synthèse)
- Fiche produit complète : identité, équipe propriétaire, stock, références.
- **Rendu 2D des structures** à la volée via le moteur cheminformatique RDKit (SVG haute définition).
- Descripteurs moléculaires, **squelettes de Murcko**, **clustering de Butina** et analyse de **diversité structurale**.
- **Enrichissement automatique** depuis PubChem (mise à jour planifiée des données).
- Gestion des **produits chimiques commerciaux** et de leurs piluliers.

### Extractothèque (produits naturels)
- Extraits **bruts** et **fractions** reliés (lignée parent → fractions).
- **Taxonomie mutualisée** (famille, genre, espèce, sous-espèce), partie d'organisme, type d'extraction et solvants.
- Suivi des **spécimens et échantillons** d'origine.
- Champs de **conformité réglementaire** : protocole de Nagoya, CITES.
- Référentiel de **formes** (extrait brut, fraction, huile essentielle, etc.) et d'unités.

### Bioactivité & fractionnement bioguidé
- Saisie des **résultats biologiques** par cible (enzyme, lignée cellulaire, parasite…) et par laboratoire/protocole.
- Mesures multiples : **IC50, EC50, CC50**, % d'activité, % d'inhibition, **indice de sélectivité**, opérateurs et unités dédiés.
- **Classification d'activité** selon des barèmes adaptés au type d'essai issus de la littérature (cytotoxicité *NCI / Suffness-Pezzuto*, antipaludique *Berthi 2019*, antimicrobien *Kuete 2010*), barème générique sinon.
- **Facteur d'enrichissement** parent → fraction : visualise la concentration de l'activité au fil du fractionnement — le cœur du criblage bioguidé.
- Liens vers les ressources externes des cibles (UniProt, etc.) et **analyse SAR**.

### Import / Export
- Import par **fichier Excel (.xlsx) ou CSV** pour les produits, les extraits, les tares et les résultats biologiques ; import **SDF** pour les structures.
- **Auto-détection des en-têtes multilingue** : un modèle téléchargé puis rempli dans n'importe laquelle des 10 langues est reconnu automatiquement (et insensible aux accents).
- Modèles commentés téléchargeables ; exports des données.

### Stock, étiquettes et traçabilité
- **Mouvements de stock** et plaques (plates) de criblage.
- Génération d'**étiquettes et QR codes**.
- **Journalisation des opérations conforme ISO 9001**.
- Tableau de bord, rapports et idées de synthèse.

---

## Pensé pour le laboratoire

- **Multi-équipes** avec contrôle de visibilité des données par contrat/équipe.
- **Interface en 10 langues** : français, anglais, espagnol, allemand, italien, portugais, néerlandais, grec, polonais, suédois.
- **Chimie durable** : indicateur d'empreinte durable sur les fiches.
- Conçu pour s'intégrer à un environnement de recherche existant (annuaire, sauvegardes, dépôt Git interne).

---

## Architecture technique

| Composant | Choix |
| --- | --- |
| Langage | **PHP 8.4**, architecture **MVC** (sans Composer) |
| Base de données | **PostgreSQL 16** avec **cartouche RDKit** |
| Cheminformatique | **RDKit** (rendu des structures, descripteurs, scaffolds, clustering) |
| Internationalisation | 10 langues, sans repli silencieux |
| Sécurité | Requêtes préparées (placeholders nommés), protection **CSRF**, **CSP** par nonce, échappement systématique des sorties |

---

## Versions

Le journal détaillé des évolutions est disponible dans [`CHANGELOG.md`](CHANGELOG.md). Les métadonnées de la dernière version sont publiées dans [`version.json`](version.json).

---

## Auteur & licence

Développé par **Laurent ROBIN** — CNRS / Université d'Orléans (ICOA, UMR 7311).
Dépôt APP N°99.75.3615
Distribué sous licence **CeCILL**.
