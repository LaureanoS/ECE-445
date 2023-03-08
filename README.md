# ECE-445

Galvanic Isolated Voltage Sensor

Laureano Salcines and Jevin Liu


//Update//


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

- Texas Instruments #TLV9154QDYYRQ1 : It has 4 channels in case any one breaks down (we will only use 2), $1.65, ask Jason about what specs are important in the OP-AMPs.
