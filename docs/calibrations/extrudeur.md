---
hide:
  - toc
---

# Calibration de l'extrudeur

Sur un extrudeur, la distance de rotation est la distance parcourue par le filament pour une rotation complète du moteur pas à pas. La meilleure façon d'obtenir une valeur précise pour ce paramètre est d'utiliser une procédure de "mesure et ajustement".

{==

:warning: Assurez-vous que l'extrudeur contient du filament, que la hotend est chauffée à une température appropriée et que l'imprimante est prête à extruder.

==}

<h2 style="color:#86be7c"><b>Procédure :</b></h2>

- Utilisez un marqueur pour placer une marque sur le filament à **120 mm** de l'entrée de l'extrudeur.

- Utilisez ensuite un pied à coulisse numérique pour mesurer la distance réelle de cette marque aussi précisément que possible. Notez cette valeur de **120** mm comme {==distance_de_la_marque==}.

- Via la section console de Mainsail ou de KlipperScreen, extrudez **100 mm** de filament avec la séquence de commande suivante. Notez cette valeur de **100** mm comme {==distance_demandée==} :

``` yaml
G91
```

``` yaml
G1 E100 F100
```

- Attendez que l'extrudeur termine le mouvement (cela prendra plusieurs secondes). Il est important d'utiliser une vitesse d'extrusion lente pour ce test, car une vitesse plus rapide peut provoquer une pression élevée dans l'extrudeur, ce qui fausserait les résultats. N'utilisez donc pas les boutons d'extrusion depuis Mainsail ou l’écran pour ce test car ils extrudent à un rythme rapide.

- Utilisez ensuite un pied à coulisse numérique pour mesurer la nouvelle distance entre l’entrée de l'extrudeur et la marque sur le filament. Notez cette valeur comme {==distance_mesurée==}.

- Calculez ensuite : 

    {==distance_de_la_marque==} :fontawesome-solid-minus: {==distance_mesurée==} :fontawesome-solid-arrow-right-long: {==distance_extrusion==}

- Récupérez ensuite la valeur {==rotation_distance_actuelle==} dans le fichier **printer.cfg** à la ligne **rotation_distance:** de la section **Paramètres Extrudeur & Driver** :

``` yaml hl_lines="10" title="printer.cfg"
########################################
# Paramètres Extrudeur & Driver
########################################

[extruder]
step_pin: PD6
dir_pin: PD3
enable_pin: !PB3
microsteps: 16
rotation_distance: 7.805
full_steps_per_rotation: 200
nozzle_diameter: 0.4
filament_diameter: 1.750
```

- Calculez la rotation_distance comme suit :

    {==rotation_distance_actuelle==} :fontawesome-solid-xmark: {==distance_extrusion==} :fontawesome-solid-divide: {==distance_demandée==} :fontawesome-solid-arrow-right-long: {==rotation_distance==}

- Remplacez ensuite la nouvelle valeur dans le fichier **printer.cfg** en arrondissant la nouvelle **rotation_distance** à trois décimales.

<h2 style="color:#86be7c"><b>Exemple :</b></h2>

- Après avoir extrudé 100 mm, je mesure une distance de **18** mm entre l’entrée de mon extrudeur et le trait sur le filament.

- J’ai donc :

    * Ma valeur initiale {==distance_de_la_marque==} de **120** mm.
    * Ma valeur demandée {==distance_demandée==} de **100** mm.
    * Ma valeur obtenue {==distance_mesurée==} de **18** mm.

- Je calcule donc ma distance d’extrusion actuelle pour 100 mm demandée :

    {==distance_de_la_marque==} :fontawesome-solid-minus: {==distance_mesurée==} :fontawesome-solid-arrow-right-long: {==distance_extrusion==}

    120 :fontawesome-solid-minus: 18 :fontawesome-solid-arrow-right-long: **102** mm

- Je récupére la valeur {==rotation_distance_actuelle==} dans le fichier **printer.cfg**.

- Je calcule donc ensuite ma nouvelle valeur de rotation_distance :

    {==rotation_distance_actuelle==} :fontawesome-solid-xmark: {==distance_extrusion==} :fontawesome-solid-divide: {==distance_demandée==}

    7.805 :fontawesome-solid-xmark: 102 :fontawesome-solid-divide: 100 :fontawesome-solid-arrow-right-long: **7.9611**

- Je remplace donc la ligne **rotation_distance: 7.805** du fichier **printer.cfg** par **rotation_distance: 7.961**.

<br />

Vous trouverez plus d'informations sur la documentation officielle : :material-web: <a href="https://www.klipper3d.org/Rotation_Distance.html" target="blank">Rotation Distance | Klipper</a>

<br />
