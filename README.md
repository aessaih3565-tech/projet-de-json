# Tableau de bord des commandes

Application web frontend qui affiche, recherche et filtre une liste de commandes à partir d'un fichier JSON. Elle présente les statistiques principales sous forme de cartes et affiche les résultats dans un tableau responsive.

## Fonctionnalités

- Afficher toutes les commandes depuis `data/data.json`
- Rechercher une commande par nom de client
- Filtrer les commandes par statut :
  - Toutes
  - Livrée
  - En attente
  - Annulée
- Afficher uniquement les commandes payées
- Consulter les statistiques :
  - Nombre total de commandes
  - Nombre de commandes livrées
  - Nombre de commandes payées
  - Montant total en DH
- Afficher un message lorsqu'aucun résultat ne correspond

## Technologies utilisées

- HTML5
- CSS3
- JavaScript ES Modules
- Bootstrap 5
- API `fetch` pour charger les données JSON

## Structure du projet

```text
.
├── index.html
├── css/
│   └── style.css
├── js/
│   ├── app.js
│   ├── dataservice.js
│   ├── state.js
│   └── view.js
├── data/
│   └── data.json
└── README.md
```

## Architecture JavaScript

- `app.js` initialise l'application et relie les événements aux filtres.
- `dataservice.js` charge les commandes depuis le fichier JSON.
- `state.js` applique la recherche, le filtre de statut et le filtre de paiement.
- `view.js` génère le tableau et met à jour les statistiques.

## Lancer le projet

Ce projet charge ses données avec `fetch`, donc il doit être ouvert via un serveur HTTP local.

### Avec Live Server dans VS Code

1. Installer l'extension **Live Server**.
2. Ouvrir le dossier du projet dans VS Code.
3. Cliquer sur **Go Live** dans la barre d'état ou ouvrir `index.html` avec Live Server.
4. Accéder à l'adresse affichée par Live Server, généralement `http://127.0.0.1:5501`.

### Avec Python

Dans le dossier du projet, exécuter :

```bash
python -m http.server 5500
```

Puis ouvrir `http://localhost:5500` dans le navigateur.

### Avec Node.js

Si le package `npx` est disponible :

```bash
npx serve .
```

## Format des données

Les données sont stockées dans `data/data.json` sous forme de tableau d'objets :

```json
[
  {
    "id": 1,
    "client": "Sara",
    "montant": 450,
    "statut": "Livrée",
    "paiement": "Payé",
    "date": "2026-10-12"
  }
]
```

Pour ajouter une commande, ajouter un objet dans ce tableau. Les valeurs possibles pour le statut sont `Livrée`, `En attente` et `Annulée`. Les valeurs possibles pour le paiement sont `Payé` et `Non payé`.
