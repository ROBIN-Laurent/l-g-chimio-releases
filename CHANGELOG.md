# Changelog L-g-Chimio

Toutes les versions notables sont documentées ici.
Format basé sur [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/),
versionnage suivant [Semver](https://semver.org/lang/fr/).

## [2.0.0] - 2026-05-30

### Nouveautés
- **Numérotation V2** : refonte complète du système de numérotation avec builder drag&drop, archivage des modèles précédents, et historique consultable directement dans la page de paramètres
- **Bascule de modèle** : possibilité de changer la composition du numéro avec archivage automatique de l'ancien et activation du nouveau
- **Restriction admin sur le type** : le changement de type (libre/contrat/brevet) d'un produit existant est désormais réservé à l'administrateur
- **Régénération du numéro pilulier** : lors d'un changement de type, l'admin peut choisir de régénérer le numéro pilulier si le segment TYPE est dans la composition
- **Notifications de mise à jour** : nouvelle page Administration → Mises à jour avec détection des migrations en attente, version installée, et vérification opt-in d'une nouvelle version disponible

### Améliorations
- Footer enrichi avec trait tricolore
- Page Sécurité publique et documentation SECURITY.md complète
- Audit ISO 9001 complet (Snapshot avant modification, Audit log de chaque changement critique)

### Sécurité
- Restriction admin sur les changements de type (anti-tampering frontend + backend)
- Audit log des changements de version, de modèle, de type
- Vérification de version opt-in (aucun appel réseau sans consentement explicite)

### Migration BDD
- Nouvelles colonnes : `parametres.para_update_check_enabled`, `parametres.para_update_check_url`, `parametres.para_version_seen`
- Nouvelles colonnes : `produit.pro_anciens_numeros_pilulier`, `extraits.ext_anciens_numeros_pilulier`
- Nouvelles colonnes : `produit.pro_id_modele`, `extraits.ext_id_modele`
- Nouvelle table : `numerotation_archive`
