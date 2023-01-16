---
hide:
  - toc
---

# Calibration Delta Automatique

La calibration Delta consiste à trouver les positions de butée des tours, les angles des tours, le rayon delta et les longueurs des bras. 

Ces paramètres contrôlent les mouvements sur une imprimante Delta. Chacun d'eux a un impact non évident et non linéaire et il est difficile de les calibrer manuellement. En revanche, la calibration Delta automatique peut fournir d'excellents résultats en quelques minutes seulement.

<br />

- Pour démarrer la calibration Delta vous pouvez passer par l'écran ou lancer directement cette macro :

{==

:warning: Le capteur de nivellement doit être branché pour cette opération.

==}

``` yaml
DELTA_CALIBRATION
```

- Il est ensuite nécessaire de sauvegarder la configuration en cliquant sur la macro :

``` yaml
SAUVEGARDER
```

<br />

Vous trouverez plus d'informations sur la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Delta_Calibrate.html" target="blank">Delta Calibration | Klipper</a>

<br />
