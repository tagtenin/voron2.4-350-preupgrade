# Validation sequence

Recommended validation after switching to this branch:

```text
FIRMWARE_RESTART
G28 X Y
G28 Z
QUAD_GANTRY_LEVEL
G28 Z
CARTOGRAPHER_TOUCH_ACCURACY
BED_MESH_CALIBRATE
```

Stop immediately if any axis direction, homing position, probe movement or mesh boundary is not as expected.

After the mechanical/probe checks, run a small first-layer test with the intended build surface and filament before attempting large parts.
