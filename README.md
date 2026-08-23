# Voron 2.4 350 pre-upgrade configuration

Quality-first Klipper configuration for the stock-ish Voron 2.4 before the Monolith upgrade.

## Hardware represented by `printer.cfg`

- Voron 2.4 350
- BTT Octopus Pro
- BTT EBB36 v1.2 over CAN
- Stealthburner toolhead
- Formbot all-metal V6-style hotend
- Cartographer V3 / Survey Touch

Printer-specific configuration has been consolidated into `printer.cfg`. Vendor/client-managed configuration such as Mainsail and Obico remains included externally.

## OrcaSlicer machine start/end G-code

Start G-code:

```gcode
PRINT_START BED=[bed_temperature_initial_layer_single] EXTRUDER=[nozzle_temperature_initial_layer]
```

You can override the automatic timed heat soak by adding `SOAK=<minutes>`, for example:

```gcode
PRINT_START BED=[bed_temperature_initial_layer_single] EXTRUDER=[nozzle_temperature_initial_layer] SOAK=15
```

End G-code:

```gcode
PRINT_END
```

Default heat-soak times are 15 minutes for bed targets >=105 C, 10 minutes for >=95 C, and 5 minutes below 95 C.

## Before the first print

1. Run `FIRMWARE_RESTART` and confirm Klipper loads the configuration without errors.
2. Verify X/Y homing direction and all four Z motors before allowing the nozzle close to the bed.
3. Verify the new `20,20` to `330,330` bed-mesh area is mechanically reachable with the current toolhead and Cartographer mount.
4. Clean the nozzle and bed, then run `CARTOGRAPHER_TOUCH_ACCURACY` several times. If Touch is not repeatable, fix that before adjusting first-layer Z.
5. Re-run Cartographer Touch calibration if necessary. The existing `scanner_touch_z_offset: 0.1` is intentionally retained instead of masking a repeatability problem with a guessed offset.
6. Input shaping is intentionally disabled until resonance measurements / Shake&Tune are re-run successfully.

## Temperature note

The hotend `max_temp` remains at 270 C. Do not raise it until the exact thermistor and heater ratings of the current Formbot V6-style hotend are verified.
