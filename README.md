# 📋 CODIR Perf & Tech

Application Kanban collaborative pour la direction CODIR Perf & Tech.
Données partagées en temps réel entre tous les postes via Firebase.

![](https://img.shields.io/badge/hébergement-GitHub%20Pages-blue)
![](https://img.shields.io/badge/backend-Firebase%20Realtime%20DB-orange)
![](https://img.shields.io/badge/dépendances-aucune-green)

---

## 🚀 Installation en 3 étapes

### Étape 1 — Créer le projet Firebase (5 min)

1. Allez sur **[console.firebase.google.com](https://console.firebase.google.com)**
2. Cliquez **"Ajouter un projet"**
3. Nommez-le `codir-perf-tech` → Continuer → Désactivez Google Analytics → **Créer le projet**

#### Activer la base de données
4. Dans le menu gauche → **"Realtime Database"** → **"Créer une base de données"**
5. Choisissez la région **Europe-west1 (Belgique)** → Suivant
6. Sélectionnez **"Commencer en mode test"** → Activer

   > ⚠️ Le mode test autorise tout le monde à lire/écrire pendant 30 jours.
   > Remplacez ensuite les règles par ceci pour une protection permanente :
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
   *(La vraie protection est assurée par le mot de passe de l'application.)*

#### Récupérer les clés
7. Cliquez l'icône ⚙️ → **"Paramètres du projet"** → onglet **"Général"**
8. Descendez jusqu'à **"Vos applications"** → Cliquez l'icône **`</>`** (Web)
9. Nommez l'app `kanban` → **Enregistrer l'application**
10. Copiez le bloc `firebaseConfig` affiché

---

### Étape 2 — Configurer `index.html`

Ouvrez `index.html` et remplacez le bloc `FIREBASE CONFIG` :

```javascript
const FIREBASE_CONFIG = {
    apiKey:            "AIzaSy...",           // ← votre valeur
    authDomain:        "codir-perf-tech.firebaseapp.com",
    databaseURL:       "https://codir-perf-tech-default-rtdb.europe-west1.firebasedatabase.app",
    projectId:         "codir-perf-tech",
    storageBucket:     "codir-perf-tech.appspot.com",
    messagingSenderId: "123456789",
    appId:             "1:123...:web:abc..."
};
```

Changez aussi le mot de passe si besoin :
```javascript
window.APP_PASSWORD = "codir2025";   // ← votre mot de passe
```

---

### Étape 3 — Déployer sur GitHub Pages

```bash
git clone https://github.com/VOTRE_USER/codir_perf_tech.git
cd codir_perf_tech
# (copiez index.html et README.md dans ce dossier)
git add .
git commit -m "Initial deploy"
git push origin main
```

Puis dans GitHub :
1. **Settings** → **Pages**
2. Source : **Deploy from a branch**
3. Branch : `main` / `/ (root)` → **Save**

✅ L'app sera disponible sur : `https://VOTRE_USER.github.io/codir_perf_tech/`

---

## ✨ Fonctionnalités

| Fonctionnalité | Description |
|---|---|
| 🔒 Mot de passe | Accès protégé, commun à toute l'équipe |
| 🔄 Sync temps réel | Les données se mettent à jour sur tous les postes instantanément |
| 📋 3 colonnes | Cette semaine / Prochaines semaines / Sujets importants |
| 🎨 5 thématiques | Performance, Outils, Animation, Efficience, Interne |
| 🔴🟡🔵 Priorités | Haute / Normale / Basse |
| 👥 Acteurs | Gestion avec autocomplétion |
| 📅 Dates | Archivage automatique à échéance, alertes retard |
| 💬 Commentaires | Par tâche |
| 🔗 Liens URL | Cliquables |
| 🗂 Archives | Dépliables |
| 🔃 Tri | Par thème & date |
| 📄 Duplication | De tâches |
| 📊 Export CSV | Compatible Excel (`;`, UTF-8 BOM) |
| 💾 Backup JSON | Export/Import pour sauvegarde manuelle |
| 🖱 Drag & drop | Entre colonnes |
| 📝 Notes libres | Zone "Infos diverses" partagée |
| 🟢 Indicateur sync | Statut de connexion visible en temps réel |

---

## 💾 Données & Sauvegardes

- **Stockage principal** : Firebase Realtime Database (cloud, partagé)
- **Backup automatique** : localStorage (navigateur) en cas de coupure réseau
- **Backup manuel** : bouton **💾 Backup JSON** → partagez le fichier si besoin

### Quota Firebase (plan gratuit Spark)
| Ressource | Limite gratuite |
|---|---|
| Stockage | 1 GB |
| Téléchargements | 10 GB/mois |
| Connexions simultanées | 100 |

Largement suffisant pour un usage CODIR.

---

## 🔧 Personnalisation

### Modifier les thématiques
Dans `index.html`, bloc `themeConfig` :
```javascript
var themeConfig = {
    "performance": { label: "Performance", color: "#3498db" },
    // Ajoutez/modifiez ici...
};
```
Puis mettez à jour le `<select id="theme">` en conséquence.

### Modifier les colonnes
Changez les titres HTML et les options du `<select id="status">`.

---

## 🔐 Sécurité

> Le mot de passe est vérifié côté client. Il protège l'accès à l'interface mais **les clés Firebase sont visibles dans le code source**. Pour un usage interne (intranet, équipe restreinte), ce niveau de protection est adapté. Pour des données critiques, envisagez Firebase Authentication.

---

## 📁 Structure du dépôt

```
codir_perf_tech/
├── index.html   # Application complète
└── README.md    # Ce fichier
```
