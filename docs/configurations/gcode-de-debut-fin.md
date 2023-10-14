---
hide:
  - toc
---

# Gcode de Début / Fin

Il est nécessaire de modifier votre Gcode de Début et de Fin dans votre Slicer car ils sont désormais intégrés dans les macros.

Cela a pour avantage de pouvoir imprimer un même modèle avec des Gcodes de Début et de Fin différents.


<h2 style="color:#86be7c"><b>Pour Cura :</b></h2>

- Gcode de démarrage :

``` yaml
;Nozzle diameter = {machine_nozzle_size}
;Filament type = {material_type}
;Filament name = {material_brand} {material_name}
;Filament weight = {filament_weight}
;M109 S{material_print_temperature}
;M190 S{material_bed_temperature}
START_PRINT BED_TEMP={material_bed_temperature_layer_0} EXTRUDER_TEMP={material_print_temperature_layer_0}

```

- Gcode de fin :

``` yaml
END_PRINT
```

<h2 style="color:#86be7c"><b>Pour PrusaSlicer / SuperSlicer :</b></h2>

- Gcode de démarrage :

``` yaml
M140 S0
M104 S0
START_PRINT BED_TEMP=[first_layer_bed_temperature] EXTRUDER_TEMP=[first_layer_temperature]
```

- Gcode de fin :

``` yaml
END_PRINT
```

<h2 style="color:#86be7c"><b>Pour LycheeSlicer :</b></h2>

- Gcode de démarrage :

``` yaml
START_PRINT BED_TEMP={bed_temp} EXTRUDER_TEMP={temp}
```

- Gcode de fin :

``` yaml
END_PRINT
```

<h2 style="color:#86be7c"><b>Pour Simplify3D :</b></h2>

- Gcode de démarrage :

``` yaml
START_PRINT BED_TEMP=[platform0_temperature] EXTRUDER_TEMP=[extruder0_temperature]
```

- Gcode de fin :

``` yaml
END_PRINT
```

<h2 style="color:#86be7c"><b>Pour OrcaSlicer :</b></h2>

- Gcode de démarrage :

``` yaml
M140 S0
M104 S0
START_PRINT BED_TEMP=[bed_temperature_initial_layer_single] EXTRUDER_TEMP=[nozzle_temperature_initial_layer]
```

- Gcode de fin :

``` yaml
END_PRINT
```

<br />

Vous pouvez ensuite continuer vers la section :material-arrow-right-box: [Utilisation de la Rétraction Firmware](../configurations/retraction-firmware.md).
