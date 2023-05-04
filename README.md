# ECE-445

Galvanic Isolated Voltage Sensor

Laureano Salcines and Jevin Liu

02/02/2023
We met with Jason so he could talk us about the isolated voltage sensor pitched project. We discused the main features of the project and high-level requirements, Jason gave an overview of the working of octocouplers. 


02/04/2023

Completed our RFA on the course website

02/06/2023

We preperaed for the first meeting with TAs an we needed the the following data:

 First draft of Block Diagram, as the project was pitched the initial block diagram was done at a high level, but it still needed to be worked on.

 Your three High-Level Requirements, again as it was a pitch project this was already given in the specifications of the project.
 
 Proof of completion of the lab safety training (in-person students only), uploaded to Canvas. Completed safety course on Canvas.
 
02/07/2023
 5:40-6:00pm we had our first meeting with Hanyin and Jason all together. The things prepared on the 02/06/2023 were okay but the block diagram still had lots of faults, also we were missing some things that should have been done by the meeting date.

 - One subsystem requirement
 
 
 - A rough draft of the entire proposal.
 
 
 - We still were needing a group workbook so this repository was created.

02/07/2023

 Worked on the project proposal for our design


The problem to be solved was:

  In power electronics, there is a need to sense a voltage through galvanic isolation. In these applications, the output measurements must be accurate and be represented digitally.

And our solution:

Our solution is a small board that can be mounted onto another larger PCB, this small board will carry an analog front end, analog to digital converter, isolated digital interface, a microcontroller and a power supply.
measure a voltage across an isolated barrier, provide the measurement as a floating point number.

The components we pretended to use were:

- Analog front end

- Analog to digital converter with voltage reference.

- isolated digital interface

- microcontroller

Here we are missing a Power subsytem that will later be implemented with a DC-DC converter.

02/08/2023

meeting in ECEB 2070 to finish up the proposal.

2/9/2023
 Submision of the project proposal

2/13/2023

Firs weekly meeting with the Hanyin, we discussed how the initial procedure of our project was coming along, and after looking at the project proposal several things were pointed out:

 The block-diagram still had clear big mistakes.

 We didn't have a clear tolerance analysis.
 
 We didn't have clear subsystems requirements, only the high-level ones.
 
So that had to be worked on.
 
 

03/06/2023

Meeting with Jason to discus the next steps of the project. We have to choose our  components and we discussed a litle about the voltage divider.

Also discussed what components we should buy, started to talk about the voltage divider, is it best to do it with one component already made or to buy two resistors and make it ourselves in the PCB board? (we need 100:1 voltage ratio and 10Mohms input impedance).
After looking at some components we couldn't find any available voltage divider that meet our criteria because the most aqqurate one could be the Vishay #CDMA15M0D2500DE5 that has 15Mohms input impedance but it has a voltage ratio of 250:1 which means we will have to amplify the voltage output, having to add more components and potencially adding error.

03/07/2023

Meeting with Hanyin to discus the design document and the design review. We have to update the design document because we are still missing the schematic, a calendar and a cost analisys.

03/08/2023

After the idea of having the voltage divider allready made was ruled out we started to look for resistors that meet our criteria and we found:
-	Vishay/Beyschlag  #MCU0805MD1504BP500: 1.5 Mohms, 0.1%, 25 PPM / C, L=2mm, 0.6$

-	Vishay #CRMA1206AF15M0DKEF: 15Mohms, 0.5%, 100 PPM / C, L=3.18mm, 0.68$

Once we have choosen the voltage divider we need to buy two OP-AMPs and three resistances R0, R1 and R3. The first OP-AMP one will be  a unity gain buffer that is used to reduce the load currents hugely because it has a huge input impedance. The second one will have to regulate the voltage from +-1Volt to 0-5Volts by using the right Vref and resistors R1 and R2.

Both OP-AMPs can be implemented in one component, we will choose the:

- Texas Instruments #LM358B : It has 4 channels in case any one breaks down (we will only use 2), $1.65, ASK JASON WHAT SPECS ARE IMPORTANT FOR THE OP-AMPS.

After choosing the OP-AMPs we also need the three resistors R0, R1 and R2 (ASK JASON WHY DO WE NEED R0) 

After calculating what Vref and R2/R1 ratio we will need to convert the +-1Volt to 0-5Volts we know that Vref=-5/3V and R2/R1=3/2, so now we can choose two resistances that meet these ratio. (ASK JASON ABOUT THE SIZE OF THE RESISTANCE I THINK BIG TO REDUCE CURRENT LOADS). After asking we knwow that the resistance have to be big but not as much as the voltage divider ones.


03/08/2023

Meeting with Hanyin and Jason to discuss the Ki-Kad and choosing the parts for later shipment.

03/09/2023

Meeting with professor Arne to discuss how the project was getting along.


03/20/2023

Choosing the A-D converter and we have chosen:

Starting to make the schematic of the project in KI-Kad, there were some problems for example the A to D converter thta we needed wasn't in Ki-Kad so it had to be exported from ultralibrarian.

After implementing everything it has been added to the design document for later submision

03/24/2023

Adding lots of things that were discussed with Professor Arne to the design document:

 - The tolerance analysis had to be changed
 
 - A schedule has been added to direct us on what to do in eac week
 
 - The cost analysis has been implemented
 
 - More references are being added

Remaking the OP-AMPs schematic for something that makes more sence and its easier to work with, once we have calculated the resistance and Vref needed after doing some calculous it comes out that we need two resistances with a 2.5 ratio between them and an Vref of 5/7 volts. The resistances we have chosen are 10 and 25 Kohms and this are their values:

 -	YAGEO  #RT0603DRE07152KL: 152 Kohms, 0.5%, 50 PPM / C, L=1.6mm, 0.11$

 -	Vishay #CRMA1206AF15M0DKEF: 15Mohms, 0.5%, 100 PPM / C, L=3.18mm, 0.68$
 
 
We can get Vref by putting the Vref of the ADC through a voltage divider. 

03/27/2023

Another meeting with Jason and Hanyin to discuss the parts, we are going to work with a DC to DC isolated converter which will isolate the voltage supply for all the components and will power a reference IC which will power the Analog to Digital Converter and will give Vref to the OP-AMPs. We use this reference IC because is far more precise than directly getting the voltage from the DC-DC converter.

Adjusting the resistances of the voltage divider so the Vout will be more aqqurate, we had 15Mohms and 150Kohms which turned he +-100V to +-0.9901V we changed the R2 to 152Kohms so the new output is +-1.003V wich is more aqurate, the prefect resistance value would be 151.5Kohms but there isn't a resistance of that precise value.

The new resistances for the voltage divider are now:

 -	YAGEO  #RP0402BRE0710KL : 10 Kohms, 0.1%, 50 PPM / C, L=1mm, 0.38$

 -	TE Connectivity / Holsworthy  #CPF-A-0805B25KE: 25Kohms, 0.1%, 25 PPM / C, L=2mm, 0.58$



Working with the schematic in Ki-Kad and choosing new components for the circuit:

We have chosen the galvanic isolation for which we have chosen a digital isolator:
 
 -	Texas instruments  #ISO7320C: Voltage input: 3V ~ 5.5V , Voltage output: +-15V , 3.46$

We have also chosen the DC-DC converter:

 -	Texas instruments  #NMA0512DC: Voltage input: 5V , Voltage output: +-15V , 5.08$

 
 For this component after studying the datasheet we know it works better with some capacitors to get rid of small ripples that might appear int the input and output, so we selected three capacitors with that end:
 
 2 2.2 uF Capacitors:
  - TAIYO YUDEN  #MSRLJ103SB5225MFNA01 : 1.2 µF, ±20%,  1mm x 0.5mm, 0.32*2$

 2 220 uH Inductance:
  - TAIYO YUDEN  #LSXNH8080YKL221MJG  : 220 µH, ±20%,  8mm x 8mm, 0.46*2$
 

After this the reference IC:

 - Analog Devices  #ADR4550BRZ-R7: Voltage Input:5.1V ~ 15V , Voltage output: 5V , 10.8$
 
For this component after studying the datasheet we know it works better with some capacitors to get rid of small ripples that might appear int the input and output, so we selected three capacitors with that end:
 
 2 1 uF Capacitors:
  - TAIYO YUDEN  #TMR107B7105KA-T: 1 µF, ±10%,  1.60mm x 0.80mm, 0.17*2$

 1 0.1 uF Capacitors:
  - TAIYO YUDEN  #MSAST1L3YB5104MFNA01: 0.1 µF, ±20%, 1.00mm x 0.50mm, 0.21$
 

In order to get the Vref that we need for the OP-AMPs we need a high precision voltage divider that gets us the 5/7 volts we desire, for that we are going to need another two resistance this time with a ratio of 6, and we have chosen:

 -	Panasonic #ERA-8ARW202V   : 2 Kohms, 0.05%, 10 PPM / C, L=3.2mm, 1.57$

 -	Panasonic #ERA-3VRW1202V    : 12 Kohms, 0.05%, 10 PPM / C, L=1.6mm, 0.74$

03/27/2023

 -PCB review with Jason
 
 After looking at the diagram had to add a couple more capacitors on the power to the ADC and changed the DC-DC converter for one wit a +-12 Volts output so the voltage wasn't that close to the limits of the OP-Amps and reference IC.
 
 -So added 2 more 1 uF Capacitors and the new DC-DC converter is:
 
   -	Texas instruments  #NMA0512DC: Voltage input: 5V , Voltage output: +-15V , 5.08$
  
  For which we had to change its capacitance and inductance to:
  
  2 0.33 uF Capacitors:
  - TAIYO YUDEN   #TMK107BJ334KA-T : 0.33 µF, ±10%,  1.6mm x 0.8mm, 0.11*2$

 2 150 uH Inductance:
  - TAIYO YUDEN  #LSXNH8080YKL221MJG  : 150 µH, ±20%,  8mm x 8mm, 0.46*2$

Also we discussed protecting our ADC in case the circuit is not working as we want, and we are going to use two schottky diodes which are better than normal diodes on the output of the OP-AMPs:
 The diode that we are going to use:
 
 - ROHM Semiconductor  #RB078RSM10STFTL1   : 150 µH, ±20%,  6.35mm x 4.45mm, 1.55*2$

