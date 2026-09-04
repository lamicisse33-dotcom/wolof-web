# wolof.khalam.app — page d'attente

Une seule page. Elle affiche la marque KHALAM pendant que le serveur l’interprète se
réveille, puis bascule dessus toute seule.

## Pourquoi elle existe

Le serveur l’interprète est hébergé chez Render sur l'offre gratuite : il s'endort
après 15 minutes sans visite et met environ une minute à revenir. Pendant ce
temps, Render affiche **sa** page à lui — fond noir, logo Render,
« APPLICATION LOADING ». Sur une démonstration, c'est la marque de
l'hébergeur qu'on montre.

Cette page-ci vit ailleurs (GitHub Pages, toujours éveillé). Elle s'affiche
tout de suite, réveille le serveur en arrière-plan, et n'ouvre l’interprète qu'une
fois qu'il répond vraiment.

## Ce qu'il faut savoir

- Le raccourci de l'écran d'accueil doit pointer sur **wolof.khalam.app**,
  plus sur l'adresse Render.
- Le fichier `CNAME` porte le sous-domaine. Ne pas le supprimer : GitHub Pages
  s'en sert pour servir le site sous ce nom.
- Si l'adresse du serveur change un jour, une seule ligne à modifier dans
  `index.html` :

      const SERVEUR = 'https://interprete-wolof.onrender.com';

## Réglage DNS (fait une fois, chez Namecheap)

Un enregistrement **CNAME** : hôte `wolof`, valeur `lamicisse33-dotcom.github.io`

## L'icône

`icone.svg` est le dessin d'origine : la balance KHALAM, une pastille bleue sur
le plateau du français, une verte sur celui du wolof — les couleurs des deux
drapeaux, volontairement plus vives qu'eux : sur ce bleu nuit, un bleu foncé se
perdrait dans le fond à la taille d'une icône.

Les fichiers `icone-32/180/192/512.png` en sont tirés — ne pas les modifier à la
main, les regénérer :

    for t in 180 192 512 32; do
      convert -background '#0B1020' -density $((t*4)) icone.svg \
              -resize ${t}x${t} -depth 8 -strip icone-${t}.png
    done

L'image reste **carrée et opaque** : iOS arrondit lui-même les coins.

Le raccourci de l'écran d'accueil ne change pas d'icône tout seul : il faut le
supprimer et le recréer depuis Safari (Partager → Sur l'écran d'accueil).
