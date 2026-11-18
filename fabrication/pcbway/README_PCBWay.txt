AI MotoLogger - IMU test board v0.1
===================================

Small test board that carries four inertial sensors side by side on one rigid PCB, so that they all see the same
shocks and vibration on a motocross bike: TDK ICM-45686, ST LSM6DSV320X, ST ASM330LHH and ADI ADXL375.

Files
-----
prueba_imu_gerbers.zip            Gerber (RS-274X/X2) + Excellon drill (PTH and NPTH separate) + job file
gerbers/                          same files unzipped, plus drill maps (PDF)
prueba_imu_BOM_PCBWay.csv         bill of materials with manufacturer part numbers
prueba_imu_centroid_PCBWay.csv    pick and place, mm, top side only (same origin as the Gerber files)

PCB
---
Size              54.0 x 50.0 mm, rounded corners (r = 1 mm)
Layers            4: Top signals + GND pour / In1 GND plane / In2 +3V3 plane / Bottom signals + GND pour
Thickness         1.6 mm FR-4, standard copper (1 oz outer, 0.5 oz inner), no impedance control
Tracks            0.20 mm signals, 0.40 mm power
Clearance         0.15 mm minimum (the LGA pads themselves are 0.15 mm apart)
Vias              0.6 mm pad / 0.3 mm drill, tented
Holes             4 x 3.2 mm NPTH (M3) + 2 x 3.0 mm NPTH, 15 x PTH (pin header)
Finish            ENIG preferred: three LGA-14 packages with 0.5 mm pitch need flat pads
Mask / silk       any colour

Stencil
-------
Top side only, 0.12 mm stainless steel.
The paste apertures of the four sensors (U2-U5) are already reduced in the paste layer, as ST TN0018 §3.3 asks
(70-90 % of the pad area). All other pads are 100 %.

Assembly (only if PCBA is included)
-----------------------------------
- 32 SMD parts, all on the top side. J1 (1x15 pin header) is NOT populated. TP1-TP3 are bare test pads.
- U5 (ADXL375) is rotated 270 degrees on purpose, so that the X and Y axes of the four sensors are aligned.
- U4 (ASM330LHH) and U5 (ADXL375) may be supplied by the customer.
- MEMS handling (ST TN0018, also valid for the TDK and ADI parts):
    * no ultrasonic cleaning;
    * avoid mechanical shock: do not drop the parts or the boards;
    * reflow to IPC/JEDEC J-STD-020, with a ramp-down slope not steeper than -3 °C/s;
    * no solder on the sides of the LGA packages; no underfill, no conformal coating;
    * moisture sensitivity level as printed on each part's packing label.
