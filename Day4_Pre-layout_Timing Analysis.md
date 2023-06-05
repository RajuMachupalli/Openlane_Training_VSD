# Pre-layout Timing Analaysis
As of now, we learned about openlane setup, synthesis, floorplan and next step is routing. in Day 3 labs, we used the MAGIC tool for layout creation, and SPICE tool for characterization. Today we will use the work on how to use the designed inverter cell in the picorv32a design.

## Lef file extraction
For the placement and routing (PnR) tool, only power, groung, input and outputs are needed along with the size. The size should be in multiples of base pitch. Width should be in the odd multiples of the X-pitch. Input and output ports should be in the intersection of a and y tracks. Define the pins and its class for LEF file generation.
LEF file is created using command lef write in tkcon window. The generated lef file is shown in follwing figure.

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/93512fcc-bff7-454a-8e0d-4d0d767ea1bf)

## Plugin the inv cell into picorv32a design
Now, we can plugin the customized inverter cell into picorv32a design and run routing.
1. copy the lef file into picorv32a/src folder.
2. copy .lib/*.lib files into picorv32a/src folder
3. edit config.tcl at /picorv32a/ 
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/acf873d7-0df5-413b-9522-3426f355d606)


set lefs  [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

and run the synthesis, the synthesis was successful and inv cell is added to the design as shown below.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/d6d0917f-4332-4588-bd77-20259f192d90)


4. dvcmasdb
