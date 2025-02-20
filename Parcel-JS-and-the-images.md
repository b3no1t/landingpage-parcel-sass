# Parcel JS and the images

## Image

Parcel intègre un support pour **le redimensionnement, la conversion et l'optimisation des images. Les images peuvent être** référencées à partir de fichiers HTML, CSS, JavaScript ou tout autre type de fichier.

### Redimensionner et convertir des images

Parcel inclut un **transformateur d'image prêt à l'emploi**, qui vous permet de redimensionner les images, de les convertir dans un format différent ou d'ajuster la qualité pour réduire la taille du fichier.
Cela peut être effectué à l'aide de paramètres de requête lors du référencement de l'image ou à l'aide d'un fichier de configuration .

Le transformateur d'image s'appuie sur la bibliothèque de transformation d'image *Sharp* , qui sera automatiquement installée en tant que dépendance de développement dans votre projet lorsque cela est nécessaire.

**Les paramètres de requête que vous pouvez utiliser sont :**

`width` La largeur pour redimensionner l’image
`height` La hauteur à laquelle redimensionner l’image
`quality` Le pourcentage de qualité d’image souhaité, par exemple?quality=75
`as`  Format de fichier vers lequel convertir l’image, par exemple :?as=webp

### Formats d'image

Les formats d'image suivants sont pris en charge, à la fois en entrée et en sortie via le *as*, paramètre de requête :

`jpeg` \ `jpg`  est un format d'image avec perte très largement pris en charge. 
Il est souvent utilisé pour les photos et offre une compression relativement bonne, mais *ne prend pas en charge la transparence ou la compression sans perte*.

`png`  Portable Network Graphics (PNG) est un format d'image sans perte. 
Les PNG sont généralement beaucoup *plus volumineux que les JPEG* ou d'autres formats d'image avec perte, mais prennent *en charge la transparence* et offrent une qualité bien supérieure pour les détails fins.

`WebP` prend en charge la compression avec et sans perte, ainsi que l'animation et la transparence. Il est pris en charge par tous les navigateurs modernes et offre une meilleure compression pour la même qualité que les fichiers JPEG et PNG.

`AVIF` est un nouveau format d'image avec perte basé sur le codec vidéo AV1 qui offre des améliorations significatives en termes de compression et de qualité par rapport aux formats JPEG et WebP.
*Il est actuellement pris en charge dans les dernières versions de Chrome et Firefox.*

Les GIF sont également pris en charge si vous configurez une version libvips personnalisée . 
Cependant, l'utilisation de GIF est déconseillée en raison de leur taille de fichier importante. 
Utilisez plutôt un format vidéo.

Pour plus de conseils sur le choix des bons formats d'image, consultez le guide sur web.dev .

Exemple de code HTML :
```html
    <picture>
      <source srcset="image.jpeg?as=avif&width=800" type="image/avif" />
      <source srcset="image.jpeg?as=webp&width=800" type="image/webp" />
      <source srcset="image.jpeg?width=800" type="image/jpeg" />
      <img src="image.jpeg?width=200" alt="test image" />
    </picture>
```