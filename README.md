# Design steps
1. Logic synthesis: RTL to gate level netlist
2. Floor planning: Define the core and die size, IO pads and power trails. Results core utilization. 
3. Placement: Placing gates with less delay or wire length
4. Clock tree synthesis (CTS): Route the clock tree with minimum clock skew across the core.
5. Routing: Place and route the netlist.
6. Static timimg analysis: Post-CTS timining analysis.


# Openlane_test
As a part of Openlane training, virtual disk with all the required tools installed is provided. Some design example are provided as shown in the below figure 
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/4397d506-142e-4e1c-ad9c-0a81774e4cf4)


![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/8775dc0e-1b3f-4b30-a097-3ef24af54a60)
/n
example project picrorv32a directory has above files

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/72e6cb81-8bf7-41dd-852a-ac5ead633c2d)

how does the config.tcl file looks

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/1f309fbb-a57f-47e6-8af2-4e5453e2df4d)

how the existing file looks, specially clock period

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/9660db28-d88c-41cf-b952-2195d8796f66)

after preparation command

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/d34412b6-68b4-4065-a1da-73dba5ab2d51)

updated picorv32a directory after preparation command, additiona;l run folder is created

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/0f6db329-beb5-439d-b556-a1a83c8fe759)
the run folder

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/dbd3ce8e-f5f2-4bd0-91d2-e2c25ad8a771)

config.tcl file created in the run folder. can observe clock period set similar to one existing 24.73

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/58c726e2-15e0-4396-a00f-2e4fd2d848bf)

synthesis results: part of it to show dflipflop ratio
