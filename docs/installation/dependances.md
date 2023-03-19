---
hide:
  - toc
---

# Installation des dépendances

Cette étape permet d'installer les dernières mises à jour disponibles, de supprimer les dépendances et fichiers inutiles afin d'avoir un système d'expoitation "propre" et sain.


- Dans la fenêtre d'invite de commande SSH, entrez la commande suivante pour télécharger la liste des mises à jour (vous devrez entrer le mot de passe du Raspberry Pi) :

``` yaml
sudo apt update
```

- Puis cette commande pour les installer :

``` yaml
sudo apt full-upgrade -y
```

- Supprimez ensuite les dépendances inutiles (une commande à la fois) :

``` yaml
sudo apt autoremove
```
``` yaml
sudo apt autoclean
```
``` yaml
sudo apt clean
```

- Vous pouvez également mettre à jour le firmware de votre Raspberry Pi en saisissant cette commande :

``` yaml
sudo rpi-update
```

- Puis saisissez les commandes suivantes (une commande à la fois) :

``` yaml
sudo rm -rf /home/pi/mainsail-config
```
``` yaml
sudo rm  /home/pi/printer_data/config/mainsail.cfg
```
	
- Puis saisissez la commande suivante pour redémarrer :

``` yaml
sudo reboot
```

<br />

Vous pouvez ensuite continuer vers la section de compilation du firmware Klipper en fonction de votre carte mère :

:material-arrow-right-box: [Compilation du firmware sur MKS Robin Nano v3.x](../firmwares/compilation-mks-robin-nano.md)

:material-arrow-right-box: [Compilation du firmware sur BigTreeTech SKR 1.3](../firmwares/compilation-btt-skr1.3.md)

:material-arrow-right-box: [Compilation du firmware sur BigTreeTech SKR 2.0](../firmwares/compilation-btt-skr2.0.md)
