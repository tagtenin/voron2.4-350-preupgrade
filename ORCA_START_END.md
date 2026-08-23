# OrcaSlicer start/end G-code

Use the following as the machine start G-code:

```gcode
PRINT_START BED=[bed_temperature_initial_layer_single] EXTRUDER=[nozzle_temperature_initial_layer]
```

Optional explicit heat soak:

```gcode
PRINT_START BED=[bed_temperature_initial_layer_single] EXTRUDER=[nozzle_temperature_initial_layer] SOAK=15
```

Use the following as machine end G-code:

```gcode
PRINT_END
```

The macro turns the bed off at print end so ASA / engineering-material parts can cool while remaining attached to the build plate. If a future back-to-back production workflow makes a warm-bed mode useful, add that as an explicit option rather than making it the default.
