#  Agent de classifitaion d'emails (Gmail vers Google Sheets)

Cet agent Python automatise la récupération des e-mails entrants de la boîte Gmail, les classe par catégorie et urgence, et les distribue dans un Google Sheet dédié pour un suivi centralisé.

---

##  Configuration

| Ressource | Description |
| :--- | :--- |
| **Google Cloud** | APIs **Gmail** et **Sheets** activées. |
| **Fichiers Locaux** | Clé JSON   |
| **Google Sheets ID** |

##  Structure du Google Sheet

Pour éviter les erreurs d'API, les noms d'onglets doivent être simplifiés.

| **Nom de l'Onglet (API)** | Catégorie (Triage) | **Explication / Contenu** |
| :--- | :--- | :--- |
| **`AccesAuth`** | Problème d’accès / authentification | Problèmes de **connexion**, mot de passe ou compte bloqué. |
| **`BugDysfct`** | Bug ou dysfonctionnement d’un service | **Erreurs logicielles**, plantages et fonctionnalités cassées. |
| **`TechInfo`** | Problème technique informatique | Problèmes de **matériel**, réseau ou VPN. |
| **`Admin`** | Demande administrative | Requêtes **non techniques** (RH, factures, contrats). |
| **`SupportUser`** | Demande de support utilisateur | **Catégorie par défaut** : Questions générales et demandes d'aide. |

---

##  Fonctionnalités Clés

1.  **Récupération:** Récupère tous les e-mails de la boîte de réception en utilisant l'API Gmail (gestion de la pagination et décodage Base64).
2.  **Analyse/Triage:** Attribue une **Catégorie** et un niveau d'**Urgence** (Critique $\rightarrow$ Anodine) via une logique de mots-clés. Génère une **Synthèse** de 100 caractères.
3.  **Reporting:** Ajoute les données (`Sujet`, `Urgence`, `Synthèse`) dans l'onglet correspondant du Google Sheet (mode ajout de lignes).

### Résultat de la dernière exécution

**549** tickets récupérés, analysés et distribués avec succès.
