# ECE-445

Galvanic Isolated Voltage Sensor

Laureano Salcines and Jevin Liu


//Update//


03/06/2023

Meeting with Jason to discus the next steps of the project. We have to choose our  components and we discussed a litle about the voltage divider.

Also discussed what components we should buy, started to talk about the voltage divider, is it best to do it with one component already made or to buy two resistors and make it ourselves in the PCB board? (we need 100:1 voltage ratio and 10Mohms input impedance).
After looking at some components we couldn't find any available voltage divider that meet our criteria because the most aqqurate one could be the Vishay #CDMA15M0D2500DE5 that has 15Mohms input impedance but it has a voltage ratio of 250:1 which means we will have to amplify the voltage output, having to add more components and potencially adding error.

03/07/2023
Meeting with Hanyin to discus the design document and the design review. We have to update the design document because we are still missing the schematic and a calendar with the deadlines that we want to meet.

03/08/2023

After the idea of having the voltage divider allready made was ruled out we started to look for resistors that meet our criteria and we found:
-	Vishay/Beyschlag  #MCU0805MD1504BP500: 1.5 Mohms, 0.1%, 25 PPM / C, L=2mm, 0.6$

-	Vishay #CRMA1206AF15M0DKEF: 15Mohms, 0.5%, 100 PPM / C, L=3.18mm, 0.68$
