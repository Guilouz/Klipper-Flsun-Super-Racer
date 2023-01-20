---
hide:
  - toc
---

# Mesure du Z-Offset

Le Z-Offset est la distance entre la buse et le plateau lorsque le palpeur se déclenche.

<br />

- Pour mesurer le Z-Offset vous pouvez passer par l'écran ou lancer directement cette macro :

{==

:warning: Le capteur de nivellement doit être branché pour cette opération.

==}

``` yaml
Z_OFFSET_CALIBRATION
```

- Cette fonction effectuera une palpation sur le plateau, puis soulèvera la tête et démarrera la fonction d'ajustement manuelle :

![Z-Offset](../assets/img/calibrations/zoffset-1.png){ width="400" }

- Retirez alors le palpeur et à l'aide d'un morceau de papier pour "photocopieuse" entre le plateau et la buse, ajustez la hauteur du Z jusqu'à ressentir une petite friction lorsque l'on pousse le papier d'avant en arrière. Cela permet de déterminer la distance réelle entre la buse et le plateau.

{==

:octicons-info-16: Préférez utiliser les boutons de la section **ADVANCED**, ils sont plus précis et cela pourrait éviter que de la buse vienne forcer sur le plateau.

==}

- Une fois ces étapes terminées, vous pouvez cliquer sur **ACCEPT** pour valider la mesure du Z-Offset.

- Il est ensuite nécessaire de sauvegarder la configuration en cliquant sur la macro :

``` yaml
SAUVEGARDER
```

<br />

- Suite à une mesure du Z-Offset, après toute vos autres calibrations effectuées, je recommande d'appliquer un Offset de sécurité de 2 mm via la macro :

``` yaml
SECURITY_OFFSET
```

{==

:octicons-info-16: Cela pourrait éviter que la buse vienne gratter ou s'enfoncer sur le plateau en cas d'un mauvais ajustement du Z-Offset.

==}

- Après avoir effectué toutes les calibrations de l'imprimante, démarrez ensuite une impression et ajustez la première couche à l'aide des babysteps via le bouton **Ajustements** de KlipperScreen ou via la section **Tête d'impression** de Mainsail :

![Z-Offset](../assets/img/calibrations/zoffset-2.png){ width="400" }

{==

:warning: Ne pas sauvegarder la valeur du Z-Offset, une macro se charge de le faire automatiquement dans le fichier **variables.cfg** et de recharger cette valeur automatiquement au démarrage de Klipper.

==}

![Z-Offset](../assets/img/calibrations/zoffset-3.png){ width="400" }

- Vous trouverez un STL de test de première couche ici : :material-download: <a href="https://github.com/Guilouz/Klipper-Flsun-Super-Racer/raw/main/Downloads/First_Layer_Test.stl" target="_blank">First_Layer_Test.stl</a>

<br />

Vous trouverez plus d'informations sur la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Probe_Calibrate.html#calibrating-probe-z-offset" target="blank">Calibrating Probe Z Offset | Klipper</a>

<br />
