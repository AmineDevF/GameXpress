# 💻 V3 Frontend — Gestion des Commandes et Paiements

To design the **v3 frontend** for managing orders and payments based on your backend API, we’ll create a user interface that integrates with the provided backend endpoints and user flows. Below is a structured outline of how to approach this, building upon your v2 frontend structure.

---

## 🛒 User Story - Gestion des Commandes et Paiements (V3)

### 🎯 Objectif :  
Permettre à l'administrateur de gérer les commandes, les paiements et les transactions de manière fluide, avec une interface d'administration simple et intuitive.

---

## 📌 Acteurs  

- 👨‍💼 **Administrateur** : Peut consulter, mettre à jour et annuler les commandes, gérer les paiements, et visualiser les transactions.  
- 🛠️ **Système** : Effectue les appels API pour obtenir les données, les mettre à jour ou les supprimer, et présente les résultats sous forme d'interface interactive.

---

## 📍 Fonctionnalités détaillées

### 1️⃣ Liste des commandes
**Objectif :** Afficher toutes les commandes avec un tableau interactif.

**Règles métiers :**
- Utiliser la route **GET** `/api/v1/admin/orders`.
- Afficher ID, prix total, statut, dates.
- Permettre tri et filtrage (statut, date, utilisateur).

**Composants :**
- Tableau des commandes avec pagination.
- Filtres : statut (en attente, en cours, expédiée, annulée).
- Action "Voir" pour afficher plus de détails.

---

### 2️⃣ Voir une commande
**Objectif :** Afficher les détails d’une commande spécifique.

**Règles métiers :**
- Route : **GET** `/api/v1/admin/orders/{id}`.
- Détails : articles, adresse de livraison, mode de paiement.
- Bouton pour mise à jour du statut ou annulation.

**Composants :**
- Modal de détails de la commande.
- Tableau des articles (nom, quantité, prix).

---

### 3️⃣ Mettre à jour le statut de la commande
**Objectif :** Permettre la mise à jour du statut.

**Règles métiers :**
- Route : **PUT** `/api/v1/admin/orders/{id}/status`.
- Statuts : "en attente", "en cours", "expédiée", "annulée".
- Mise à jour temps réel.

**Composants :**
- Menu déroulant pour le statut.
- Bouton "Mettre à jour".

---

### 4️⃣ Annuler une commande
**Objectif :** Annuler une commande.

**Règles métiers :**
- Route : **DELETE** `/api/v1/admin/orders/{id}`.
- Confirmation avant suppression.

**Composants :**
- Bouton "Annuler la commande" avec confirmation.

---

### 5️⃣ Liste des paiements
**Objectif :** Afficher toutes les transactions.

**Règles métiers :**
- Route : **GET** `/api/v1/admin/payments`.
- Détails : montant, statut, mode, transaction ID.

**Composants :**
- Tableau des paiements avec pagination.
- Filtres : statut (réussi, en attente, échoué).
- Action "Voir" pour plus de détails.

---

### 6️⃣ Détails d’un paiement
**Objectif :** Voir les détails d’un paiement spécifique.

**Règles métiers :**
- Route : **GET** `/api/v1/admin/payments/{id}`.
- Détails : montant, type, statut, transaction ID.

**Composants :**
- Modal de détails.
- Action "Voir la commande associée".

---

### 7️⃣ Traitement des paiements
**Objectif :** Traiter un paiement.

**Règles métiers :**
- Route : **POST** `/api/v1/admin/payments`.
- Formulaire : type de paiement, montant, etc.

**Composants :**
- Formulaire de paiement.
- Indicateur de succès/échec.

---

### 8️⃣ Calcul du total des paiements et commandes
**Objectif :** Calculer et afficher les totaux.

**Règles métiers :**
- Calcul dynamique des totaux.
- Prendre en compte taxes et frais.

**Composants :**
- Section "Total des paiements" et "Total des commandes".

---

## 📅 Planning de Développement

| Jour       | Tâches principales                                             |
|------------|---------------------------------------------------------------|
| **Jour 1** 🛠️ | Création de la vue pour lister les commandes et afficher les détails |
| **Jour 2** 🔄 | Développement de la mise à jour du statut et de l'annulation         |
| **Jour 3** 🔑 | Création des vues pour les paiements (liste et détails)             |
| **Jour 4** 💰 | Intégration du traitement des paiements et calculs de total         |
| **Jour 5** ✅ | Mise en place des filtres et validation des formulaires             |

---

## 📂 Organisation du Code

