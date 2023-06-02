# Commands follwed in the workshop

## Synthesis


## Floor planning

## Placement


## Custom cell plugin
### layout creation
The custon inverter github repositay: https://github.com/RajuMachupalli/vsdstdcelldesign 

cd openlane

git clone https://github.com/RajuMachupalli/vsdstdcelldesign

cd vsdstdcelldesign

// now we need to copy the  sky13a tech file

cp /pdks/sky130a/lib.tech/magic/sky130a.tech .

// open layout in magic 

magic -T sky13A.tech sky130_inv.mag & 

//magic tool: s for selection and v for center move

//in the tkcon window
extract all
// sky130_inv.ext is generated
// use .ext file to extract spice files, will extarct all parasitic capacitance

ext2spice cthresh 0 rthresh 0

ext2spcie

// sky130_inv.spice is created, edit the .spice file to include nmos, pmos models and transient sweep parameters.
// spice deck file is ready, now we can run spice simulation

ngspice sky130_inv.spice

plot y vs time a //drawing the sweep plot and calculate propoagation delays


### Lef file generaytion and integration
