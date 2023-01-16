---
hide:
  - toc
---

# Installation du firmware sur MKS Robin Nano V3.0/V3.1

- Récupérez le firmware nommé **klipper.bin** dans le répertoire suivant :

``` yaml
/home/pi/klipper/out/
```

{==

:octicons-info-16: Vous pouvez faire un clic droit sur le fichier **klipper.bin** puis **Download** et sélectionner l’emplacement de destination sur votre ordinateur via **MobaXterm** sous Windows ou via **Cyberduck** sous macOS.

==}

- Renommez-le fichier **klipper.bin** en **Robin_nano_v3.bin**.

- Copiez le firmware **Robin_nano_v3.bin** à la racine d'une carte microSD formatée en **FAT32** et une taille d’allocation de **4096**.

- Insérez la carte microSD dans la Super Racer puis allumez l'imprimante.

- L'installation dure que quelques secondes.

- Retirez ensuite la carte microSD de l’imprimante et redémarrez la.

- Pour vérifier que le firmware a bien été installé, le fichier sur la carte microSD doit avoir été renommé en **ROBIN_NANO_V3.CUR**.

<br />

Vous pouvez ensuite continuer vers la section :material-arrow-right-box: [Récupération du Serial USB](../configurations/recuperation-du-serial-usb.md).
