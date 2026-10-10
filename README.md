# Rover Sélène

Une Lune en 3D à explorer dans le navigateur : orbite libre, vaisseau de combat, rover blindé et alunissage du module Eagle d'Apollo 11. Tout tient dans un seul fichier `index.html`. Le relief lunaire, les cratères, la Terre, les nuages, les étoiles et les bruitages sont générés au chargement : il n'y a aucune image ni aucun fichier son.

## Lancer

Ouvre `index.html` dans un navigateur récent (Chrome, Edge, Firefox ou Safari) avec WebGL activé. Il faut une connexion Internet pour charger Three.js et les polices depuis leurs CDN. La génération du terrain prend quelques secondes.

Si l'ouverture directe du fichier pose problème, sers le dossier avec un petit serveur local :

```bash
python -m http.server 8000
```

puis va sur `http://localhost:8000`.

## Modes

| Touche | Mode | Principe |
|---|---|---|
| `1` | Orbite | Tourner autour de la Lune, de la Terre ou du Soleil, zoomer, plonger vers un point en double-cliquant |
| `2` | Vaisseau | Le vaisseau tourne vers le curseur, les tirs partent vers lui. Des drones attaquent par vagues |
| `3` | Rover | Rover blindé 6×6, tourelle qui suit la souris. Des rovers ennemis attaquent par vagues |
| `4` | Alunissage | Descente du module lunaire à travers 9 anneaux jusqu'à une cible, avec un score |

## Commandes principales

**Vaisseau** : souris pour diriger et viser, clic gauche pour le canon rapide, clic droit pour les canons lourds, `E` pour les missiles à tête chercheuse, `Z`/`S` pour la poussée, `Q`/`D` pour le roulis, `Espace`/`C` pour monter et descendre, clic molette pour tourner la caméra.

**Rover** : `ZQSD` (ou `WASD`, ou les flèches) pour conduire, souris pour viser, clic gauche pour le canon, clic droit pour les mitrailleuses, `F` pour les roquettes guidées, `V` pour que la caméra suive la souris, `L` pour les phares, `R` pour redresser.

**Alunissage** : `Espace` pour le moteur, `ZQSD` pour incliner le module. Pour réussir, il faut se poser à moins de 3 m/s et presque à plat. Une fois posé, `Espace` fait décoller l'étage de remontée.

**Partout** : `X` active ou arrête le combat, `M` coupe le son.

## Ce qui se passe à l'écran

- Tirer au même endroit creuse le sol : les cratères s'additionnent.
- On peut bombarder la Terre depuis le vaisseau : cratères, villes qui s'éteignent, trous dans les nuages, lave.
- Les meilleurs scores sont gardés dans le navigateur.

## Technique

- [Three.js](https://threejs.org/) r128 avec rendu HDR, halo lumineux (bloom) et ombres.
- Relief lunaire procédural (mers, environ 11 000 cratères, traînées claires) et détails de surface calculés par le GPU.
- Physique simplifiée sur une sphère : gravité, suspensions, trajectoires balistiques, missiles guidés.
- Bruitages synthétisés en direct avec la Web Audio API.

Projet réalisé avec Claude Code.
