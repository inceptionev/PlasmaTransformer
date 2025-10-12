# Plasma Transformer

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/20cmGlobe.jpg" width="400">
</p>

## An open-source plasma toroid project by inceptionev (Dr. Bunga)

This project mainly focuses on creating a driver and 3D-printed support structure that allows for safe continuous operation of a plasma toroid.  The objectives are stable operation of a levitating halo of plasma at maximum height above the coil and protection against touching energized components, while providing airflow to keep both the electronics and the globe cool.  The globes are filled with a low-pressure of xenon gas.

Special thanks to:  
Sky-guided, whose inductive oscillation indicator design is used in this project.  
@ltwin8, whose RF node parasitic auto-igniter design is used in this project and was detailed in https://github.com/inceptionev/PlasmaTransformer/issues/1  

Native design files and manufacturing files in gerber and stl format are provided for the 20cm and 13cm globe sizes.

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/3globes.jpg" width="400" align="center">
</p>

KiCAD PCB files are found in the /Plasma Transformer PCB folder.  If you want to edit the design, the files are in the folder.  If you just want to make the boards, you need:
- Plasma Transformer PCB/manufacturing/[the zip file with the latest rev]
- Plasma Transformer/bom/[the bom file matching that rev]

3d print design files and a dxf for the heatsink hole pattern are found in the 3D Print and CNC folder.  The heatsink holes are all M3 drill/tap.

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/pcbRev5.jpg" width="400">
</p>

If you just want to print the files, look here:
- /3D Print and CNC/20cm Globe STL 3D Print Set
- /3D Print and CNC/13cm Globe STL 3D Print Set

## Additional Materials Needed:
- 12 AWG magnet wire (2mm dia)
- 12mm or 1/2" polyimide (kapton) tape
- 4x M4*35mm self tapping screws
- 4x M4*12mm self tapping screws
- 4x M3 6x6mm Male/Female threaded standoff
- 4x M3 6mm screws to mount PCB to heatsink
- JST XHP-2 connector and contacts for fan
- The appropriate capacitor values from the list below
- Thermal pad for TO-247 MOSFET (example: SPK4-0.006-00-104)
- M3*20mm screw, washer, and lockwasher for mounting MOSFET
- 4mm OD x 2.5mm ID PTFE tube (commonly sold as Bowden tube for 1.75mm filament 3D printers)

## Assembly instructions:
- Assemble the PCB per the BOM EXCEPT for the MOSFET.  That component will be soldered last.
- Prepare the heatsink
  - Drill and tap the holes in the heatsink.  They are all M3.  A DXF is provided if you wnat to use a CNC.
  - Mount the MOSFET into the heatsink with thermal pad LOOSELY (do not tighten yet)
  - Bend the MOSFET pins up 90 degrees
  - Put the standoffs into the heatsink
- Mount the heatsink to the PCB, threading the MOSFET pins through the holes in the board.  Make sure the MOSFET is loose so it can move into alighment with the board.
- Now tighten the screw mounting the MOSFET to the heatsink.
- Solder the MOSFET in.
- Add connector to the fan.  Pin 1 is positive.
- Mount the foot and the fan to the bottom with the M4*35mm screws, threading the fan wires through the notch in the bottom.
- Connect the fan to the PCB
- Mount the PCB to the cooling shroud with the M4*12mm screws
- Make the coil
  - Print out the coil form in the folder for the globe size you are using.
  - Push a length of 12AWG magnet wire in a length of insulating PTFE tube.  It helps if the tube and the wire are both straight.  Taping them to the edge of a table will accomplish this.
    - For the 13cm globe, push 171.6cm of wire into 151.6cm of PTFE tube.  Leave 10cm of wire sticking out at both ends.
	- For the 20cm globe, push 203cm of wire into 175cm of of PTFE tube.  Leave 14cm of wire sticking out at both ends.
  - First wrap the wire and insulator around an object slightly smaller than the coil form.  This will make wrapping on the coil form easier.
  - Wrap the slightly-smaller coil of wire and insulator onto the coil form.  Start at the lip, and work up from there in a clockwise direction with the lip facing away from you.  This ensures that the bottom coil connects to the RF Node (the right block on the PCB).  This is the higher voltage terminal, and having it on the bottom coil helps with levitation of the plasma.
    - 13cm Globe: you should get 4 coils, minus the 9mm gap where the ends meet.
	- 20cm Globe: you should get 3 coils, minus the 9mm gap where the ends meet.
  - Use the slots in the coil form to tape up the coil so it holds its shape.  Polyimide (Kapton) tape is recommended.
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
- 13cm Globe: none

Resonant Cap:
- 20cm Globe: 3x 24pF 564RC0GAJ602EJ240J
- 13cm Globe: 3x 12pF CGP1C120KNSDAAWL25

Gate-Source Cap:
- 20cm Globe: 2.7nF + 3.6nF + 1.8nF + 1.8nF
- 13cm Globe: 2.7nF
