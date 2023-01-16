---
hide:
  - toc
---

# Calibration des PID

Il est important de réaliser les calibrations de PID afin d'avoir une chauffe constante de la buse et du plateau.

<br />

- Pour calibrer le **PID de la Buse**, lancez la macro suivante :

``` yaml
CALIBRATION_PID_HOTEND_220
```

{==

:octicons-info-16: Il est possible de choisir la température de calibration de la buse en cliquant sur la flèche de la macro.

==}

- Les nouvelles valeurs PID de la buse seront enregistrées automatiquement dans le fichier **printer.cfg** à la fin du processus.

<br />

- Pour calibrer le **PID du Plateau**, lancez la macro suivante :

``` yaml
CALIBRATION_PID_BED_65
```

{==

:octicons-info-16: Il est possible de choisir la température de calibration du plateau en cliquant sur la flèche de la macro.

==}

- Les nouvelles valeurs PID du plateau seront enregistrées automatiquement dans le fichier **printer.cfg** à la fin du processus.

<br />

Vous trouverez plus d'informations sur la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Config_checks.html?h=pid#calibrate-pid-settings" target="blank">Calibrate PID settings | Klipper</a>

<br />
