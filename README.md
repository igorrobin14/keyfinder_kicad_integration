# Séance 7 de Design : intégration sur KiCad 7.0 d'un nouveau capteur sur le keyfinder de chez Action et redimensionnement

## Igor Robin - ZZ2 - F1

### Contenu du dépôt
- Les fichiers kiCad 7.0 correspondant au schématique, au circuit imprimé, ainsi qu'au projet lui-même
- Une photo du schématique montrant le branchement du nouveau composant
- Une photo de l'éditeur de PCB montrant le réagencement des composants
- Une vue 3D du PCB avec ce nouveau composant intégré
- Ce ```README.md```

###
*Utilisation : télécharger le dépôt complet, extraire l'archive .zip, mettre tous les fichiers qu'elle contient dans un dossier choisi, mettre au même niveau que le ficher projet (.kicad_pro) le dépôt complet qui se trouve à cette adresse :*
https://github.com/NordicPlayground/nrf5-eagle-reference-design
*Ouvrir le projet dans KiCad et faire en sorte que le package nRF52832 soit prit en compte*

## Introduction
Le but de cette séance de Design était de redimensionner le PCB afin qu'il corresponde à la forme modélisée sur Fusion 360, d'y intégrer un nouveau capteur et de réagencer les composants déjà présents afin de les faire rentrer sur le PCB avec sa forme et taille finale. Concernant le capteur, nous avons de le choisir, déterminer son utilité pour le produit, et enfin rechercher le capteur réel pour l'intégrer.

## Mise en œuvre

### Capteur choisi
Le nouveau capteur qui a été choisi pour être intégré est un capteur d'humidité et de température ENS210

### Utilité pour le produit
L'intérêt pour le keyfinder d'avoir un capteur de température et d'humidité est de pouvoir s'en servir comme thermomètre ou baromètre, ce qui permettrait d'obtenir des informations sur l'environnement situé autour de l'object auquel est rattaché le keyfinder. Bien évidemment, il y a peu de chances que l'on mette ses clés dans un environnement extrême le plus souvent, mais cela peut en revanche servir à améliorer le niveau d'information que l'on a sur la localisation du keyfinder. Si on a placé notre objet attaché au keyfinder dans un endroit chaud/froid, humide/sec, cela peut nous apporter une information supplémentaire au moment ou on arrive a côté de l'objet cherché pour le retrouver plus rapidement. Cela permet notamment de faire la distinction au niveau de la hauteur car l'application fournie avec le keyfinder ne nous renseigne pas sur celle-ci. Par exemple : nous sommes au niveau du keyfinder sur la minicarte mais celui-ci est en fait sur la terasse dehors, sur le toit, ou dans la cave. A ce moment, la mesure de température et de pression peuvent être cruciales pour s'y retrouver.

### Recherche du composant
L'empreinte du produit sur KiCad 7.0 est celle correspodant à un capteur ENS210 AMS_QFN-4-1. Lorsqu'on va sur Octopart, le composant le plus proche que l'on trouve de cette empreinte est un ENS210-LQFM de chez ScioSense.
Ses caractéristiques sont les suivantes :
- Technologie de communication utilisée : I²C
- Taille : 2.00 mm * 2.00 mm * 0.75 mm
- Prix : 1,727 $ / 100 unités achetées
- Disponibilité : disponible sur Digikey et Mouser notamment (stock de 170000 et 15000 respectivement)

### Lien pour acheter le composant
https://www.digikey.fr/en/products/detail/ENS210-LQFM/2618-ENS210-LQFMCT-ND/6490749?curr=usd&utm_campaign=buynow&utm_medium=aggregator&utm_source=octopart

### Défis relevés
- Afin de faire rentrer tous les composants sur la forme finale du PCB, le choix a été fait de retirer l'antenne Bluetooth mise au cours de la séance 5 pour la remplacer par un simple fil plus épais et mit en zig-zag
- Un défi important a été de corriger les erreurs signalées au moment de la réalisation de la DRC, mais celles-ci ont bel et bien été supprimées en routant correctement les fils pour relier les composants
- Il n'a pas fallu modifier la mécanique du PCB et/ou du keyfinder
- Une question subsiste : l'empreinte du porte-pile mit lors de la séance 6 n'est pas disponible sur KiCad 7.0 et par conséquent il n'est pas possible de savoir s'il peut être intégré sur l'autre face du PCB, néanmoins la place peut être jugée suffisamment grande, et il y a donc de grandes chances qu'il puisse être intégré.
