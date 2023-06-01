# To Do
1. get the number of gates or standard cells and its dimiensins from synthesis.
2. difference between core and die?
3. what are .lef, .def, and .tech file?
4. Euler's path and stick digarms?

# Day2 Floor plan session

## step 1: defining core size
The core size mainly depends on the logic gates presents and its size
Utlization factor = (area occupaid by netlist)/(core area)
Aspect ratio = Height/Width
Pre-placed cells: The design has many blocks. Each block is made such that its has minimum io pins. each block can call IP or cell. These blocks are position is fixed on the core, called floor planning.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/4cac7f4a-5496-4353-bdef-742a54f2d785)

To avoid the voltage drop (cross counpling?) due to resistance in metal, decoupling capacitance is added around the pre-placed cells or blocks.
Power planning: when large size bus or connection between modules changes state from one to zero, large amount of current is flows to ground. At certain point, the ground might show at higher voltage then noise margin causing undfined state instead of ground state (ground bump?). Simillarly when changing from zero to one huge voltage drop may cause droup in vdd, droping below the noise level may cause undefined state
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/98bd545c-1c63-46ca-b069-8b00d424d168)
to avaoid this ptoblem, power lines/ mesh are planned such that required cuttents are drawn from nearest power souce to pull or pull down the logic as frequently as possible.
steps: 1. Utilization factor
        2. Pre-placed cells: groupig the closely coupled gates to make minimum ios.
        3. Decoupling capacitor: Capacitance around the blocks to supply the current at logic switching (??)
        4. Power planning : Vdd and Vss lines
        5. Pin placement : IO pins placement, pin pads
        6. Logical cell placement blockage: to block floor planning to use are around pin pads (between core and die)
        
Initially I could not find floorplan.tcl in configuration folder so I run run_floorplan command and saw floorplan.tcl file.
I also could not see few parameters set at config.tcl file in design directory so i modified as follows:
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/a41de427-7c25-47bb-bdc7-1814f8e021cb)

floor plan log file shows as below, but expected lot of details as shown in videos.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/87cb8c03-e2ea-4b42-b6b4-38301166a0ea)

To see the acutal floorplan, we need to use magic tools. magic tool needs tech file from sky130A pdk, and lef file (merged lef file from tech lef and cell lef) present in tmp folder, and then def file (results/floorplan folder).
# What are these .def, .lef and .tech files??
## Placement
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/abf20ad4-4487-4d30-91ed-f5f294103fd1)

in the placement, do we place cell like the above images manually? or openlane will take care of it?

steps:
        1. physical library
        2. placement
        3. Optimized placement
        
 repeaters are dummy buffers for signal integrity.
 
 The placementt has two stages: global placement (coarse placement) and detail placement. legalization happens in detail placement. The aim of global placement is to reduce the wire length. openlane follows half parameters wire length.
 
 ![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/7bae06ee-a00c-4a7a-babf-714e95a0438d)

running placement does not giving the right results, no iterations happen and it looks completely different than lecture slide.

# Cell design flow
Cell design flow has three steps:
1. inputs
2. design steps
3. outputs
inputs: process design kits (pdks), DRS and LVS rules, spice model, library and user defined specs. Tech files have lamda based design rules. spice model parameters are equations from spice model for threshold, linear region, saturation voltage. user defined specs are: voltage, cell height, fan-in and fan-out strength, contact metal, pin location.

Design steps: circuit design, layout, and characterization. 
In circuit design, define the different parameters like threshold and get width and hights of nmos and pmos (Wp and Lp, Wn and Ln) similar to follwing image. Circuit design produce CDL (circuit discription langiage). 
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/88297567-9a53-42b8-8111-3092385d611e)

In layout design: Draw the circuit and get pmos, nmos graphs. Use the Euler's path and stick digarm to get the layout. MAgic tool is an opensource toll to draw layout. The layout produce the outputs: GDSII - layout schematic, Lef - width and height of cell, extracted spice netlisf (.cir) - information about parasetics, resistance and capacitance of every element in layout.

In characterization: we have inputs from layout, circuit, spice extracted model, nmos and pmos parameters. First step is to read the model files (nmos and pmos from foundary). Second read the extracted spice netlist, third is to  recognise the circuit behaviour and fourth step is to simulation setup with power and input sources and output capacitances. Generate dc and transcient behaviour. Feed all these to characterization software called ## GUNA. GUNA gives timing, power and noise characerization.
