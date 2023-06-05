# Pre-layout Timing Analaysis
As of now, we learned about openlane setup, synthesis, floorplan and next step is routing. in Day 3 labs, we used the MAGIC tool for layout creation, and SPICE tool for characterization. Today we will use the work on how to use the designed inverter cell in the picorv32a design.

## Lef file extraction
For the placement and routing (PnR) tool, only power, groung, input and outputs are needed along with the size. The size should be in multiples of base pitch. Width should be in the odd multiples of the X-pitch. Input and output ports should be in the intersection of a and y tracks. Define the pins and its class for LEF file generation.
LEF file is created using command lef write in tkcon window. The generated lef file is shown in follwing figure.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/93512fcc-bff7-454a-8e0d-4d0d767ea1bf)

## Plugin the inv cell into picorv32a design
