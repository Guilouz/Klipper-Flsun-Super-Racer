---
hide:
  - toc
---

# Calibration des EndStops

Cette fonctionnalité peut améliorer la précision des interrupteurs de fin de course traditionnels.

Un interrupteur de fin de course typique a une précision d'environ 100 microns. A chaque fois qu'un axe est mis en Home, l'interrupteur peut se déclencher légèrement plus tôt ou légèrement plus tard. Bien qu'il s'agisse d'une erreur relativement faible, elle peut entraîner des artefacts indésirables et cela  peut être perceptible lors de l'impression de la première couche d'une impression.

<br />

- Pour calibrer les EndStops vous pouvez passer par l'écran ou lancer directement cette macro :

``` yaml
ENDSTOPS_CALIBRATION
```

{==

:octicons-info-16: Le capteur de nivellement n'est pas nécessaire pour cette opération.

==}

- Cette fonction effectuera plusieurs déplacements de bas en haut.

- Il est ensuite nécessaire de sauvegarder la configuration en cliquant sur la macro :

``` yaml
SAUVEGARDER
```

<br />

Vous trouverez plus d'informations sur la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Endstop_Phase.html" target="blank">Endstop Phase | Klipper</a>

<br />
