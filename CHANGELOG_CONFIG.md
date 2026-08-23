# Configuration overhaul summary

This branch is a pre-Monolith cleanup focused on reliable ASA and engineering-material printing rather than maximum speed.

Key changes:

- Consolidated printer-specific Klipper settings into `printer.cfg`.
- Rebuilt OrcaSlicer `PRINT_START` and `PRINT_END` macros.
- Added timed heat soak before precision levelling.
- Fresh QGL, Z home, full-bed Cartographer mesh and Survey Touch before every print.
- Expanded Cartographer mesh coverage to nearly the full 350 mm bed.
- Removed untrusted input-shaper values pending new measurements.
- Set conservative 250 mm/s / 3000 mm/s² machine ceilings.
- Preserved known wiring, MCU IDs, axis geometry and heater settings.
- Preserved the 270 C hotend safety ceiling pending verification of the current V6 heater/thermistor ratings.
- Added first-run validation and Cartographer troubleshooting notes.
