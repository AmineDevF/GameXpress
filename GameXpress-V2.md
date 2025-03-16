### 🛒 **User Story - Gestion du Panier (V2)**  

#### 🎯 **Objectif :**  
Permettre aux utilisateurs (connectés et invités) d'ajouter des produits à leur panier, de modifier les quantités, d'appliquer des remises, et de finaliser leur commande de manière fluide et sécurisée.  

---

## **📌 Acteurs**  
👤 **Utilisateur invité** : Peut ajouter des articles au panier, mais le panier est stocké en session.  
👥 **Utilisateur authentifié** : Son panier est sauvegardé en base de données et accessible sur plusieurs appareils.  
🛒 **Système** : Gère les interactions et applique les règles métier (gestion du stock, remises, etc.).  

---

## **📍 Fonctionnalités détaillées**  

### **1️⃣ Ajout au panier**  
- En tant qu’utilisateur, je veux **ajouter un produit à mon panier** avec une quantité définie afin de le retrouver plus tard.  
- **Règles métiers :**  
  - Vérifier que le produit existe et qu’il est disponible en stock.  
  - Si l’utilisateur est **invité**, le panier est stocké en session.  
  - Si l’utilisateur est **connecté**, l’article est sauvegardé en base de données.  
  - Si le produit est déjà dans le panier, la quantité est mise à jour.  

### **2️⃣ Mise à jour et suppression d’un article**  
- En tant qu’utilisateur, je veux **modifier la quantité d’un article dans mon panier** afin d’ajuster ma commande.  
- En tant qu’utilisateur, je veux **supprimer un article de mon panier** si je change d’avis.  
- **Règles métiers :**  
  - La quantité ne peut pas dépasser le stock disponible.  
  - La suppression est immédiate et met à jour le total du panier.  

### **3️⃣ Gestion du panier pour utilisateurs invités et connectés**  
- En tant qu’utilisateur, je veux **retrouver mon panier après connexion** afin de ne pas perdre mes articles.  
- **Règles métiers :**  
  - Lorsqu’un invité se connecte, son panier temporaire est **fusionné avec son panier enregistré**.  
  - En cas de doublon, la quantité est mise à jour.  

### **4️⃣ Application des remises et codes promo** (bonus) 
- En tant qu’utilisateur, je veux **appliquer un code promo** pour bénéficier d’une réduction.  
- **Règles métiers :**  
  - Vérifier la validité du code (date d’expiration, conditions d’application, nombre d’utilisations).  
  - Calculer la réduction et mettre à jour le total du panier.  

### **5️⃣ Calcul du total du panier (avec taxes et remises)**  
- En tant qu’utilisateur, je veux **voir le total de mon panier** avec le détail des taxes et des éventuelles réductions.  
- **Règles métiers :**  
  - Appliquer la TVA et les éventuels frais de livraison.  
  - Afficher un résumé clair des prix avant validation.  

### **6️⃣ Expiration des articles du panier**  
- En tant qu’utilisateur, je veux que **les articles du panier expirent après une période définie** afin de garantir leur disponibilité pour d’autres clients.  
- **Règles métiers :**  
  - Si un article reste dans le panier plus de **48 heures**, il est supprimé automatiquement.  

---

## **📅 Planning de Développement (5 jours)**  

| Jour | Tâches principales |  
|------|--------------------|  
| **Jour 1** 🛠️ | Création de la table `cart_items` avec relations + Ajout des routes API pour le panier |  
| **Jour 2** 🔄 | Développement du `CartController` (ajout, mise à jour, suppression) + Gestion du stock |  
| **Jour 3** 🔑 | Implémentation de la fusion du panier après connexion + Gestion des sessions |  
| **Jour 4** 💰 | Ajout du système de codes promo + Calcul du total (TVA, réductions, etc.) |  
| **Jour 5** ✅ | Mise en place de l’expiration des articles |  

---

## **📂 Organisation du Code**  

📂 **app**  
 ├── 📁 Http  
 │   ├── 📂 Controllers  
 │   │   └── 📂 Api/V1  
 │   │       └── 📜 CartController.php  
 ├── 📁 Models  
 │   ├── 📜 CartItem.php  
 ├── 📂 routes  
 │   ├── 📜 api.php  
 ├── 📂 tests  
 │   ├── Feature/Api/V1/CartTest.php  

---

### **📌 Points Bonus**  
🔹 **Intégration avec Stripe** pour le paiement en ligne  
🔹 **Mise en cache du panier pour optimiser les performances**  



