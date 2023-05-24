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

<br />

{==

:warning: Si vous rencontrez le message **No such file or directory** lors de la tentative de récupération du serial USB, plusieurs éléments sont alors à vérifier :

==}

- Assurez-vous que l'imprimante est allumée.

- Vérifiez le branchement du câble USB de votre imprimante à votre Raspberry Pi, si nécessaire utilisez un autre câble USB.

- Assurez-vous que le firmware Klipper de l'imprimante a été correctement flashé.

- Il est également possible que vous ayez une version de udev qui a un bug connu (version : 247.3-7+deb11u2 ou 247.3-7+rpi1+deb11u2) et qui n'est pas corrigé dans les versions de MainsailOS inférieures à 1.2.0. Ce qui ne crée pas de liens symboliques /dev/serial/by-id pour votre MCU.

- Pour corriger cela, saisissez la commande suivante :

``` yaml
curl -sSL https://raw.githubusercontent.com/mainsail-crew/MainsailOS/develop/patches/udev-fix.sh | bash
```

- Cela vous demandera votre mot de passe sudo.

{==

:warning: N'EXÉCUTEZ PAS CE PATCH SI VOUS IMPRIMEZ !!!

==}

- Après le redémarrage vous devriez pouvoir récupérer le serial via la commande :

``` yaml
ls /dev/serial/by-id/*
```

- Si cela ne fonctionne toujours pas, vous pouvez alors utiliser la commande suivante :

``` yaml
ls /dev/serial/by-path/*
```

<br />

Vous pouvez ensuite continuer vers la section :material-arrow-right-box: [Installation des fichiers de configuration](../configurations/fichiers-de-configuration.md).
