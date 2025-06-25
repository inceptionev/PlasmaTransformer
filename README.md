# Plasma Transformer

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/20cmGlobe.jpg" width="400">
</p>

## An open-source plasma toroid project by inceptionev (Dr. Bunga)

This project mainly focuses on creating a driver and 3D-printed support structure that allows for safe continuous operation of a plasma toroid.  The objectives are stable operation of a levitating halo of plasma at maximum height above the coil, while providing airflow to keep both the electronics and the globe cool.  The globes are filled with a low-pressure of xenon gas.

The most current work is on the 20cm diameter globe size, but files are also provided for the 13cm globe.

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/3globes.jpg" width="400" align="center">
</p>

KiCAD PCB files are found in the root folder.  If you want to edit the design, the files are in the root folder.  If you just want to make the boards, you need:
- /manufacturing/20250526-PlasmaTransformer-Rev2.zip
- /bom/ibom.html

3d print design files and a dxf for the heatsink hole pattern are found in the 3D Print and CNC folder.  The heatsink holes are all M3 drill/tap.

If you just want to print the files, look here:
- /3D Print and CNC/20cm Globe STL 3D Print Set
- /3D Print and CNC/13cm Globe STL 3D Print Set

## Additional Materials Needed:
- 14 AWG magnet wire
- 12mm or 1/2" polyimide (kapton) tape
- 4x M4*35mm self tapping screws
- 4x M4*12mm self tapping screws
- 4x M3 6x6mm Male/Female threaded standoff
- 4x M3 6mm screws to mount PCB to heatsink
- JST XHP-2 connector and contacts for fan
- The appropriate capacitor values from the list below
- Thermal pad for TO-247 MOSFET (example: SPK4-0.006-00-104)
- M3*20mm screw, washer, and lockwasher for mounting MOSFET

## Assembly instructions:
- Assemble the PCB per the BOM EXCEPT for the MOSFET.  That component will be soldered last.
- Prepare the heatsink
  - Drill and tap the holes in the heatsink.  They are all M3.  A DXF is provided if you wnat to use a CNC.
  - Mount the MOSFET into the heatsink with thermal pad LOOSELY (do not tighten yet)
  - Bend the MOSFET pins up 90 degrees
  - Put the standoffs into the heatsink
- Mount the heatsink to the PCB, threading the MOSFET pins through the holes in the board.  Make sure the MOSFET is loose so it can move into alighment with the board.
- Solder the MOSFET in.
- Add connector to the fan.  Pin 1 is positive.
- Mount the foot and the fan to the bottom with the M4*35mm screws, threading the fan wires through the notch in the bottom.
- Connect the fan to the PCB
- Mount the PCB to the cooling shroud with the M4*12mm screws
- Make the coil
  - Print out the coil form in the folder for the globe size you are using
  - Push approximately 14cm of 14AWG wire through the hole in the coil form, then bend it 90 degrees to follow the coil form AWAY from the notch
  - Wrap 3 turns around the coil form working from the bottom up (this ensures that the higher-voltage RF node is on the bottom of the coil, away from the globe - this helps with levitation)
  - After the 3rd turn when you return to the notch, bend another 90 degree in the wire and make another 14cm tail.
  - Use the notches in the coil form to wrap the coil with polyimide tape to keep the coil.
  - Remove the coil from the form and wrap the coil again where the tail meets the coil
  - Open the coil terminal latches and fit the coil into the assembly with the PCB, making bends to allow for the envelope of the globe.
  - Trim the coil tails if necessary.
  - Burn about 12mm of insulation off the end of the coil tails and clean it up with sandpaper until you can see the shiny copper underneath.
  - Latch the coil into the PCB.

## Known successful values from experimentation:

Supply Voltage:
- 20cm Globe: 24V
- 13cm Globe: 19V

Gate-Drain Cap:
- 20cm Globe: none
- 13cm Globe: 220nF + 220nF

Resonant Cap:
- 20cm Globe: 2x 24pF 564RC0GAJ602EJ240J
- 13cm Globe: 5x 12pF CGP1C120KNSDAAWL25

Gate-Source Cap:
- 20cm Globe: 2.7nF + 1.8nF + 1.8nF
- 13cm Globe: 2.7nF
