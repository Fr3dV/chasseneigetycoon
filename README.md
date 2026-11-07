# Chasse-Neige Tycoon

Jeu 3D dans le navigateur : déneiger le village de Valneige, encaisser les paiements de la mairie et acheter des chasse-neige de plus en plus puissants (12 machines, de la souffleuse de Papi au Mammouth polaire).

## Contenu

```
chasse-neige-tycoon/
├── index.html              le jeu complet (HTML, CSS et JavaScript dans un seul fichier)
├── vendor/
│   ├── three.min.js        three.js r128, embarqué localement (aucune dépendance CDN)
│   └── THREE-LICENSE.txt   licence MIT de three.js
├── CLAUDE.md               consignes pour Claude Code
└── README.md
```

Site 100 % statique : aucun serveur applicatif, aucune base de données, aucune étape de build.

## Tester en local

Ouvrir `index.html` directement fonctionne dans la plupart des navigateurs. Pour un test fidèle à la production :

```bash
cd chasse-neige-tycoon
python3 -m http.server 8080
# puis http://localhost:8080
```

## Déployer

Copier le dossier tel quel sur n'importe quel hébergement statique (serveur web, bucket, Netlify, Cloudflare Pages, Firebase Hosting…). `index.html` doit rester à la racine du site et `vendor/` à côté de lui.

Recommandations :

- servir en HTTPS ;
- mettre en cache longue durée `vendor/three.min.js` (fichier figé), cache court pour `index.html` ;
- activer la compression gzip ou brotli (three.min.js passe d'environ 600 Ko à 150 Ko).

## Dépendances externes restantes

- Polices Google Fonts (Barlow, Barlow Condensed). Sans réseau, le jeu bascule sur les polices système, sans autre effet.

## Sauvegarde

La partie (argent, machines, statistiques, réglage du son) est sauvegardée dans le `localStorage` du navigateur sous la clé `chasseNeigeTycoon_v1`. Elle est propre à chaque navigateur et à chaque domaine : changer de domaine repart d'une partie neuve.

## Commandes

| Touche | Action |
|---|---|
| Z / W ou ↑ | Avancer |
| S ou ↓ | Reculer |
| Q / A, D ou ← → | Tourner |
| G | Garage |
| V | Vue cabine |
| C, molette | Changer de vue, zoomer |
| M | Couper le son |

Sur mobile, des boutons tactiles apparaissent à l'écran.
