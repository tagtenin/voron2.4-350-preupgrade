# Print-start sequence

`PRINT_START` performs the following high-level sequence:

1. Clear old mesh and home.
2. Heat the bed and perform a timed soak.
3. Re-home Z after thermal expansion.
4. Run QGL and re-home Z.
5. Bring the nozzle to 150 C.
6. Generate a fresh full-bed Cartographer mesh.
7. Run Survey Touch.
8. Heat the nozzle to the slicer target.
9. Purge and begin printing.

This intentionally favours repeatability over minimizing start time.
