---
hide:
  - toc
---

# Input Shaping

Klipper intégre le support de l'accéléromètre ADXL345, qui peut être utilisé pour mesurer les fréquences de résonance de l'imprimante pour différents axes, et régler automatiquement les paramètres d'entrée pour compenser les résonances. Cela permet de réduire l'ondulation (également connue sous le nom de ghosting) sur les impressions.

<br />

Il en convient que vous ayez suivi la procédure de configuration de l'ADXL au préalable via cette section :material-arrow-right-box: [Configuration de l'ADXL](../configurations/adxl.md).

- Pour tester la connexion de l'accéléromètre, lancez la macro suivante :

``` yaml
ADXL_TEST
```

- Quelque chose comme ceci doit être renvoyé dans l’invite de commande de Mainsail :

``` yaml
accelerometer values (x, y, z): 5551.544565, 7048.078582, -1924.535449
```

- Pour mesurer le bruit de l'accéléromètre pour chaque axe, lancez la macro suivante :

``` yaml
ADXL_NOISE
```

- Vous devriez obtenir des chiffres de référence pour le bruit de l'accéléromètre sur les axes (ils devraient être compris dans la plage de ~ 1-100). Un bruit d'axes trop élevé (par exemple 1000 et plus) peut indiquer des problèmes de capteur, des problèmes d'alimentation ou des ventilateurs déséquilibrés trop bruyants.


- Pour mesurer les résonances de l’axe X, lancez la macro suivante :

``` yaml
ADXL_AXE_X
```

- Le résultat vous indique le type et la fréquence recommandée pour l'axe X ainsi que la valeur d'accélération maximum recommandée.

- Pour mesurer les résonances de l’axe X, lancez la macro suivante :

``` yaml
ADXL_AXE_Y
```

- Le résultat vous indique le type et la fréquence recommandée pour l'axe Y ainsi que la valeur d'accélération maximum recommandée.

- Il est ensuite nécessaire de sauvegarder la configuration en cliquant sur la macro :

``` yaml
SAUVEGARDER
```

- Rendez-vous dans l'onglet **Machine** sur le menu latéral gauche, ouvrez le fichier **printer.cfg** et modifiez la ligne **max_accel** de la section **Paramètres Imprimante** en reportant la plus petite des deux valeurs d'accélération maximum recommandées obtenue :

``` yaml hl_lines="8" title="printer.cfg"
########################################
# Paramètres Imprimante
########################################

[printer]
kinematics: delta
max_velocity: 300
max_accel: 3700
max_accel_to_decel: 2000
square_corner_velocity: 5.0
```

- Commentez (ajoutez un #) devant la ligne suivante dans le fichier **printer.cfg** pour désactiver la prise en charge de l’ADXL :

``` yaml title="printer.cfg"
#[include adxl345.cfg]  #Activer si vous souhaitez utiliser l'ADXL (doit être désactivé après utilisation)
```

- Cliquez sur **SAUVEGARDER ET REDÉMARRAGE** en haut à droite pour enregistrer le fichier.

{==

:octicons-info-16: Les tests de résonances doivent de nouveau être effectués après une maintenance sur l'imprimante ou si celle-ci a été déplacée.
  
==}

<br />

Vous trouverez plus d'informations sur la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Measuring_Resonances.html#measuring-the-resonances" target="blank">Mesasuring Resonances | Klipper</a>

A noter que ces mesurances peuvent également être faites sans ADXL, cependant cela reste moins précis. Voir la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Resonance_Compensation.html" target="blank">Resonance Compensation | Klipper</a>

<br />
