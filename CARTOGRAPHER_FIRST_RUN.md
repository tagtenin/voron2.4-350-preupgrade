# Cartographer first-run checklist

Before relying on Survey Touch for a large print:

1. Clean the nozzle and build surface.
2. Verify the Cartographer mount is rigid and approximately 2.6-3.0 mm above the nozzle tip if using Survey Touch.
3. Home safely.
4. Run:

```gcode
CARTOGRAPHER_TOUCH_ACCURACY
```

Repeat it a few times and look for stable, tightly grouped results.

If results are inconsistent, check toolhead rigidity, loose hardware, Z motion, belt tension, wiring and nozzle cleanliness before changing Z offsets.

The existing `scanner_touch_z_offset: 0.1` is retained in this branch. The reported nozzle-too-close behaviour should be diagnosed through Touch repeatability/calibration first rather than hidden by a guessed compensation value.

The current installed configuration uses the older scanner-style Cartographer plugin setup. A later dedicated migration can adopt the newest Cartographer configuration and `CARTOGRAPHER_TOUCH_HOME` workflow once this baseline is working reliably.
