# TopoMobile Pro 🗺️

**Application topographique professionnelle** pour géomètres, ingénieurs civils, topographes et urbanistes.

> ⚡ Application 100% client-side — aucun serveur requis. Fonctionne hors connexion après le premier chargement.

[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://VOTRE-USERNAME.github.io/topomobile-pro/)

---

## 🚀 Démo en ligne

Après déploiement sur GitHub Pages, l'application est accessible à :
```
https://VOTRE-USERNAME.github.io/topomobile-pro/
```

## 📱 Fonctionnalités

### 📐 Module Conversion de Coordonnées
- Conversion bidirectionnelle **DD/DMS ↔ UTM** (WGS84)
- Algorithme **Karney-Krüger 6ème ordre** — précision sub-millimétrique (< 1 mm)
- Codes EPSG automatiques (326xx Nord / 327xx Sud)
- Convergence du méridien et facteur d'échelle
- Historique des conversions persisté localement

### 📏 Module Calcul de Superficie
- **Import CSV** de fichiers de points (drag & drop)
- Formats supportés : `Nom;E;N` · `E;N;Nom` · `E;N` (séparateurs `;` `,` `tab`)
- Aperçu **temps réel** du polygone avec animation progressive
- Formule de **Gauss (Shoelace)** sur coordonnées UTM
- Surface en **m²**, **hectares** et **km²**
- Périmètre, centroïde, nombre de sommets
- Labels de points et longueurs des côtés sur le canvas

### 📍 Module GPS Terrain
- Acquisition GPS **temps réel continu** via `watchPosition`
- Coordonnées UTM de précision (Karney-Krüger)
- Coordonnées géographiques DD + DMS (WGS84)
- **Altitude** et précision altimétrique
- Échelle de précision **0–1 m** (topographie professionnelle)
- Classification : RTK Fixe (≤2 cm) → RTK Flottant (≤5 cm) → PPK (≤10 cm) → DGNSS (≤30 cm) → SBAS (≤50 cm) → Autonome (≤1 m)
- Enregistrement de points avec horodatage
- Vitesse et cap

### 🗺️ Module Carte
- Carte **OpenStreetMap** interactive via Leaflet
- Contrôles de zoom et localisation GPS

### ⚙️ Paramètres & Historique
- Thème sombre optimisé pour le terrain
- Historique des conversions persisté (localStorage)
- Points GPS sauvegardés entre les sessions

---

## 🏗️ Architecture Technique

```
Application TOPO/
├── index.html          ← Application complète (single-file)
├── README.md           ← Ce fichier
├── .nojekyll           ← Désactive le processeur Jekyll de GitHub
├── samples/
│   ├── parcelle_6pts.csv
│   └── terrain_12pts.csv
└── LICENSE
```

### Stack Technique
| Technologie | Usage |
|-------------|-------|
| **HTML5 / CSS3 / JS ES6** | Application single-page |
| **Karney-Krüger 6ème ordre** | Conversion UTM sub-millimétrique |
| **Gauss Shoelace** | Calcul de superficie exacte |
| **Leaflet 1.9** | Cartographie OpenStreetMap |
| **Geolocation API** | GPS temps réel haute précision |
| **localStorage** | Persistance hors-ligne |
| **Google Fonts** | Inter (UI) + JetBrains Mono (données) |

### Algorithmes de Précision
- **UTM ↔ Lat/Lon** : Séries de Krüger au 6ème ordre (α₁–α₆, β₁–β₆) sur l'ellipsoïde WGS84
- **Superficie** : Formule de Gauss-Shoelace + centroïde pondéré
- **GPS** : `enableHighAccuracy: true`, `maximumAge: 0` pour précision maximale

---

## 📦 Déploiement sur GitHub Pages

### 1. Créer le dépôt
```bash
cd "Application TOPO"
git init
git add .
git commit -m "feat: TopoMobile Pro v1.0.0"
git branch -M main
git remote add origin https://github.com/VOTRE-USERNAME/topomobile-pro.git
git push -u origin main
```

### 2. Activer GitHub Pages
1. Aller dans **Settings** → **Pages**
2. Source : **Deploy from a branch**
3. Branch : **main** / **(root)**
4. Cliquer **Save**

### 3. Accéder à l'application
```
https://VOTRE-USERNAME.github.io/topomobile-pro/
```

---

## 📱 Utilisation sur mobile

L'application est responsive et optimisée pour tablettes et téléphones :

1. Ouvrir l'URL GitHub Pages sur votre appareil mobile
2. **Android** : Menu ⋮ → "Ajouter à l'écran d'accueil"
3. **iOS** : Bouton partage → "Sur l'écran d'accueil"

> 💡 Pour une précision GPS ≤ 2 cm, connectez un récepteur GNSS RTK via Bluetooth à votre appareil.

---

## 🧪 Fichiers de test CSV

Deux fichiers d'exemple sont fournis dans le dossier `samples/` :

- **`parcelle_6pts.csv`** — Parcelle simple à 6 sommets
- **`terrain_12pts.csv`** — Terrain complexe à 12 sommets

Un bouton "📋 Exemple CSV" dans l'app charge aussi des données de démo intégrées.

---

## 📄 Licence

MIT License — © 2026 TopoMobile Pro
