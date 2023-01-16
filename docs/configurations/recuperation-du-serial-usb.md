---
hide:
  - toc
---

# Récupération du Serial USB

Cette étape permet de récupérer le serial USB de la carte mère afin que Klipper puisque communiquer avec votre imprimante.


- Assurez-vous que votre imprimante est connectée sur l’un des ports USB du Raspberry Pi.

- Connectez-vous en SSH puis saisissez la commande suivante afin de récupérer le serial USB et s’assurer que l’imprimante communique bien avec votre Raspberry Pi :

``` yaml
ls /dev/serial/by-id/*
```

- Copiez la ligne qui s'affiche (dans un fichier texte par exemple), elle nous sera utile plus tard :

![Serial](../assets/img/configurations/serial.png){ width="600" }

{==

:octicons-info-16: Chaque serial est différent, il est donc normal que vous n'ayez pas exactement le même que celui de l'illustration.

==}

<br />

Vous pouvez ensuite continuer vers la section :material-arrow-right-box: [Installation des fichiers de configuration](../configurations/fichiers-de-configuration.md).
