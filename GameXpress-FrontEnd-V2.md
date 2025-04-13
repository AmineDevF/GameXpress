
# 🎨 Frontend Administrateur & Client – GameXpress (V2)

## 🚀 Introduction  
Cette version V2 du frontend GameXpress introduit la **gestion avancée du panier**, le **rôle utilisateur**, la **fusion des paniers**, le **calcul dynamique des totaux (TVA, remises)** et bien plus encore.  
Elle est conçue pour offrir une **expérience fluide aux clients** connectés et invités, tout en permettant une **administration fine des rôles** via une interface dédiée.

---

## 🛠️ Technologies Utilisées
- **Framework Frontend** : React.js  
- **State Management** : `useContext`
- **Requêtes API** : Axios  
- **Routing** : React Router Dom  
- **Authentification** : Laravel Sanctum (via API backend)  
- **Notifications** : React Toastify  
- **Upload** :  ++ React Dropzone  ++
- **Form Validation** : ++ Yup + Formik ++
- **Graphiques** : Recharts.js (bonus)

---

## 🛒 Gestion du Panier (Nouveauté V2)

### 🔹 Fonctionnalités
- **Ajout au panier** (connecté ou invité)
- **Mise à jour des quantités**
- **Suppression d’article**
- **Fusion automatique du panier après login**
- **Panier persistant en base pour les utilisateurs connectés**
- **Calcul total (TVA, remises, livraison)**
- **Expiration automatique après 48h d’inactivité**

### 🧠 Comportement UX
| Statut | Stockage Panier |  
|--------|------------------|  
| 🧑‍🚀 Invité | `localStorage` / session |  
| 👤 Connecté | Base de données via API |

> Lorsqu’un invité se connecte, les deux paniers sont **fusionnés automatiquement**.

---

## 🔐 Gestion des Rôles et Permissions (Bonus V2)
### 🔹 Fonctionnalités côté frontend :
- Attribution de rôle via interface admin (si autorisé)
- Affichage conditionnel des boutons/options selon rôle :
  - `Client` : accès au panier uniquement
  - `Manager` : accès aux commandes
  - `Admin` : accès total (utilisateurs, rôles, produits...)

---



## 🧾 Gestion du Panier – Détails API utilisés

| Action | Méthode | Endpoint |
|--------|---------|----------|
| Ajouter produit | `POST` | `/api/v2/cart/add` |
| Modifier quantité | `PUT` | `/api/v2/cart/update/{id}` |
| Supprimer produit | `DELETE` | `/api/v2/cart/remove/{id}` |
| Voir panier | `GET` | `/api/v2/cart` |
| Fusion panier après login | `POST` | `/api/v2/cart/merge` |

---

## 💰 Calcul du Total & Remises

- Calculs dynamiques côté frontend en interaction avec le backend
- Résumé affiché dans la page "Panier" :
  - Sous-total
  - TVA (20% par défaut)
  - Remises appliquées
  - Frais de livraison (forfait ou conditionnel)
  - **Total TTC**

---

## 🧪 Validation & Expériences Utilisateur

- ✅ Feedback visuel via **React Toastify**
- ✅ **Loader** sur chaque action async
- ✅ **Formulaires validés** avec **Yup**
- ✅ Gestion des erreurs : Axios Interceptors + Catch centralisé

---


## 🗓️ **Planning de Développement – Frontend V2 (10 jours)**

| **Jour** | **Tâches principales** |  
|----------|------------------------|  
| **Jour 1 🛠️** | 🔧 Mise en place des composants de base du **panier** (CardProduit, PanierSidebar, RésuméCommande) <br>🧩 Implémentation du **stockage local** pour les invités (localStorage/sessionStorage) |  
| **Jour 2 🔄** | 👥 Création du **contexte Panier** (`CartContext`) <br>🔐 Liaison avec l’authentification : détection **invité vs connecté** |  
| **Jour 3 📦** | ➕ Ajout des actions panier (ajouter, modifier, supprimer) <br>🔄 Gestion dynamique des quantités (avec contrôle stock) |  
| **Jour 4 🧠** | 🔗 Détection de connexion et **fusion automatique** entre panier local et DB (via API `/cart/merge`) <br>🔒 Implémentation des **règles de rôles UI** (`Client`, `Manager`, `Admin`) |  
| **Jour 5 💰** | 🧮 Calcul **automatique du total TTC**, TVA, remises <br>📋 Affichage du récapitulatif clair avant validation (CheckoutPreview) |  
| **Jour 6 ✅** | 🧪 Mise en place des **tests visuels** et validation de chaque action panier <br>🎯 UX : gestion des erreurs, loader sur actions async |  
| **Jour 7 🔔** | 📢 Intégration de **React Toastify** pour les feedbacks (succès, erreurs) <br>💡 Affichage de messages spécifiques selon cas (ex : stock insuffisant) |  
| **Jour 8 🧼** | ⏳ Mise en place de la **logique d’expiration automatique** des articles du panier (48h) avec `setTimeout` ou date-check |  
| **Jour 9 🔄** | 🧱 Refactor du code : découpage logique, nettoyage, séparation UI & logique <br>📁 Organisation finale des fichiers & contextes |  
| **Jour 10 🚀** | ✅ Vérification complète de tous les flows (invité -> connecté, fusion, checkout) <br>🌐 Préparation au déploiement (`npm run build`, config `.env`) |

---

### 🎁 **Livrables attendus en fin de sprint**
- ✅ Panier fonctionnel avec toutes les règles métiers
- ✅ Contexte global robuste (`CartContext`, `AuthContext`)
- ✅ UI fluide, testée, et sécurisée selon les rôles
- ✅ Système d’expiration et de fusion au point
- ✅ Projet prêt à être **déployé sur Vercel ou Netlify**


## 🚀 Déploiement (optionnel)

- Hébergement via **Vercel**, **Netlify** ou **GitHub Pages**
- Commandes :
  ```bash
  npm run build
  ```
- Configuration :
  - `.env` avec les variables d’API (`REACT_APP_API_URL`)
  - HTTPS recommandé pour compatibilité avec Sanctum

---

## ✅ Bonus / Améliorations futures
- 🔐 Auth via **OAuth (Google/Facebook)**  
- 💳 Intégration **Stripe** pour le paiement  
- 🔄 Mise en **cache du panier** pour performance offline  
- 🔔 Notifications en temps réel (WebSocket)

---
