# MEC1003F 2024 Assignment 2

Starting repository for MEC1003F 2024 Assignment 2.

## Overview

For this assignment you will demonstrate your ability to make a basic footprint, link it with a schematic symbol, and populate a PCB with a complete circuit.

Bonus marks are also available for laying out and routing the PCB.

In the last lecture we started with a template project which provided a set of schematic symbols and some footprints, but not all. Additionally, that entire circuit was powered from `+BATT`. However, in this assignment we will make a small change by adding a voltage regulator to the circuit, and using that regulated voltage to change the output amplitude of the second comparator's output.

## Initial Instructions

1. Clone or download this repository to your local machine. If downloading manually, remember to extract the contents of the zip file!
2. Open the schematic in KiCad. You should notice the following changes:
	- The last power flag has been changed from `+BATT` to `+3V3`.
	- A voltage regulator has been added to the circuit (creating `+3V3`).
	- The voltage regulator pins numbers have not been specified.
3. Open the Symbol Editor and you should find the `Project Symbols` library. This library contains all the symbols for this project.
4. Open the Footprint Editor and you should find the `Project Footprints` library. This library contains all the footprints for this project.
5. Open the PCB Editor. You should find this blank.

With this you should have the general outline of the project you are working with.

## Tasks

### 1. Complete the Voltage Regulator Symbol (3 marks)

Open the linked datasheet for the LP2950. All the information you require to complete the component model is in there.

Do the following:

1. Open the symbol editor and find the `LP2950` symbol in the `Project Symbols` library.
2. Identify which specific footprint package the given symbol should be linked to (TO-92/TO-252/DIP/SOIC/VSSOOP/WSON).
3. Given the identified package, edit the symbol to number the pins accordingly.
4. Save the symbol.

### 2. Create the Voltage Regulator Footprint (10 marks)

Given the package identified in the previous task, create a new footprint for the voltage regulator:

1. Open the footprint editor and open the `Project Footprints` library.
2. You can create the footprint in whatever way you like, but as a reminder, you can typically go one of two routes:
   1. Search for an existing component within the KiCad standard libraries, or elsewhere, that generally matches the package type and modify it to match the exact dimensions of the LP2950 datasheet; or,
   2. Create a new footprint from scratch.
3. In addition to the pads (which are critical), also add a silkscreen outline and a reference designator.
4. Also, ensure you place an appropriate courtyard and component outline on the relevant layers.
5. Save the footprint.
6. Go back to the symbol editor and link the `LP2950` symbol to the newly created footprint.
7. Save the symbol.
8. Update the schematic symbol to use the new symbol footprint.
    > If you have any issues updating the symbol, simply place a new symbol and delete the old one.
9. Save the schematic.

With this you should have a complete circuit with all the necessary footprints.

### 3. Populate the PCB (2 marks)

1. Open the PCB editor.
2. Update the PCB from the schematic and place all components. This should produce a PCB with all the components placed.
3. Check your footprints! Now that everything is placed, ensure that all the footprints look correct. If you made any error in dimensions or forgot to add some features, hopefully you notice it here.
4. Save the PCB.

### 4. Bonus: Layout and Route the PCB (2 marks)

Getting the footprints to the PCB is all we expect for now. However, if you want to go further, you can try to layout and route the PCB. This is not required, but if you do, you will receive bonus marks.

1 mark will be awarded to a layout that is reasonably well done, with an appropriate board outline and ground pour. 1 mark will be awarded for complete traces and reasonable us of vias.

## Support

Remember that you can ask for help at any time. Post your questions on MS Teams Under the `Assignments` channel or otherwise contact the lecturer for some hints. This is an important assignment and we want you to do well and get comfortable doing this!