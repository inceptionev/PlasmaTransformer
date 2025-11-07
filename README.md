# Plasma Transformer

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/20cmGlobe.jpg" width="400">
</p>

## An open-source plasma toroid project by inceptionev (Dr. Bunga)

This project mainly focuses on creating a driver and 3D-printed support structure that allows for safe continuous operation of a plasma toroid.  The objectives are stable operation of a levitating halo of plasma at maximum height above the coil and protection against touching energized components, while providing airflow to keep both the electronics and the globe cool.  The globes are filled with a low-pressure of xenon gas.

### Key Features of this project:
- Plasma Driver PCB with experimentation-friendly features:
  - Wide input power range from 12-60V for easy power control.  Onboard 12V supply for stable fan and gate drive.
  - High-voltage auto-igniter strikes the plasma whenever plasma is not present, but also does not load the driver when plasma is live.  This helps prevent damage from runaway unloaded oscillation.  Designed in collaboration with @ltwin0.
  - Oscillation detector illuminates to show when the driver is in oscillation, whether or not plasma is present.  Based on a design from Sky-guided.
  - Socketed coil and tank capacitor connectors for easy tuning.
  - Dedicated on-board oscilloscope probes on the MOSFET gate and drain nets for Class-E tuning.  Connect an SMA cable directly from the board to a terminator and the oscilloscope.
  - Selectable Gate-Source cap via jumper headers to tune AC gate drive strenth.
  - Separate power switch and DC Gate Bias control.  Turn it off and on without changing the DC gate bias level.
- 3D printed cooling shroud:
  - Provides directed airflow for cooling both the electronics and the globe for continuous use.
  - Supports the fan, board, coil, and globe with ideal spacing for achieving a levitating plasma halo.
  - Provides attachments for rubber bands to hold the globe in place for environments where the device may be in motion, or to attach a shade to make the plasma more visible in outdoor installations.
  - Includes a cover and coil ring that keeps curious fingers away from the hazardous high-voltage parts. (But caution is always advised around high voltage and RF)
- 3D-printed assembly aids:
  - Coil forms for ease of making the plasma coil.

Special thanks to:  
Sky-guided, whose inductive oscillation indicator design is used in this project.  
@ltwin8, whose RF node parasitic auto-igniter design is used in this project and was detailed in https://github.com/inceptionev/PlasmaTransformer/issues/1  

Native design files and manufacturing files in gerber and stl format are provided for the 20cm and 13cm globe sizes.

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/3globes.jpg" width="400" align="center">
</p>

KiCAD PCB files are found in the /Plasma Transformer PCB folder.  If you want to edit the design, the files are in the folder.  If you just want to make the boards, you need:
- Plasma Transformer PCB/manufacturing/[the zip file with the latest rev]
- Plasma Transformer PCB/bom/[the bom file matching that rev]

Rev 5 PCB specific note:
The holes for the capacitor sockets are too large, so instead of being press-fit, they will need to be soldered in.  I recommend using a piece of paper tape to hold them in place on the top side, then soldering them on the bottom side.  Or you can skip the sockets and solder in the capacitors directly.


3d print design files and a dxf for the heatsink hole pattern are found in the 3D Print and CNC folder.  The heatsink holes are all M3 drill/tap.

If you are doing turnkey PCBA assembly, you probably want to DNP the fan, heatsink, and MOSFET from the BOM, as you will assemble these later.

<p align="center">
  <img src="https://github.com/inceptionev/PlasmaTransformer/blob/master/images/pcbRev5.png" width="400">
</p>

If you just want to print the files, look here:
- /3D Print and CNC/20cm Globe STL 3D Print Set
- /3D Print and CNC/13cm Globe STL 3D Print Set

## Additional Materials Needed:
- 12 AWG magnet wire (2mm dia)
- 12mm or 1/2" polyimide (kapton) tape
- 4x M4*30mm self tapping screws
- 4x M4*8mm self tapping screws
- 4x M3 6x6mm Male/Female threaded standoff
- 4x M3 6mm screws to mount PCB to heatsink
- M3 washers and lockwashers
- JST XHP-2 connector and contacts for fan
- The appropriate capacitor values from the list below
- Thermal pad for TO-247 MOSFET (example: SPK4-0.006-00-104)
- M3*20mm screw, washer, and lockwasher for mounting MOSFET
- 4mm OD x 2.5mm ID PTFE tube (commonly sold as Bowden tube for 1.75mm filament 3D printers)

## Assembly instructions:
- I recommend 3D-printing the coil forms and the spacer ring first, then the cooling shroud, cover, and foot.  You may also want to print a smaller coil form for pre-winding in the first batch, see coil instructions below.
- The main cooling shroud may take 20+ hrs to print, so you can build the heatsink, coil and PCB while it is printing.
- Prepare the heatsink
  - Drill and tap the holes in the heatsink.  They are all M3.  A DXF is provided if you wnat to use a CNC.
  - Mount the MOSFET into the heatsink with thermal pad LOOSELY (do not tighten yet)
  - Bend the MOSFET pins up 90 degrees
  - Install the standoffs into the heatsink
- Assemble the PCB per the BOM EXCEPT for the MOSFET.  That component will be soldered last.
- Mount the PCB to the heatsink with 4x M3x6mm screws, washers, and lockwashers, threading the MOSFET pins through the holes in the board.  Make sure the MOSFET is loose so it can move into alighment with the board.
- Tighten the screws mounting the PCB to the heatsink first.
- Then tighten the mounting screw of the MOSFET to the heatsink.
- Solder the MOSFET in.
- Add connector to the fan.  Pin 1 is positive.
- Make the coil
  - Print out the coil form in the folder for the globe size you are using.
  - Push a length of 12AWG magnet wire in a length of insulating PTFE tube.  It helps if the tube and the wire are both straight.  Taping them to the edge of a table will accomplish this.
    - For the 13cm globe, push 171.6cm of wire into 151.6cm of PTFE tube.  Leave 10cm of wire sticking out at both ends.
	- For the 20cm globe, push 203cm of wire into 175cm of of PTFE tube.  Leave 14cm of wire sticking out at both ends.
  - First wrap the wire and insulator around an object slightly smaller than the coil form.  This will make wrapping on the coil form easier.  You can use the 13cm coil form as the pre-wind form for the 20cm coil. An stl file for an 80mm coil form is also provided to act as the pre-wind for the 13cm coil.
  - Wrap the slightly-smaller coil of wire and insulator onto the coil form.  Start at the lip, and work up from there in a clockwise direction with the lip facing away from you.  This ensures that the bottom coil connects to the RF Node (the right block on the PCB).  This is the higher voltage terminal, and having it on the bottom coil helps with levitation of the plasma.
    - 13cm Globe: you should get 4 coils, minus the 9mm gap where the ends meet.
	- 20cm Globe: you should get 3 coils, minus the 9mm gap where the ends meet.
  - Use the slots in the coil form to tape up the coil so it holds its shape.  Polyimide (Kapton) tape is recommended.
  - Remove the coil from the form and wrap the coil again where the tail meets the coil
  - Open the coil terminal latches on the PCB and fit the coil into the assembly with the PCB, making bends to allow for the envelope of the globe.  Make an 'S' curve at the bottom of the coil wires where they exit the PCB blocks, to allow for adjusting the height.
  - Trim the coil tails if necessary.
  - Burn about 12mm of insulation off the end of the coil tails and clean it up with sandpaper until you can see the shiny copper underneath.  A lighter works well for this.
  - Install the coil spacer ring into the top of the coil, opposite of the direction where the wire tails go.
- Mount the foot and the fan to the bottom with the M4*30mm screws, threading the fan wires through the notch in the bottom.  
- Connect the fan to the PCB.  On the 20mm cooling shroud, a slot is provided in the wall next to the PCB to hold the fan connector temporarily for easy connecting and disconnecting.
- Mount the PCB to the cooling shroud with the M4*8mm screws
- Latch the coil into the PCB.
- Screw in 5x M4x8mm screws into the bosses around the circumference of the cooling shroud. This can be used for shrouds or rubber bands to secure the globe.
- Optionally install the cover into the cooling shroud.

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

Measured Air Core Inductance of Globe Coils (no globe or plasma present):
- 13cm Globe, 4 turns 122mm x 16mm long: 3.3uH
- 20cm Globe, 3 turns 187mm dia x 12mm long: 3.6uH


## Tips and Tricks for Experimenting with Plasma Toroids:
- The goal of feedback tuning is to minimize the source-drain voltage across the MOSFET during the points of switching, otherwise it will get hot quickly.
- Also be mindful of the voltage rating on the cap between the plasma globe coil and the gate.  This cap will see 1000V+ when the coil is unloaded (when there is no plasma).
- Also be careful of anything in that node.  That means anything between the gate-coil capacitor and the coil, including the bottom turns of the coil.  This is the HF node, aka RF node, where the highest amplitude of voltage oscillation is seen.  It will burn you if you touch it, sometimes even touching insulated portions.  The burn is nearly painless at first, and then painful later.
- The MOSFET and the coil-gate cap are the two most common components to break in this circuit.
- Haloplasma is a good source for the xenon-filled plasma globes.
