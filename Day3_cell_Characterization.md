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
Drive-in-diffusion to penetrate implants into substrate.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/dd7289fa-6818-4973-bec3-3c5c37183a11)

4. Formation of gate
gate formation define the threshold voltage as below screen shot
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/7e3b74a1-c04b-4e62-a202-98d047463cd2)
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/e982c73e-0b55-4619-aed3-dffb038bc27c)



5. Lightly dopped darin formation:
the soure and drains are dopped in P+NP-, N+PN- to eliminate #Hotelectron effet and #short channel effect.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/add100ff-dd34-49f7-9834-aee48a3e9f44)


6. Source darin formation:
anisotrophic etch for side ball spacers
Thin screen oxide to avoid channeling effect. In channeling effect, implat ions may go deeper into substrate to avoid it direction is randomized by screen oxide.
Anealing is a process similar to drive-in for penetarting implants further into well.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/d9a3869a-fdef-48e6-8aa6-cbce3e08af98)


7. Contacts and interconnects:
etch thin screen oxide in HF solution
deposit titanium on wafer using sputterion. titanium has low resistance. In sputtering, Argon gas are hit on Ti surface and deposited on wafer.
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/ab8f04ff-b095-43e1-b33a-107142f4df03)


8. Higher level metal formation:
Non-planer surce is not good for metals as it forms edges. So deposit 1um of SiO2 dopped with phosphoros or boron. Use CMP technique to planarize the surface
Tungustan is used as contacts, TiN is used as adhesive layer. mask 14 and higher is used for higher level contacts.

![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/4f32af42-e6de-4019-be48-0d8d5ba12786)

## Tech files lab
The generated .spice file has different data as shown below
![image](https://github.com/RajuMachupalli/openlane_test/assets/52839597/dc87f6f2-6251-40fc-97fe-2c42aa8cfe6c)

I changed pmos and nmos to pshort and nshort_model.0 as shown in libs/nmos.lib. also added the input pulse, transient sweep parameters and vdd voltage. 

Now we need to generate LEF files to use in openlane.

## magic DRC
9. scb
10. dncjkd
