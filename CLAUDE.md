# Consignes pour Claude Code

## Le projet

Jeu 3D statique « Chasse-Neige Tycoon ». Tout le code du jeu est dans `index.html` (CSS dans `<style>`, logique dans le `<script>` final, une IIFE). La seule bibliothèque est three.js r128, chargée depuis `vendor/three.min.js` en script UMD (global `THREE`).

## Règles

- Ne pas migrer vers une version plus récente de three.js sans vérification complète : le code s'appuie sur l'API r128 (`InstancedMesh.setColorAt`, `BufferAttribute.updateRange`, chunks de shader `#include <begin_vertex>` et `vec4 diffuseColor = vec4( diffuse, opacity );` patchés via `onBeforeCompile` pour les traces au sol).
- Pas de build, pas de bundler : le dossier se déploie tel quel.
- Textes visibles en français, apostrophe typographique ’, pas de tiret cadratin.
- La clé de sauvegarde `chasseNeigeTycoon_v1` ne doit pas changer, sinon les joueurs perdent leur partie.

## Déploiement

Hébergement statique, `index.html` à la racine, `vendor/` à côté. Vérifier après déploiement :

1. la page charge sans erreur dans la console ;
2. `vendor/three.min.js` répond en 200 ;
3. la partie se sauvegarde (recharger la page : le bouton d'accueil indique « Reprendre la partie »).

## Repères dans le code

- `MACHINES` : les 12 chasse-neige (prix, vitesse, largeur de lame, puissance, contrat).
- `WEATHERS` : la météo et ses primes.
- `buildMachine` : modèles 3D des machines.
- `house`, `gableRoof` : habitations (fusionnées par matériau pour limiter les appels de rendu).
- `refreshSnow`, `cellH`, `pushBerm` : surface de neige (champ de hauteur) et congères.
- `saltTime`, `clearT` : durée pendant laquelle une rue déneigée reste propre.
- `updatePile`, `dropPile` : bourrelet de neige devant la lame.
- `updateTracks` : traces de pneus, chenilles et pas.
- `updateProps`, `smash` : objets à casser et combos.
- `cabCam`, `updateCockpit` : vue cabine.
