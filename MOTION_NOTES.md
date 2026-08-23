# Motion baseline

The branch sets conservative machine-level ceilings of:

- `max_velocity: 250`
- `max_accel: 3000`
- `square_corner_velocity: 5.0`

These are ceilings, not recommended slicer print speeds. OrcaSlicer should continue to use lower feature-specific speeds/accelerations where surface quality and layer adhesion benefit.

Input shaping is intentionally not configured until new resonance measurements are available.
