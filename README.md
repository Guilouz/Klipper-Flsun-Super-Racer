# Configuration Klipper pour FLSUN Super Racer

![maxresdefault](https://user-images.githubusercontent.com/12702322/187098254-be0a0182-cc04-401a-9e95-97dda4bdb1b6.jpeg)

Klipper est un firmware d'imprimante 3D. Il combine la puissance d'un ordinateur à usage général avec un ou plusieurs microcontrôleurs.

Consultez le [document sur les fonctionnalités](https://www.klipper3d.org/Features.html) pour plus d'informations sur les raisons pour lesquelles vous devriez utiliser Klipper.

<br />

## Table des matières

- [Informations](#informations)
- [Liens utiles](#liens-utiles)
- [Fichiers STL nécessaires](#fichiers-stl-nécessaires)
- [Schémas de câblage](#schémas-de-câblage)
- [Installation de Klipper via MainsailOS](#installation-de-klipper-via-mainsailos)
- [Connexion via SSH](#connexion-via-ssh)
- [Mise à jour des dépendances](#mise-à-jour-des-dépendances)
- [Installation de KlipperScreen](#installation-de-klipperscreen)
- [Désactivation du PCI Express sur le CM4](#désactivation-du-pci-express-sur-le-cm4)
- [Installation de l'image de démarrage](#installation-de-limage-de-démarrage)
- [Installation du driver pour écran DSI & Caméra CSI](#installation-du-driver-pour-écran-dsi--caméra-csi)
- [Modification du fichier /boot/cmdline.txt](#modification-du-fichier-bootcmdlinetxt)
- [Modification du fichier /boot/config.txt](#modification-du-fichier-bootconfigtxt)
- [Installation du firmware Klipper sur la Manta M4P](#installation-du-firmware-klipper-sur-la-manta-m4p)
- [Configuration pour l'ADXL345](#configuration-pour-ladxl345)
- [Utilisation de la Configuration](#utilisation-de-la-configuration)
- [Changements coté Slicers](#changements-coté-slicers)
- [Calibrez votre imprimante](#calibrez-votre-imprimante)
- [Mettre à jour Mainsail](#mettre-à-jour-mainsail)
- [Mettre à jour KlipperScreen](#mettre-à-jour-klipperscreen)
- [Installer et mettre à jour Timelapse](#installer-et-mettre-à-jour-timelapse)
- [Utilisation du Neopixels Ring Light](#utilisation-du-neopixels-ring-light)
- [Remerciements](#remerciements)

<br />

Si vous aimez mon travail, n'hésitez pas à me soutenir en me payant une 🍺 ou un ☕. Merci 🙂 

[ ![Download](https://user-images.githubusercontent.com/12702322/115148445-e5a40100-a05f-11eb-8552-c1f5d4355987.png) ](https://www.paypal.me/CyrilGuislain)

<br />

## Informations

Cette configuration est compatible avec la FLSUN Super Racer uniquement et avec cette configuration :

- Carte mère BigTreeTech Manta M4P
- Raspberry Pi Compute Module 4
- Extrudeur Bondtech LGX Lite
- Bloc de chauffe Trianglelab CHC Pro (104NT-4-R025H42G) (en option, voir fichier printer.cfg)
- Drivers TMC 2209/2226
- LED Neopixel (en option, voir fichier printer.cfg)
- Ecran BigTreeTech PITFT70 V2.0

<br />

Cette configuration de Klipper pour la Super Racer doit être utilisée avec cette version de KlipperScreen disponible ici : [KlipperScreen-Flsun-Super-Racer](https://github.com/Guilouz/KlipperScreen-Flsun-Super-Racer)

<br />

## Liens utiles

- Pour calibrer votre extrudeur, voir ici : https://www.klipper3d.org/Rotation_Distance.html

- Pour régler le Pressure Advance, voir ici : https://www.klipper3d.org/Pressure_Advance.html

- Pour ajuster manuellement la compensation de résonance, voir ici : https://www.klipper3d.org/Resonance_Compensation.html

- Pour mesurer les Resonances avec l'ADXL, voir ici : https://www.klipper3d.org/Measuring_Resonances.html

- Pour utiliser la fonction Exclude Objects, voir ici : https://docs.mainsail.xyz/features/exclude_objects

- Pour afficher les vignettes à l'écran, voir ici : https://klipperscreen.readthedocs.io/en/latest/Thumbnails/

<br />

## Fichiers STL nécessaires

- Support pour BigTreeTech Manta M4P : https://www.printables.com/model/268979-flsun-super-racer-manta-m4p-mount
- Case pour écran BigTreeTech PITFT70 + Support : https://www.printables.com/model/268989-flsun-super-racer-pitft70-case-mount
- Easy connection pour ADXL : https://www.printables.com/model/268986-flsun-super-racer-easy-connection-for-adxl345
- Support ADXL : https://www.printables.com/model/245136-adxl345-mount-for-flsun-super-racer

<br />

## Schémas de câblage

- Avec branchement ADXL sur GPIO :

![Manta M4P SR](https://user-images.githubusercontent.com/12702322/187642336-86ce7061-2d1e-45b7-9825-e911b071344c.png)

- Avec branchement ADXL sur SPI :

![Manta M4P SR SPI](https://user-images.githubusercontent.com/12702322/209481248-77f039a0-3b70-4f84-8a0f-e2a2b1da71f2.png)

- Pins :

![Pins](https://user-images.githubusercontent.com/12702322/187642527-ae006f09-ed8e-44cc-a29e-cc6f2cf0a496.jpg)

<br />

## Installation de Klipper via MainsailOS

- Téléchargez et installez la dernière version de Raspberry Pi Imager ici : https://www.raspberrypi.com/software/
- Si vous utilisez un Raspberry Pi CM4 avec mémoire eMMC, vous aurez également besoin de RpiBoot :
	- Pour Windows : http://github.com/raspberrypi/usbboot/raw/master/win32/rpiboot_setup.exe
	- Pour MacOS : https://github.com/raspberrypi/usbboot#macos

- Lors de l'ouverture de Raspberry Pi Imager, les éléments suivants s'affichent :

![001](https://user-images.githubusercontent.com/12702322/209439292-4f0a528c-35f6-4648-a61c-d26c853f5343.jpg)

- Sélectionnez `CHOISISSEZ L'OS` et une fenêtre contextuelle s'ouvrira comme illustré ci-dessous.
- Faites défiler jusqu'à `Other specific-purpose OS` :

![002](https://user-images.githubusercontent.com/12702322/209439343-4af9c111-219e-47a3-b659-ce6bea414a8d.jpg)

- Sélectionnez `3D printing` :

![003](https://user-images.githubusercontent.com/12702322/209439366-c497b0cf-9d77-45ab-abd6-a1977951e220.jpg)

- Sélectionnez `Mainsail OS` :

![004](https://user-images.githubusercontent.com/12702322/209439427-b7fe98f3-d38e-46b5-bc8d-9109d87557bf.jpg)

- Puis la version désirée (32-bit ou 64-bit) :

![005](https://user-images.githubusercontent.com/12702322/209439432-099b1f87-9c28-4bb5-81dc-99362dddc877.jpg)

- Une fois cela fait, cliquez sur `CHOISISSEZ LE STOCKAGE` et sélectionnez la carte microSD souhaitée ou l'eMMC (voir la documentation de BigTreeTech page 21 : [ici](https://github.com/bigtreetech/Manta-M4P/blob/master/BIGTREETECH_M4P%26CB1%20User%20Manual.pdf)) :

![006](https://user-images.githubusercontent.com/12702322/209439491-9802bf1a-c9c8-4115-bd37-ba8be03c32a1.jpg)

- Le nom d'hôte, le SSH, le Wi-Fi, la langue et de nombreux autres paramètres peuvent désormais être parcourus et préconfigurés dans un menu de configuration, en cliquant sur la petite roue dentée dans le coin droit :

![007](https://user-images.githubusercontent.com/12702322/209439780-be655081-de4d-4516-bb54-612022e7b1f0.jpg)

- Configurez les divers paramètres comme suit :

![Sans titre](https://user-images.githubusercontent.com/12702322/210407996-71867cc7-5a5b-469f-b6bb-9dcee71441be.png)

Note : Si vous modifiez le paramètre `Set hotname`, l'URL de votre Raspberry Pi sera modifiée en conséquence.                                              Comme indiqué dans la capture d'écran ci-dessus, votre URL sera : http://flsun-super-racer.local

Veuillez également à ne pas changer le nom d’utilisateur `pi` !  La configuration de MainsailOS repose sur cet utilisateur.                                                                                                                             
- Cliquez ensuite sur `SAVE` pour sauvegarder ces paramètres.

- Vous pouvez ensuite cliquer sur `ÉCRIRE` :
     
![012](https://user-images.githubusercontent.com/12702322/209439815-56274a2a-e7ed-4454-9fb0-c67b75d3a724.jpg)

- Puis acceptez l'avertissement :

![013](https://user-images.githubusercontent.com/12702322/209439842-911fe29b-1682-40d7-85e5-499a423b6345.jpg)

- Cela prendra un certain temps pour écrire l'image sur la carte microSD ou l'eMMC :

![014](https://user-images.githubusercontent.com/12702322/209439856-64d53e40-028c-4e3a-a348-885ba5a25890.jpg)

-  Une fois l'écriture terminée, une vérification sera effectuée :

![015](https://user-images.githubusercontent.com/12702322/209439890-190698fc-4908-481d-8c1b-3fd1f6632a54.jpg)

- Une fois la vérification terminée, cliquez sur `CONTINUER` :

![016](https://user-images.githubusercontent.com/12702322/209439914-a571c3ea-7ccb-4bb7-bb28-66c980f196cb.jpg)

- L'installation est maintenant terminée.

<br />

## Connexion via SSH

- Téléchargez et installez le logiciel MobaXterm ici : https://mobaxterm.mobatek.net/download-home-edition.html

- Lancez-le puis cliquez sur l'icône `Session` puis `SSH` : 

![01](https://user-images.githubusercontent.com/12702322/209440762-d9efc473-22c3-484b-8250-71bb05db1e5f.jpg)
![02](https://user-images.githubusercontent.com/12702322/209440764-45f23603-8b33-4700-af43-ede574bf6287.jpg)

- Renseignez l'adresse IP de votre Raspberry Pi dans le champ `Remote Host`, cochez la case `Specify username` et saisissez le nom d'utilisateur `pi` dans le champ puis cliquez sur `OK` :

![Capture d’écran 2022-12-24 à 15 34 31](https://user-images.githubusercontent.com/12702322/209440775-9cb69f62-15b2-4407-8907-33c1733d8983.jpg)

- Sur la fenêtre qui s'affiche, saisissez votre mot de passe précédemment défini dans Raspberry Pi Imager (il ne s'affiche pas à la saisie, c'est normal) : 

![Capture d’écran 2022-12-24 à 15 39 29](https://user-images.githubusercontent.com/12702322/209440822-6af829bc-0f36-42c1-be75-faf411ea6a5c.jpg)

- Une fenêtre d'autorisation va s'afficher, autorisez-la. Il est également possible qu'une autre fenêtre vous demandant de changer le mot de passe s'affiche, ignorez-là.

- Une fois connecté, sur la partie gauche de la fenêtre vous avez l'accès aux dossiers et fichiers de votre Raspberry Pi et à la fenêtre d'invite de commande SSH sur la partie droite :

![Capture d’écran 2022-12-24 à 15 36 40](https://user-images.githubusercontent.com/12702322/209440829-aa86e3ff-5e24-4026-b321-370150fa3e58.jpg)

<br />

## Mise à jour des dépendances

- Dans la fenêtre d'invite de commande SSH, entrez la commande suivante pour télécharger la liste des mises à jour (vous devrez entrer le mot de passe root) :
```
sudo apt update
```

- Puis cette commande pour les installer :
```
sudo apt full-upgrade
```

- Supprimez ensuite les dépendances inutiles (une commande à la fois) :
```
sudo apt autoremove
sudo apt autoclean
sudo apt clean
```

- Vous pouvez également mettre à jour le firmware de votre Raspberry Pi en saisissant cette commande :
```
sudo rpi-update
```

- Puis saisissez la commande suivante pour redémarrer :
```python
sudo reboot
```

<br />

## Installation de KlipperScreen

- Dans la fenêtre d'invite de commande SSH, saisissez les commandes suivantes (une à la fois) :
```
git clone https://github.com/Guilouz/KlipperScreen-Flsun-Super-Racer.git
sudo mv /home/pi/KlipperScreen-Flsun-Super-Racer /home/pi/KlipperScreen
cd ~/KlipperScreen
./scripts/KlipperScreen-install.sh
```
- Puis saisissez la commande suivante pour redémarrer :
```python
sudo reboot
```

<br />

## Désactivation du PCI Express sur le CM4

La Manta M4P ne dispose pas de port PCI Express, il est donc nécessaire de désactiver la fonctionnalité pour éviter un message au démarrage.

- Créez le fichier `disable-pcie-overlay.dts` avec la commande suivante : 
```python
sudo nano /boot/overlays/disable-pcie-overlay.dts
```
- Copiez ce code dans la fenêtre qui s'affiche :
```
/*
 * disable-pcie-overlay.dts
 */

/dts-v1/;
/plugin/;

/ {
	compatible = "brcm,bcm2835";

	fragment@0 {
		target = <&pcie0>;
		__overlay__  {
			status = "disabled";
		};
	};
};
```
- Puis sur votre clavier appuyez sur les touches `Ctrl+X` pour quitter, `Y` pour sauvegarder et `Entrée` pour valider.

- Il faut ensuite convertir le fichier `disable-pcie-overlay.dts` en `disable-pcie-overlay.dtbo` avec la commande suivante :
```python
sudo dtc -@ -I dts -O dtb -o /boot/overlays/disable-pcie-overlay.dtbo /boot/overlays/disable-pcie-overlay.dts
```
- Puis supprimez le fichier `disable-pcie-overlay.dts` avec la commande suivante :
```python
sudo rm /boot/overlays/disable-pcie-overlay.dts
```

<br />

## Installation de l'image de démarrage

- Téléchargez ce pack puis dézipez-le : [Pack Boot](https://github.com/Guilouz/Klipper-Flsun-Super-Racer/files/10146997/Boot.Pack.zip)


- Faites glisser les 3 fichiers `initramfs.img`, `splash.txt` et `splash.png` dans la fenêtre de gauche en vous assurant d'être bien dans le répertoire `/home/pi/`.

- Dans la fenêtre d'invite de commande SSH, saisissez les commandes suivantes (une à la fois) :
```python
sudo cp /home/pi/splash.png /boot/
sudo cp /home/pi/splash.txt /boot/
sudo cp /home/pi/initramfs.img /boot/
```
- Vous pouvez ensuite supprimer ces 3 fichiers du répertoire `/home/pi/` en saisissant les commandes suivantes (une à la fois) :
```python
sudo rm /home/pi/splash.png
sudo rm /home/pi/splash.txt
sudo rm /home/pi/initramfs.img
```

<br />

## Installation du driver pour écran DSI & Caméra CSI

- Saisissez la commande suivante : 
```python
sudo wget https://datasheets.raspberrypi.com/cmio/dt-blob-disp1-cam1.bin -O /boot/dt-blob.bin
```

<br />

## Modification du fichier /boot/cmdline.txt

- Saisissez la commande suivante : 
```python
sudo nano /boot/cmdline.txt
```
- Sur la fenêtre qui s'affiche, remplacez le paramètre `console=tty1` par `console=tty3`

- Puis ajoutez ces éléments à la fin de la ligne :
```python
logo.nologo loglevel=0 vt.global_cursor_default=0 splash silent quiet
```
![Capture d’écran 2022-12-24 à 17 15 56](https://user-images.githubusercontent.com/12702322/209443857-f6760a96-c6aa-46ce-8f60-f439775c2dd2.jpg)

- Puis sur votre clavier appuyez sur les touches `Ctrl+X` pour quitter, `Y` pour sauvegarder et `Entrée` pour valider.

<br />

## Modification du fichier /boot/config.txt

- Saisissez la commande suivante : 
```python
sudo nano /boot/config.txt
```
- Sur la fenêtre qui s'affiche, ajoutez ces éléments au début du fichier :
```
## Splashcreen settings
initramfs initramfs.img
dtoverlay=disable-pcie-overlay
disable_splash=1
boot_delay=0
```
![Capture d’écran 2022-12-24 à 16 07 40](https://user-images.githubusercontent.com/12702322/209442001-4a7a2e8c-d9c0-455a-a0ea-c4e31f396155.jpg)

- Puis modifiez également ces lignes déjà présentes en ajoutant un "#" devant `dtoverlay=vc4-fkms-v3d` comme suit :
```
# Enable DRM VC4 V3D driver
#dtoverlay=vc4-kms-v3d
max_framebuffers=2
```
![Capture d’écran 2022-12-24 à 16 08 48](https://user-images.githubusercontent.com/12702322/209442063-3cc9816e-2477-4fba-8e12-bc1940143833.jpg)

- Puis également ces lignes en remplaçant la ligne `otg_mode=1` par `dtoverlay=dwc2,dr_mode=host` comme suit :

```
[cm4]
# Enable host mode on the 2711 built-in XHCI USB controller.
# This line should be removed if the legacy DWC2 controller is required
# (e.g. for USB device mode) or if USB support is not required.
dtoverlay=dwc2,dr_mode=host
```
![Capture d’écran 2022-12-24 à 17 01 17](https://user-images.githubusercontent.com/12702322/209443460-a3067521-2496-4134-9d15-36dbf2763f37.jpg)

- Puis sur votre clavier appuyez sur les touches `Ctrl+X` pour quitter, `Y` pour sauvegarder et `Entrée` pour valider.

- Vous pouvez maintenant saisir la commande suivante pour redémarrer le Raspberry Pi :
```python
sudo reboot
```

<br />

## Installation du firmware Klipper sur la Manta M4P

- Connectez-vous de nouveau en SSH et saisissez ces commandes (une à la fois) :
```shell
cd ~/klipper/
make menuconfig
```
- Sélectionnez ces paramètres :
```
[*] Enable extra low-level configuration options
    Micro-controller Architecture (STMicroelectronics STM32) --->
    Processor model (STM32G0B1)  --->
    Bootloader offset (8KiB bootloader) --->
    Clock Reference (8 MHz crystal) --->
    Communication interface (USB (on PA11/PA12)) --->
    USB ids  --->
()  GPIO pins to set at micro-controller startup
```
- Puis sur votre clavier appuyez sur la touche `Q` puis sur `Y` pour sauvegarder la configuration.

- Saisissez les commandes suivantes pour compiler le firmware (une à la fois) :
```python
make clean
make
```
- Récupérez le firmware nommé `Klipper.bin` sur la page de gauche dans le répertoire `/home/pi/klipper/out/`.

- Renommez-le en `firmware.bin`.

- Copiez-le à la racine d'une carte SD (et non microSD) formatée en FAT32 et une taille d'allocation de 4096.

- Insérez la carte SD dans la Manta M4P puis allumez l'imprimante.

- L'installation dure que quelques secondes, pour vérifier que le firmware a bien été installé, le fichier sur la carte SD doit avoir été renommé en `FIRMWARE.CUR`.

- Connectez-vous de nouveau en SSH puis saisissez la commande suivante afin de récupérer le serial USB de la Manta M4P :
```shell
ls /dev/serial/by-id/*
```
- Copiez la ligne qui s'affiche (dans un fichier texte par exemple), elle nous sera utile après.

<br /><br />

- Note :  Pour les futures mises à jour du firmware Klipper pour la Manta M4P, il est possible de flasher directement le firmware via SSH, pour cela :
  - Saisissez la commande suivante :
  ```python
  make flash FLASH_DEVICE=/dev/serial/by-id/XXXXX (en remplaçant les XXXXX par le serial obtenu précédemment)
  ```
  - Cela doit ressembler à ça :
  ```python
  make flash FLASH_DEVICE=/dev/serial/by-id/usb-Klipper_stm32g0b1xx_2F0034001050415833323520-if00
  ```
  - Il y aura un message d'erreur `dfu-util: Error during download get_status` après la mise à jour. N'y prêtez pas attention, le plus important c'est d'obtenir la ligne `File downloaded successfully`.

![Capture d’écran 2023-01-03 à 18 26 01](https://user-images.githubusercontent.com/12702322/210409758-87adfbc1-e817-4350-96a1-14418f6c6535.jpg)

<br />

## Configuration pour l'ADXL345

- Connectez-vous de nouveau en SSH puis saisissez les commandes suivantes (une à la fois) :
```python
cd ~/klipper/
sudo cp "./scripts/klipper-mcu-start.sh" /etc/init.d/klipper_mcu
sudo update-rc.d klipper_mcu defaults
```
- Il faut ensuite compiler le code du microcontrôleur en saisissant ces commandes (une à la fois) :
```python
cd ~/klipper/
make menuconfig
```
- Sur le menu, définissez `Microcontroller Architecture` sur `Linux process`, puis sur votre clavier appuyez sur la touche `Q` puis sur `Y` pour sauvegarder la configuration :

![Capture d’écran 2022-12-25 à 00 40 14](https://user-images.githubusercontent.com/12702322/209453373-8491cbee-75ad-47f3-a144-793fc4a85d13.jpg)

- Pour compiler et installer le microcontrôleur, saisissez les commandes suivantes (une à la fois) :
```python
sudo service klipper stop
make clean
make flash
sudo service klipper start
```
- Il suffit ensuite de dé-commenter (retirer le #) de la ligne suivante dans le fichier `printer.cfg` pour activer le support de l'ADXL :
```
[include adxl345.cfg]
```
- Cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

- Après redémarrage du firmware vous devriez voir le MCU de l'ADXL se connecter à Klipper.

- Vous pouvez tester l'accéléromètre en saisissant cette commande :
```
ACCELEROMETER_QUERY
```
- Quelque chose comme ceci doit être retourné :
```
accelerometer values (x, y, z): 5551.544565, 7048.078582, -1924.535449
```
- Entrez ensuite cette commande pour mesurer le bruit de l'accéléromètre pour chaque axe :
```
MEASURE_AXES_NOISE
```
- Vous devriez obtenir des chiffres de référence pour le bruit de l'accéléromètre sur les axes (ils devraient être compris dans la plage de ~ 1-100). Un bruit d'axes trop élevé (par exemple 1000 et plus) peut indiquer des problèmes de capteur, des problèmes d'alimentation ou des ventilateurs déséquilibrés trop bruyants.

- Pour mesurer les résonances, voir ici : https://www.klipper3d.org/Measuring_Resonances.html

<br />

## Utilisation de la Configuration

- Téléchargez et décompressez le fichier zip de mon référentiel ici : https://github.com/Guilouz/Klipper-Flsun-Super-Racer/archive/refs/heads/main.zip

- Rendez-vous sur l'interface Web de Mainsail via votre navigateur en saisissant l'adresse IP de votre Raspberry Pi.

- Rendez-vous dans l'onglet `Machine` puis importez les fichiers `KlipperScreen.conf`, `printer.cfg`, `neopixels.cfg`, `macros.cfg` et `adxl345.cfg` situés dans le répertoire `Configurations`.

- Une fois importés, ouvrez le fichier `printer.cfg` et modifiez la ligne suivante dans la section `Paramètres MCU` :
```python
serial: /dev/serial/by-id/XXXXX (en remplaçant les XXXXX par le serial obtenu précédemment)
```
- Cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

- Après redémarrage du firmware, vous devriez voir le MCU de la Manta M4P se connecter à Klipper.

<br />

## Changements coté Slicers

- Changez le Gcode de démarrage et le Gcode de fin dans les paramètres de votre Slicer tels quels :

  - Pour **Cura**:
    - Gcode de démarrage :
      ```
      ;Nozzle diameter = {machine_nozzle_size}
      ;Filament type = {material_type}
      ;Filament name = {material_brand} {material_name}
      ;Filament weight = {filament_weight}
      ;M109 S{material_print_temperature}
      ;M190 S{material_bed_temperature}

      START_PRINT BED_TEMP={material_bed_temperature_layer_0} EXTRUDER_TEMP={material_print_temperature_layer_0}
      ```
    - Gcode de fin :
      ```
      END_PRINT
      ```
    
  - Pour **PrusaSlicer** / **SuperSlicer**:
    - Gcode de démarrage :
      ```
      START_PRINT BED_TEMP=[first_layer_bed_temperature] EXTRUDER_TEMP=[first_layer_temperature]
      M104 S[first_layer_temperature]
      M190 S[first_layer_bed_temperature]
      ```
    - Gcode de fin :
      ```
      END_PRINT
      ```

  - Pour **LycheeSlicer**:
    - Gcode de démarrage :
      ```
      START_PRINT BED_TEMP={bed_temp} EXTRUDER_TEMP={temp}
      ```
    - Gcode de fin :
      ```
      END_PRINT
      ```

 <br />

- La rétraction Firmware donne un avantage comparé à la rétraction Slicer, elle peut être modifiée pendant une impression (depuis Mainsail ou Klipperscreen) et donc qu'un même gcode peut être imprimé avec des paramètres différents sans nécéssité d'être re-slicer.

  - Pour **Cura**, il est nécessaire d'installer le plugin `Klipper Settings Plugin` (disponible ici : [Klipper Settings Plugin](https://github.com/jjgraphix/KlipperSettingsPlugin)) et d'activer le paramètre `Enable Firmware Retraction` comme cela :
  
  ![190531375-dc2def8d-9190-47c8-ae6e-bc7efaf2ce04](https://user-images.githubusercontent.com/12702322/197653257-9a4c29cc-64c0-4aa4-9077-32b30a9634d2.jpg)

  - Pour **PrusaSclicer / SuperSlicer**, il est juste nécessaire d'activer le paramètre `Utiliser la rétraction du firmware` comme cela :

![206947349-f522cf58-ce9f-4bd4-88a6-e73893efeaa3](https://user-images.githubusercontent.com/12702322/209440013-48d939ae-3d20-46bd-aed7-29a66cddfd08.jpg)

<br />

## Calibrez votre imprimante

Ces calibrations peuvent être effectuées par l'interface Web de Mainsail avec des macros ou directement sur l'écran.

- Démarrez un PID BED et enregistrez la configuration.

- Démarrez un PID HOTEND et enregistrez la configuration.

- Démarrez une CALIBRATION ENDSTOP et enregistrez la configuration.

- Démarrez une CALIBRATION DELTA et enregistrez la configuration.

- Démarrez un BED LEVELING et enregistrez la configuration.

- Ajustez le Z-OFFSET, vous devez d'abord aller à Z=0, puis ajuster la position de la buse avec une feuille de papier.
  -Remarque : Le Z-Offset est enregistré en temps réel, y compris lors du réglage des babysteps.

<br />

## Mettre à jour Mainsail

- Rendez-vous sur l'interface Web de Mainsail puis cliquez sur l'onglet `Machine`.

- Ouvrez le fichier `moonraker.conf` et ajoutez les lignes suivantes :
```
[update_manager mainsail]
type: web
channel: stable
repo: mainsail-crew/mainsail
path: ~/mainsail
```
- Une fois terminé, cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

- Vous pouvez maintenant cliquer sur le bouton d'actualisation (toujours dans l'onglet Machine) sur la tuile `Gestionnaire de mise à jour`.

- Vous verrez apparaître une nouvelle ligne `mainsail`.

<br />

## Mettre à jour KlipperScreen

- Rendez-vous sur l'interface Web de Mainsail puis cliquez sur l'onglet `Machine`.

- Ouvrez le fichier `moonraker.conf` et ajoutez les lignes suivantes :
```
[update_manager KlipperScreen]
type: git_repo
path: /home/pi/KlipperScreen
origin: https://github.com/Guilouz/KlipperScreen-Flsun-Super-Racer.git
env: /home/pi/.KlipperScreen-env/bin/python
requirements: scripts/KlipperScreen-requirements.txt
install_script: scripts/KlipperScreen-install.sh
```
- Une fois terminé, cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

- Vous pouvez maintenant cliquer sur le bouton d'actualisation (toujours dans l'onglet Machine) sur la tuile `Gestionnaire de mise à jour`.

- Vous verrez apparaître une nouvelle ligne `KlipperScreen`.

<br />

## Installer et mettre à jour Timelapse

- Connectez-vous de nouveau en SSH puis saisissez les commandes suivantes (une à la fois) :
```python
cd ~/
git clone https://github.com/mainsail-crew/moonraker-timelapse.git
bash /home/pi/moonraker-timelapse/install.sh -c /home/pi/printer_data/config
```
- Rendez-vous ensuite  sur l'interface Web de Mainsail puis cliquez sur l'onglet `Machine`.

- Ouvrez le fichier `moonraker.conf` et ajoutez les lignes suivantes :
```python
[update_manager timelapse]
type: git_repo
primary_branch: main
path: ~/moonraker-timelapse
origin: https://github.com/mainsail-crew/moonraker-timelapse.git
managed_services: klipper moonraker
```
- Une fois terminé, cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

- Vous pouvez maintenant cliquer sur le bouton d'actualisation (toujours dans l'onglet Machine) sur la tuile `Gestionnaire de mise à jour`.

- Vous verrez apparaître une nouvelle ligne `timelapse`.

<br />

## Utilisation du Neopixels Ring Light

**Modes disponibles :**

- Allumer les Neopixels avec la macro `NEOPIXEL_ON`
- Eteindre les Neopixels avec la macro `NEOPIXEL_OFF`
- Allumer les Neopixels en bleu avec la macro `NEOPIXEL_BLUE`
- Allumer les Neopixels en rouge avec la macro `NEOPIXEL_RED`
- Allumer les Neopixels en vert avec la macro `NEOPIXEL_GREEN`
- Allumer les Neopixels en jaune avec la macro `NEOPIXEL_YELLOW`
- Allumer les Neopixels en orange avec la macro `NEOPIXEL_ORANGE`
- Allumer les Neopixels en violet avec la macro `NEOPIXEL_VIOLET`
- Allumer les Neopixels en fonction de la température de la buse (toutes les LEDs) avec la macro `HOTEND_GLOW`
- Allumer les Neopixels en fonction de la température de la buse (LED par LED) avec la macro `HOTEND_PROGRESS`
- Allumer les Neopixels en fonction de la température du plateau (toutes les LEDs) avec la macro `BED_GLOW`
- Allumer les Neopixels en fonction de la température du plateau (LED par LED) avec la macro `BED_PROGRESS`
- Allumer les Neopixels en fonction de la progression d'impression (toutes les LEDs) avec la macro `PERCENT_GLOW`
- Allumer les Neopixels en fonction de la progression d'impression (LED par LED) avec la macro `PERCENT_PROGRESS`
- Allumer les Neopixels en fonction de la vitesse d'impression (toutes les LEDs) avec la macro `SPEED_GLOW`
- Allumer les Neopixels en fonction de la vitesse d'impression (LED par LED) avec la macro `SPEED_PROGRESS`

**Nécéssaire :**

- Neon Flexible Tube 1m T1616-Side 10mm PCB : [Ici](https://fr.aliexpress.com/item/4000095850068.html?spm=a2g0o.store_pc_allProduct.8148356.60.19667739Amjjs4&pdp_npi=2%40dis%21EUR%21%E2%82%AC%2013%2C34%21%E2%82%AC%209%2C34%21%21%21%21%21%402100bddd16626284472777282ed43e%2112000015942927508%21sh)

- LED Strip 1 m 60 IP 30 : [Ici](https://fr.aliexpress.com/item/32699391341.html?spm=a2g0o.store_pc_groupList.8148356.1.58d547644pkzbu&pdp_npi=2%40dis%21EUR%21%E2%82%AC%208%2C79%21%E2%82%AC%205%2C71%21%21%21%21%21%402100bdde16626287458333294e75cc%2112000026565180770%21sh)

- Colliers de serrage 2.5 mm

- Support (STL) : [Ici](https://www.printables.com/model/272995-flsun-neopixels-ring-light-support)


**Configuration :**

- Rendez-vous sur l'interface Web de Mainsail puis cliquez sur l'onglet `Machine`.

- Ouvrez le fichier `printer.cfg` et modifiez la ligne suivante en supprimant le `#` au tout début :
```python
[include neopixels.cfg]
```
- Cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

- Toujours sur l'onglet `Machine`, ouvrez maintenant le fichier `KlipperScreen.conf` et copiez tout ce code juste avant la ligne `#~# --- Do not edit below this line. This section is auto generated --- #~#` :
```python
[menu __main actions neopixels]
name: {{ gettext('Neopixels') }}
icon: neopixels

[menu __main actions neopixels led_off]
name: {{ gettext('Off') }}
icon: neopixels-off
method: printer.gcode.script
params: {"script":"NEOPIXEL_OFF"}

[menu __main actions neopixels led_on]
name: {{ gettext('On') }}
icon: neopixels-on
method: printer.gcode.script
params: {"script":"NEOPIXEL_ON"}

[menu __main actions neopixels led_blue]
name: {{ gettext('Blue') }}
icon: neopixels-blue
method: printer.gcode.script
params: {"script":"NEOPIXEL_BLUE"}

[menu __main actions neopixels led_red]
name: {{ gettext('Red') }}
icon: neopixels-red
method: printer.gcode.script
params: {"script":"NEOPIXEL_RED"}

[menu __main actions neopixels led_green]
name: {{ gettext('Green') }}
icon: neopixels-green
method: printer.gcode.script
params: {"script":"NEOPIXEL_GREEN"}

[menu __main actions neopixels led_yellow]
name: {{ gettext('Yellow') }}
icon: neopixels-yellow
method: printer.gcode.script
params: {"script":"NEOPIXEL_YELLOW"}

[menu __main actions neopixels led_orange]
name: {{ gettext('Orange') }}
icon: neopixels-orange
method: printer.gcode.script
params: {"script":"NEOPIXEL_ORANGE"}

[menu __main actions neopixels led_violet]
name: {{ gettext('Violet') }}
icon: neopixels-violet
method: printer.gcode.script
params: {"script":"NEOPIXEL_VIOLET"}

[menu __main actions neopixels hotend_glow]
name: {{ gettext('Hotend (All)') }}
icon: extruder
method: printer.gcode.script
params: {"script":"HOTEND_GLOW"}

[menu __main actions neopixels hotend_progress]
name: {{ gettext('Hotend (One by One)') }}
icon: extruder
method: printer.gcode.script
params: {"script":"HOTEND_PROGRESS"}

[menu __main actions neopixels bed_glow]
name: {{ gettext('Bed (All)') }}
icon: bed
method: printer.gcode.script
params: {"script":"BED_GLOW"}

[menu __main actions neopixels bed_progress]
name: {{ gettext('Bed (One by One)') }}
icon: bed
method: printer.gcode.script
params: {"script":"BED_PROGRESS"}

[menu __main actions neopixels percent_glow]
name: {{ gettext('Progress (All)') }}
icon: clock
method: printer.gcode.script
params: {"script":"PERCENT_GLOW"}

[menu __main actions neopixels percent_progress]
name: {{ gettext('Progress (One by One)') }}
icon: clock
method: printer.gcode.script
params: {"script":"PERCENT_PROGRESS"}

[menu __main actions neopixels speed_glow]
name: {{ gettext('Speed (All)') }}
icon: speed+
method: printer.gcode.script
params: {"script":"SPEED_GLOW"}

[menu __main actions neopixels speed_progress]
name: {{ gettext('Speed (One by One)') }}
icon: speed+
method: printer.gcode.script
params: {"script":"SPEED_PROGRESS"}

[menu __print neopixels]
name: {{ gettext('Neopixels') }}
icon: neopixels

[menu __print neopixels led_off]
name: {{ gettext('Off') }}
icon: neopixels-off
method: printer.gcode.script
params: {"script":"NEOPIXEL_OFF"}

[menu __print neopixels led_on]
name: {{ gettext('On') }}
icon: neopixels-on
method: printer.gcode.script
params: {"script":"NEOPIXEL_ON"}

[menu __print neopixels led_blue]
name: {{ gettext('Blue') }}
icon: neopixels-blue
method: printer.gcode.script
params: {"script":"NEOPIXEL_BLUE"}

[menu __print neopixels led_red]
name: {{ gettext('Red') }}
icon: neopixels-red
method: printer.gcode.script
params: {"script":"NEOPIXEL_RED"}

[menu __print neopixels led_green]
name: {{ gettext('Green') }}
icon: neopixels-green
method: printer.gcode.script
params: {"script":"NEOPIXEL_GREEN"}

[menu __print neopixels led_yellow]
name: {{ gettext('Yellow') }}
icon: neopixels-yellow
method: printer.gcode.script
params: {"script":"NEOPIXEL_YELLOW"}

[menu __print neopixels led_orange]
name: {{ gettext('Orange') }}
icon: neopixels-orange
method: printer.gcode.script
params: {"script":"NEOPIXEL_ORANGE"}

[menu __print neopixels led_violet]
name: {{ gettext('Violet') }}
icon: neopixels-violet
method: printer.gcode.script
params: {"script":"NEOPIXEL_VIOLET"}

[menu __print neopixels hotend_glow]
name: {{ gettext('Hotend (All)') }}
icon: extruder
method: printer.gcode.script
params: {"script":"HOTEND_GLOW"}

[menu __print neopixels hotend_progress]
name: {{ gettext('Hotend (One by One)') }}
icon: extruder
method: printer.gcode.script
params: {"script":"HOTEND_PROGRESS"}

[menu __print neopixels bed_glow]
name: {{ gettext('Bed (All)') }}
icon: bed
method: printer.gcode.script
params: {"script":"BED_GLOW"}

[menu __print neopixels bed_progress]
name: {{ gettext('Bed (One by One)') }}
icon: bed
method: printer.gcode.script
params: {"script":"BED_PROGRESS"}

[menu __print neopixels percent_glow]
name: {{ gettext('Progress (All)') }}
icon: clock
method: printer.gcode.script
params: {"script":"PERCENT_GLOW"}

[menu __print neopixels percent_progress]
name: {{ gettext('Progress (One by One)') }}
icon: clock
method: printer.gcode.script
params: {"script":"PERCENT_PROGRESS"}

[menu __print neopixels speed_glow]
name: {{ gettext('Speed (All)') }}
icon: speed+
method: printer.gcode.script
params: {"script":"SPEED_GLOW"}

[menu __print neopixels speed_progress]
name: {{ gettext('Speed (One by One)') }}
icon: speed+
method: printer.gcode.script
params: {"script":"SPEED_PROGRESS"}
```
- Une fois terminé, cliquez sur `SAUVEGARDER ET REDÉMARRAGE` en haut à droite pour enregistrer le fichier.

<br />

## Remerciements

- [digitalninja-ro](https://github.com/digitalninja-ro/klipper-neopixel) pour les templates NeoPixels.
- [Desuuuu](https://github.com/Desuuuu/klipper-macros) & [danorder](https://github.com/danorder) pour les bases de certaines macros.
