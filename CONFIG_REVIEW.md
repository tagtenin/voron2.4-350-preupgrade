# Configuration review notes

This branch intentionally prioritizes print quality and predictable behaviour over speed.

## Main changes

- Consolidated printer-specific Klipper configuration into `printer.cfg`.
- Removed the previous unverified input-shaper values.
- Reduced machine limits from 300 mm/s / 3600 mm/s² to 250 mm/s / 3000 mm/s² as conservative quality-first ceilings.
- Rebuilt `PRINT_START` and `PRINT_END` for OrcaSlicer.
- Added timed heat soaking based on bed target temperature, with an optional explicit `SOAK` override.
- Kept a fresh full-bed Cartographer scan for every print.
- Expanded the mesh from the old partial-bed area to `20,20` through `330,330`.
- Kept the existing Survey Touch Z-offset rather than hiding the reported low-Z issue with a guessed compensation value.
- Removed calls to undefined `STATUS_*` / `SET_DISPLAY_TEXT` helper macros.
- Normalized the part-cooling fan PWM cycle time to 0.01 s.

## Cartographer note

The installed configuration uses the older `[scanner]`-style Cartographer setup and a saved firmware/model from Cartographer firmware 5.0.0. Current Cartographer documentation has evolved and now recommends scan homing for normal homing plus a final `CARTOGRAPHER_TOUCH_HOME` after gantry levelling.

This branch deliberately does **not** combine a Cartographer plugin migration with the printer config cleanup. It retains the known-working `CARTOGRAPHER_TOUCH` workflow and recommends measuring Touch repeatability first. Once the current config is validated, Cartographer can be upgraded/migrated separately.

## First-run safety checks

Do not start a print immediately after merging. First:

1. `FIRMWARE_RESTART` and verify that Klipper loads cleanly.
2. Home X and Y and verify directions/endstops.
3. Verify Z motion and Cartographer homing at a safe height.
4. Confirm the toolhead can physically reach the new mesh boundaries.
5. Run `CARTOGRAPHER_TOUCH_ACCURACY` repeatedly with a clean nozzle and bed.
6. If Touch is inconsistent, recalibrate/fix the mechanical issue before tuning `scanner_touch_z_offset`.
7. Run a small first-layer test before a large ASA or PC-PBT-CF print.
8. Re-run resonance testing / Shake&Tune before adding input-shaper values back.
