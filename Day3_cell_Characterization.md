# Library Cell design and characterization
## questions to learn
1. why does pmos width greater than nmos width? how does width affectes current flow? hint: hise and fal delays and switching threshold, also current or power drawn.
2. draw backs of nmos and pmos technology amd how cmos able to slove it?
3. noise margins in nmos and pmos technology?

## Cell design
Its important to consider width and height of cmos and nmos for layout creation. The parameters play a role in inverter characteristics and power consumption. The below images should give some hints on device characters.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/2cb4ef9c-bdcc-48b0-a712-f9ec8f885823)

Instead of designing inverter layout, we coping the git repo https://github.com/RajuMachupalli/vsdstdcelldesign use the magic tool and sky130a tech file to open the layout.

## 16-mask CMOS process

1. Substract: p-type substract
2. Creating active regions for transistors: MASK1
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/b7746d88-204c-4a93-8d1c-81883f45418b)

3. N-well and P-well creation:
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/dd7289fa-6818-4973-bec3-3c5c37183a11)

4. Formation of gate
gate formation define the threshold voltage as below screen shot
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/7e3b74a1-c04b-4e62-a202-98d047463cd2)
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/e982c73e-0b55-4619-aed3-dffb038bc27c)



5. Lightly dopped darin formation:
the soure and drains are dopped in P+NP-, N+PN- to eliminate #Hotelectron effet and #short channel effect.



6. bd
