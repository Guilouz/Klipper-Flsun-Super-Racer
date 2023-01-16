---
hide:
  - toc
---

# Gcode de Début / Fin

Il est nécessaire de modifier votre Gcode de Début et de Fin dans votre Slicer car ils sont désormais intégrés dans les macros.

Cela a pour avantage de pouvoir imprimer un même modèle avec des Gcodes de Début et de Fin différents.


## Pour Cura :

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

## Pour PrusaSlicer / SuperSlicer :

- Gcode de démarrage :

``` yaml
START_PRINT BED_TEMP=[first_layer_bed_temperature] EXTRUDER_TEMP=[first_layer_temperature]
M104 S[first_layer_temperature]
M190 S[first_layer_bed_temperature]
```

- Gcode de fin :

``` yaml
END_PRINT
```

## Pour LycheeSlicer :

- Gcode de démarrage :

``` yaml
START_PRINT BED_TEMP={bed_temp} EXTRUDER_TEMP={temp}
```

- Gcode de fin :

``` yaml
END_PRINT
```

## Pour Simplify3D :

- Gcode de démarrage :

``` yaml
START_PRINT BED_TEMP=[platform0_temperature] EXTRUDER_TEMP=[extruder0_temperature]
```

- Gcode de fin :

``` yaml
END_PRINT
```

<br />

Vous pouvez ensuite continuer vers la section :material-arrow-right-box: [Utilisation de la Rétraction Firmware](../configurations/retraction-firmware.md).
