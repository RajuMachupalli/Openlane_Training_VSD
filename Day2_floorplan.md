# To Do
1. get the number of gates or standard cells and its dimiensins from synthesis.
2. difference between core and die?

# Day2 Floor plan session

## step 1: defining core size
The core size mainly depends on the logic gates presents and its size
Utlization factor = (area occupaid by netlist)/(core area)
Aspect ratio = Height/Width
Pre-placed cells: The design has many blocks. Each block is made such that its has minimum io pins. each block can call IP or cell. These blocks are position is fixed on the core, called floor planning.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/4cac7f4a-5496-4353-bdef-742a54f2d785)

To avoid the voltage drop (cross counpling?) due to resistance in metal, decoupling capacitance is added around the pre-placed cells or blocks.
Power planning: when large size bus or connection between modules changes state from one to zero, large amount of current is flows to ground. At certain point, the ground might show at higher voltage then noise margin causing undfined state instead of ground state (ground bump?). simillary when changing from zero to one huge voltage drop may cause droup in vdd 
